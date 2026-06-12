---
title: "Are &quot;SSH&quot; &quot;PDU's&quot; created at the TCP/IP Model's Application Layer"
date: 2020-06-30
forum: Networking &amp; Wireless
---

### Post by fran_3 on 2020-06-30
Question 1: Before the  SSH "handshake" between the Client and the Server... where in the process does SSH Protocol do it's thing...

Question 2: I'm assuming it Encodes/Scrambles the original data based on some algorithm... which has been agreed to by the two computers... Client & Server... right?

Question 3: So does this occur at the Application Layer before the segmented data gets it's TCP header added at the Transport Layer?

This is based on the assumption that...

Question 4: SSH traffic travels over the internet as "Frames" ... with a header and trailer... via the following steps... Right?

1 - It all starts out with the raw data at the Application Layer that Computer-1 wants to send to Computer-2... Maybe something as an ASCII text like... "Hello World"

2 - ??


3 - At the Transport Layer the the data got segmented with a Header added and thus became TCP Packets with Source & Destination Ports included

4 - At the Network Layer those TCP Packets had an additional Header added and thus became IP Packets with Source & Destination IP addresses included

5 - At the TCP/IP Updated Model's Data Link layer the IP packets had another Header added plus a "Trailer" with the Source & Destination Mac Address induced

I've Googled & watched Videos until my eyes have rolled back in my head... so I'm hopeful that some kind soul will walk through this with me.

Thanks.

---

### Post by wildmanne39 on 2020-06-30
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Thanks

---

### Post by fran_3 on 2020-06-30
Wildmanne39 - I attempted to enlarge the font because of a vision problem.

---

### Post by wildmanne39 on 2020-06-30
> **fran6 said:**
> Wildmanne39 - I attempted to enlarge the font because of a vision problem.
I understand, I have the same issue, please do like the rest of us do and just in large your fonts in your browser please.

Thanks

---

### Post by The Cog on 2020-07-01
I'll have a go...

Q1: The SSH "protocol" is a specification of how two SSH processes (client and server) should exchange information, both the format of the handshake messages and the payload data. This is all very much application layer stuff. Strictly speaking, what you see on the wire is data that confirms to that protocol.

Q2: Correct.

Q3: The ssh "protocol" (behaviour) persists for the duration of the connection. This involves creating and using a TCP connection to carry those messages. Chronologically, the ssh processes must exist before an ssh connection is established, but that ssh "session" is above the transport layer, and remains at least until the TCP connection closes again. It is before, during and after.

Q4: Frames is  a link layer term. Strictly speaking, SSH only knows it's using TCP transport. The TCP layer makes use of IP network protocol to carry its stream of data. The IP layer may well use link layer (e.g. Ethernet) to send its packets if the other IP address is not on the same host. 

You have the rest pretty-much right. Each layer uses the layer below as a service, and does not know anything about the layers below that.

---

### Post by fran_3 on 2020-07-01
This is very helpful Cog.  So to be clear on actual transmission and reception... 

Ultimately, when you finally get down to where the "stuff" is actually spit out by the computer to the Network Interface/Ethernet card...

it is sent (and received) just like anything else... in "chunks" ... and these "chunks" are called "frames" each with a header and trailer.

([I]I've have previously always referred to these "chunks" of data as Packets... as some background years ago with "Packet Switching Networks"  
but now have been educated that you start with data which gets seperated into... segments, then packets, and then frames... 
if I have it right[/I]:-)

I'm making sure I've got this clear for a reason so thanks for sticking with me :-)

---

### Post by The Cog on 2020-07-01
Yes, the chunks get different names at different layers.

ssh will use read() and write() calls to the TCP stack. I don't think there is a name for the different "chunks" at this stage.

TCP gives TCP segments to IP for delivery over the network.

IP sends IP packets to interfaces, which are the ends of links.

Links carry frames to the next IP host where the frame is removed and the IP packet either used internally or forwarded over a link to another host, depending on the destination IP address. In its journey from A to B, and IP packet may traverse many links, being wrapped and unwrapped in many frame headers.

P.S. As you are interested in this, I suggest that you install wireshark on your PC and capture some of your network traffic - an ssh session, visiting a web page etc. Reading wireshark's breakdown can be very educational. It clearly shows the different layering. You will learn a lot, and it also helps cement what you have already read.

---

