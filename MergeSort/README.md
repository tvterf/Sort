# Activity 1
## Task 1
1. Structure of Code: The Node class implements runnable which opens a server socket that reads a request and sends the response using the NetworkUtils class. The Branch class and Sorter class extend the Node class. The MergeSort class tests the distributed algorithm by making requests to the "server"/branch and printing the response. The Branch class splits the array into two halves and sends those arrays to be sorted by the Sorter nodes in 2 different priority queues. 

2. The advantage is that the sorting of the array can be split into different nodes that can do the sorting at the same time, which will decrease the overall time it takes to sort the array in theory. The disadvantage is that if the array is not very large then it will probably take longer to sort the array with this setup, and it is definitely more complicated to have it setup this way which makes it more challenging to make sure everything is being done most efficiently.

3. With the original array it took 615ms to complete. With an array of size 100 with random unsorted numbers it took 899ms to complete. From these results it is clear to see that it took longer with a larger array which makes sense since there is more work to be done. The distribution is helpful here because it splits the work to be done amongst nodes so they can work in parallel.

4. I set this up to run with three nodes using two branches by adding another Branch task in the gradle file. I set the top Branch with args 7001, 7000, 9001. The lower Branch with args 7000, 8000, 8001. Three Sorters on ports 9001, 8000, 8001. Then finally the Starter on port 7001.
     mergeSort(7001)
            |
            B1(7001)
           /  \
    (7000)B2  S1(9001)
       /  \
(8000)S2   S3(8001)

With the tree structure above and the original size array, it took 385ms.
With an array of size 100, it took 1534ms. 
From these results it seems that the smaller array went slightly faster with this tree structure compared to the set up in #3, but the larger array took longer.
With only one Sorter node and the original array, it took 137ms.
With the larger array and one Sorter node, it took 379ms.
From these results it seems that distributed algorithm increases the completion time, while the non-distributed decreases the completion time. 

5. With the 3 node set up and a large array there is a lot of traffic on Wireshark. A simple way to reduce the amount of traffic would be to sort a small array and to only use a sorting node instead of a branch to distribute. 

## Task 2
1. I expect that the runtimes will increase since the traffic is now having to travel over the wire to the AWS server and then come back, which should not be as fast as everything happening on localhost. 

2.

## Task 3
1.
2.
3.
