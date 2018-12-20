# Visualisation of the Ethereum ecosystem: Interactions and relationships between subcommunities



The purpose of this graph analysis is to observe and understand the reciprocal influence of subcommunities inside the Ethereum ecosystem.


In this analysis I have used a open source command-line tool written in [Python](https://github.com/jdevoo/twecoll/blob/master/README.md) to retrieve data from Twitter and then an open-source [software ](https://gephi.org/users/) for visualizing and analysing large networks graph.

The data collected are public data (official twitter account) of most famous projects building on ethereum or helping the ecosystem "ethereum friendly" (eg: Ipfs, zcash fondation, polkadot, cosmos, Ocean protocol....)

I have selected and vested 122 projects in order to determine their reputation (what is a famous project?) according of standart criteria:

- Does it have a long term historical reputation ?
- Does it have a github accounts ?
- Does it have other social media exposure (twitter reddit facebook youtube and so on) ?
- How many people are signaling they support this project ?
- Is it backed by others official projects or influencers (devs, entrepreneurs, analysts) within the ecosystem ?
- What is the probability that it satisfy one of set of needs stated above (usuability, prosperity, value satisfaction) ?

You can find the entire list in the [src section](https://github.com/silver84/Ethereum-community-toolset/tree/master/src/raw_dat_and_gml_data).

For some odd reason [Twecoll](https://github.com/jdevoo/twecoll/blob/master/README.md) didn't managed to fletch and processed everything (data around a dozen of projects are missing in the graph).

I appologize in advance if not all famous the project are represented here, I encourage everyone to participate to this collaborative library and add missing data about credible Ethereum project.

# Why twitter?
Analysing a community via twitter will not give you an exact metrics on the nature of a community but in the attempt to gain a better understanding, the graph visualisation of the “who’s following who” in twitter allows us to highlight the structure of the network’s relationships and identify projects whose position is particular.
It also allow us to identify weak and strong signal such as:

- The diversity and density of the network, the degree of influence of a project, how the flow of information transmit itself from project to project.
- Identify potential affinity and interest between projects and eventually identify subcommunity within the network.


# Network graph analysis

The data used

- .dat: extension of account details data (numbers of tweets, following, followers, list)
- .gml: extension of edgelist file (nodes and edges)

Network graphs consist of edges (the connections) and nodes (the entities that are connected).

In this particular experimentation:
Nodes = a twitter account here an official ethereum projects accounts.
Edges = the number of interactions and relationships that nodes have with others nodes.

We using an undirected graph which mean the connections betwenn node have no obvious direction and are represented by simple lines or curves.

# Network algorithms and metrics

In this demonstration have been using the following algorithms:

- [Weight Degree](https://en.wikipedia.org/wiki/Centrality#Degree_centrality) which count and weight the connections for each node.
The graph will create a visualisation of the calculated weight of each nodes related to their degrees of interactions.
Eg: A node with 4 edges who weight 1 is equivalent to:
 - A node with 2 edges that weight 2 (followers=2 and tweets=2) or
 - A node with 2 edges that weight 1 (follower=1 and  tweets=1)  and 1 edges who weight 2 (list=2) or
 - A node with 1 hedge that weight 4 (follower=4) and so on.

 The more thicks the edges, the more weight is has.
 The more numbers of edges a node has the more relationship and interaction this nodes has within a group.

- [Betweenness centrality](https://en.wikipedia.org/wiki/Centrality#Betweenness_centrality) an ranking algorithm  introduced by [Linton Freeman](https://en.wikipedia.org/wiki/Linton_Freeman) as a measure for quantifying the control of a human on the communication between other humans in a social network.
In our analysis this ranking algorithm is great to emphasis the shortest path between nodes and to identify central hubes (clusters of nodes who attract the most connections or relationship within the network).
A node with high betweeness centrality scores has more influence over the network because lot of informations pass through this nodes.

- [Hubs and authorities](https://github.com/gephi/gephi/wiki/HITS) link analysis algorithm which estimates the value of the node itself and estimates the value of the links outgoing from the node.

- [Modularity](https://github.com/gephi/gephi/wiki/Modularity) an ranking algorithm  often called a community structure, describes how the the network is compartmentalized into sub-networks (or subcommunities).

- [Fruchterman-Reingold](https://github.com/gephi/gephi/wiki/Fruchterman-Reingold) a force-directed layout algorithm who simulates the graph as a system of mass particles.The nodes are the mass particles and the edges are springs between the particles. The algorithms try to minimize the energy
of this physical system. In our analysis this graph algorithm was used to emphasis the importance and the influence in terme of attraction and relationship each nodes has inside its network.


- [ForceAtlas2](https://github.com/gephi/gephi/wiki/Force-Atlas-2) a graph Layout Algorithm.
This graph algorithm use an innovative way to create repulsion/attraction force between nodes and hedges.
Nodes repulse each other like charged particles, while edges attract their nodes, like springs. These forces create a movement that converges to a balanced state. This final configuration is expected to help the interpretation of the data.
In our analysis this graph algorithm was used to emphasis network visualisation and therefore allow a better understanding of complementarities/dependancy between projects inside Ethereum ecosystem.

