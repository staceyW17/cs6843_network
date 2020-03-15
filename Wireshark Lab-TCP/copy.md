

1. What is the IP address and TCP port number used by the client computer (source) that is transferring the file to gaia.cs.umass.edu? To answer this question, it’s probably easiest to select an HTTP message and explore the details of the TCP packet used to carry this HTTP message, using the “details of the selected packet header window” (refer to Figure 2 in the “Getting Started with Wireshark” Lab if you’re uncertain about the Wireshark windows. 

**ANS: ** The IP address 192.168.1.102    TCP port is 1161

![Screen Shot 2019-10-09 at 23.06.47](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.06.47.png)

2. What is the IP address of gaia.cs.umass.edu? On what port number is it sending and receiving TCP segments for this connection? 

   **ANS: ** 

   Sending IP address:192.168.1.102   TCP port: 1161

   Receiving IP address: 128.119.245.12  TCP port: 80

3. What is the IP address and TCP port number used by your client computer
   (source) to transfer the file to gaia.cs.umass.edu?

   **ANS**

   Client IP:172.31.130.217，TCP port :52836 

   Sever IP:128.119.245.12，TCP port: 80 

   ![Screen Shot 2019-10-09 at 23.07.13](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.07.13.png)

4. What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and gaia.cs.umass.edu? What is it in the segment that identifies the segment as a SYN segment? 

   **ANS: **  Client send SYN to start connection. I searched for the first sent request and find the client set SYN as 1 to establish the connection.

   SEQ = 515011625, which is a random number.  This is the first step of three-way handshake.

   ![Screen Shot 2019-10-09 at 23.11.32](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.11.32.png)

5. What is the sequence number of the SYNACK segment sent by gaia.cs.umass.edu to the client computer in reply to the SYN? What is the value of the Acknowledgement field in the SYNACK segment? How did gaia.cs.umass.edu determine that value? What is it in the segment that identifies the segment as a SYNACK segment? 

   **ANS: **

   ![Screen Shot 2019-10-09 at 23.11.58](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.11.58.png)

   According to the sequence number SEQ = client SEQ + 1 of SYN-ACK response value, the SEQ (sequence number) = 515011626 can be used to search.

   And Ack was set as 1, which means the sever has received the client’s connection request and sent SYN-ACK to confirm. 

   This the second step of three-way handshake.

6. What is the sequence number of the TCP segment containing the HTTP POST command? Note that in order to find the POST command, you’ll need to dig into the packet content field at the bottom of the Wireshark window, looking for a segment with a “POST” within its DATA field. 

   **ANS: **  The sequence number is 1237767729

   ![Screen Shot 2019-10-09 at 23.13.09](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.13.09.png)

7. Consider the TCP segment containing the HTTP POST as the first segment in the TCP connection. What are the sequence numbers of the first six segments in the TCP connection (including the segment containing the HTTP POST)? At what time was each segment sent? When was the ACK for each segment received? Given the difference between when each TCP segment was sent, and when its acknowledgement was received, what is the RTT value for each of the six segments? What is the EstimatedRTT value (see Section 3.5.3, page 242 in text) after the receipt of each ACK? Assume that the value of the EstimatedRTT is equal to the measured RTT for the first segment, and then is computed using the EstimatedRTT equation on page 242 for all subsequent segments. 

   *Note:* Wireshark has a nice feature that allows you to plot the RTT for each of the TCP segments sent. Select a TCP segment in the “listing of captured packets” window that is being sent from the client to the gaia.cs.umass.edu server. Then select: *Statistics->TCP Stream Graph- >Round Trip Time Graph.* 

   **ANS: **

   Segment1:

   ![Screen Shot 2019-10-09 at 23.14.15](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.14.15.png)

   ![Screen Shot 2019-10-09 at 23.14.53](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.14.53.png)

   Segment2:

   ![Screen Shot 2019-10-09 at 23.15.20](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.15.20.png)

   ![Screen Shot 2019-10-09 at 23.15.42](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.15.42.png)

   

   Segment3:

   ![Screen Shot 2019-10-09 at 23.16.55](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.16.55.png)

   ![Screen Shot 2019-10-09 at 23.17.14](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.17.14.png)

   Segment4:

   ![Screen Shot 2019-10-09 at 23.18.03](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.18.03.png)

   ![Screen Shot 2019-10-09 at 23.18.13](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.18.13.png)

   Segment5:

   ![Screen Shot 2019-10-09 at 23.18.43](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.18.43.png)

   ![Screen Shot 2019-10-09 at 23.18.49](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.18.49.png)

   Segment6:

   ![Screen Shot 2019-10-09 at 23.19.13](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.19.13.png)

   ![Screen Shot 2019-10-09 at 23.19.22](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.19.22.png)

   ![Screen Shot 2019-10-09 at 23.29.24](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.29.24.png)

8. What is the length of each of the first six TCP segments?

   **ANS** see above

9. What is the minimum amount of available buffer space advertised at the received 

   for the entire trace? Does the lack of receiver buffer space ever throttle the 

   sender? 

   **ANS**

   me as the sender, the window size is 227 ![Screen Shot 2019-10-09 at 23.30.57](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.30.57.png)

   No throttle is made due to the lack of buffer space.  (window size is not 0)

10. Are there any retransmitted segments in the trace file? What did you check for (in 

    the trace) in order to answer this question? 

    **ANS**

    Since the sequence is always going up, no retransmitted segments.

    ![Screen Shot 2019-10-09 at 23.34.47](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.34.47.png)

11. How much data does the receiver typically acknowledge in an ACK? Can you 

    identify cases where the receiver is ACKing every other received segment (see 

    Table 3.2 on page 250 in the text). 

    

12. What is the throughput (bytes transferred per unit time) for the TCP connection? 

    Explain how you calculated this value. 

    **ANS** 

    Throughput = (Amount of data transmitted / time incurred)

    153058 Bytes/1.16585800 s=131283.569697167 Byte/s=128.206611032 Kb/s

    ![Screen Shot 2019-10-09 at 23.38.07](/Users/wangjiahui/Desktop/Screen Shot 2019-10-09 at 23.38.07.png)

13. Use the *Time-Sequence-Graph(Stevens*) plotting tool to view the sequence number versus time plot of segments being sent from the client to the gaia.cs.umass.edu server. Can you identify where TCP’s slowstart phase begins and ends, and where congestion avoidance takes over? Comment on ways in which the measured data differs from the idealized behavior of TCP that we’ve studied in the text. 

14. Answer each of two questions above for the trace that you have gathered when you transferred a file from your computer to gaia.cs.umass.edu 