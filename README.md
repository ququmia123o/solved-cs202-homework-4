Download Link: https://assignmentchef.com/product/solved-cs202-homework-4
<br>
<h1>Question 1</h1>

<ul>

 <li></li>

</ul>

Figure 1: 2-3-4 tree

Draw an equivalent red-black tree of the 2-3-4 tree in Figure 1. Clearly indicate red and black nodes.

<ul>

 <li>[<em>5 points</em>] Draw only the final resulting 2-3-4 tree after inserting 48 into the original 2-3-4 tree in Figure 1.</li>

</ul>

<h1>Question 2</h1>

Fill in the below table appropriately by giving <em>expected </em>running times in big-O notation without providing any explanations for each operation. insert places a new item to the data structure and extractMin retrieves the item with minimum key and deletes it from the data structure. You may assume that hashing uses separate chaining.

<table width="604">

 <tbody>

  <tr>

   <td width="205">Data Structure</td>

   <td width="199">insert</td>

   <td width="199">extractMin</td>

  </tr>

  <tr>

   <td width="205">unsorted array</td>

   <td width="199"> </td>

   <td width="199"> </td>

  </tr>

  <tr>

   <td width="205">red-black tree</td>

   <td width="199"> </td>

   <td width="199"> </td>

  </tr>

  <tr>

   <td width="205">hashing</td>

   <td width="199"> </td>

   <td width="199"> </td>

  </tr>

  <tr>

   <td width="205">min-heap</td>

   <td width="199"> </td>

   <td width="199"> </td>

  </tr>

  <tr>

   <td width="205">sorted linked list</td>

   <td width="199"> </td>

   <td width="199"> </td>

  </tr>

 </tbody>

</table>

<h1>Question 3</h1>

<ul>

 <li>[<em>3 points</em>] What is the maximum number of keys that a 2-3 tree of height h can hold?</li>

 <li>[<em>2 points</em>] Is every subtree of a red-black tree also a red-black tree? Explain your answer with one sentence.</li>

 <li>[<em>5 points</em>] Assume that you have an array of length <em>N </em>that consists of unique integers. Describe an algorithm in plain English (no pseudo-code is needed) to find two integers in this array such that their sum is equal to a given target integer. Your algorithm must work in expected time <em>O(N)</em>. You can assume that exactly one pair of elements in the array sums to the given target integer.</li>

</ul>

<h1>Question 4</h1>

You are asked to develop a program that allows users to do some operations on the flight dataset given in the flightDataset.txt file. For this purpose, you will first construct a weighted, undirected graph from the dataset file and then develop some functionality for users to be able to analyze the dataset. Each line of the dataset file includes two airport names from the United Kingdom and the number of passengers transported between those airports in the year 2003. The format of each line is as follows:

airport1;airport2;numOfPassengers

You will use the given template in the graph.h, graph.cpp and main.cpp files to develop your program. In the graph structure you will implement, each vertex (node) will represent an airport and each edge will represent a reciprocal flight between airports. Each vertex will have an airport name and each edge will have the number of passengers transported between airports as value/weight. The adjacency list to represent this graph will actually be stored in a hash map as follows:

map&lt; string, list&lt;node&gt; &gt; adjList;

where string (key) keeps the airport name and list&lt;node&gt; (value) keeps the list

of vertices adjacent to the corresponding airport together with the edge value.

Graph class in the template includes seven functions (excluding constructor), whose details are given below, waiting to be implemented in order to form the adjacency list and manipulate it with the required operations.

<ul>

 <li><strong>void addAirport(const string&amp; airportName); </strong>(6 points) addAirport function gets the name of an airport (airportName) as a parameter and then adds this airport to the map, where airportName is the key and an empty node list (list&lt;node&gt;) is the value.</li>

</ul>

For example, when we add two new airports to an empty adjacency list:

addAirport(“HEATHROW”); addAirport(“ABERDEEN”);

<ul>

 <li><strong>void addConnection(const string&amp; airport1, const string&amp; airport2, int numOfPassengers); </strong>(6 points) addConnection function adds a new node to the list of airport1 using airport2 and numOfPassengers data, and adds a new node to the list of airport2 using airport1 and numOfPassengers data.</li>

</ul>

For example, when we add a new connection (edge) to the adjacency list above: addConnection(“HEATHROW”, “ABERDEEN”, 483226)

<ul>

 <li><strong>list&lt;string&gt; getAdjacentAirports(const string&amp; airportName); </strong>(6 points) getAdjacentAirports function gets name of an airport as a parameter and returns all adjacent airports of the given airport as a list of string.</li>

</ul>

For example, for the airport “NORWICH”, it should return “ABERDEEN”, “EDINBURGH”, “HUMBERSIDE”, “MANCHESTER”.

<ul>

 <li><strong>int getTotalPassengers(const string&amp; airportName); </strong>(6 points) getTotalPassengers function gets name of an airport as a parameter and returns the total number of passengers transported from/to the given airport. In other words, it returns the sum of the values of the incident edges of the given vertex.</li>

</ul>

For example, for the airport “KIRKWALL”, it should return 80264.

<ul>

 <li><strong>list&lt;string&gt; findShortestPath(const string&amp; airport1, const string&amp; airport2); </strong>(15 points) findShortestPath function gets two airport names as parameter, calculates the shortest path between the airports and returns the calculated path as a list of string. Assume that all distances among the airports are equal. If there are more than one shortest path between two airports, it is enough to return only one of them.</li>

</ul>

For example, for the airports “KIRKWALL” and “JERSEY”, the shortest paths are “KIRKWALL” →”EDINBURGH” →”JERSEY” and “KIRKWALL” →”GLASGOW”

→”JERSEY”. Your function should return one of these paths.

<ul>

 <li><strong>list&lt; pair&lt;string, string&gt; &gt; findMST(); </strong>(25 points)</li>

</ul>

findMST function simply calculates the minimum spanning tree(MST) of the flight network by using the edge values which are the number of passengers. This function returns a list of string pairs where each string pair represents an edge included in the MST by its incident vertices.

For example, some edges in the MST of the flight network are:

“DUNDEE”-“HUMBERSIDE”, “ABERDEEN”-“PLYMOUTH”, “MANCHESTER””LIVERPOOL” etc.

<ul>

 <li><strong>void deleteAirport(const string&amp; airportName); </strong>(6 points) deleteAirport function deletes the given airport from the graph together with its incident connections (edges).</li>

 <li><strong>cpp</strong></li>

</ul>

In main.cpp, construct an adjacency list by reading and processing the flight-

Dataset.txt file using addAirport and addConnection functions. Then, test the other functions with different inputs to make sure that they work correctly. Although you will write your own main function to test your functions, we will use our own main function to test whether or not your functions work.

Some important notes:

<ul>

 <li>The places that require implementation in the graph.cpp and main.cpp files are indicated with the comment /*YOUR IMPLEMENTATION*/. Please do your implementation in those places.</li>

 <li>map, list and queue data structures from the C++ standard template library (STL) are already included in graph.h. Use these data structures in your implementation directly. map and list are used by the adjacency list and as return types of many functions. You may use queue (and also priority_queue) in the implementation of findShortestPath and findMST functions, if necessary.</li>

 <li>Use the classes that are currently included; however, do not include any class (other than those specified) from the C++ standard library to graph.h and graph.cpp files.</li>

 <li>Additionaly you may include necessary classes from the C++ standard library to the main.cpp file for the purpose of reading and processing the dataset file.</li>

</ul>

Please indicate added classes in readme.txt.

<ul>

 <li>Please ask your TA, Hasan Balcı, if anything is unclear for you.</li>

</ul>

At the end, write a basic Makefile which compiles all your code and creates an executable file named hw4. Check out these tutorials for writing a simple make file: <a href="http://faculty.chas.uni.edu/~wallingf/teaching/cs4550/support/make/Makefiles.pdf">tutorial</a> <a href="http://faculty.chas.uni.edu/~wallingf/teaching/cs4550/support/make/Makefiles.pdf">1</a><a href="http://faculty.chas.uni.edu/~wallingf/teaching/cs4550/support/make/Makefiles.pdf">,</a> <a href="http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/">tutorial</a> <a href="http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/">2</a><a href="http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/">.</a> <u>Please make sure that your </u>Makefile <u>works properly, otherwise you may lose points from Question 4.</u>