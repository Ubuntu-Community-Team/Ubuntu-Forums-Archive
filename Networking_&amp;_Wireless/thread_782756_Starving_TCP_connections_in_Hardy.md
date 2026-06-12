---
title: "Starving TCP connections in Hardy"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by vitek.cvachoucek on 2008-05-05
I need to work remotely with our development server (Trac, SVN)  on a range of ports and protocols (HTTP(S), VNC, SSH). The server is hidden behind possibly pretty absolete routers that are out of my control. 

From Hardy: For any of the protocols the clients are able to establish a TCP connection to the server but no data are ever transferred and the connection just stalls and timeouts or gets reset by the other side. The behavior can be observed both in Firefox and SSH. 

From Windows: Everything works blazingly fast.

From Gutsy: Everything forks out of the box albeit incredibly slow and unreliable. Following tweaks to sysctl.conf make a huge difference:

# increase TCP maximum buffer size
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216

# increase Linux autotuning TCP buffer limits
# min, default, and maximum number of bytes to use
net.ipv4.tcp_rmem = 4096 87380 16777216 
net.ipv4.tcp_wmem = 4096 65536 16777216

# idea found at [http://kerneltrap.org/nodallowe/1752](http://kerneltrap.org/nodallowe/1752)
net.ipv4.tcp_moderate_rcvbuf=0
net.ipv4.tcp_window_scaling=0

The same set of sysctl.conf changes makes no difference for Hardy. I have tried everything I run on the internet but still unable to work with the server via any means as anything on top of TCP just opens a connection and then stalls. Unless I am able to resolve the issue I will have to downgrade.

Thanks for any suggestion.
Vitek Cvachoucek

---

### Post by vitek.cvachoucek on 2008-05-06
Ok so I have debugged the comunication sequence at a packet level using the wonderfull Wireshark tool. Soon it became apparent that the pattern at TCP segment level for HTTP request is like this:

[HTML]
me      SYN        seq=0
server  SYN,ACK    seq=0 ack=1
me      ACK        seq=1 ack=1
me      ACK,PSH    seq=1 ack=1
 .... this carries the HTTP request string
server  ACK        seq=1 ack=1
.... this says server did not understand my segments starting with the seq=1
me     ACK,PSH     seq=1 ack=1 
.... retransmission of the HTTP request
server ACK         seq=1 ack=1
.... server did not understand
.... long sequence of retransmissions and refusals
[/HTML]

I have tried the very same from Windows nearby and compared the third packet in sequence one by one looking for differences. The difference was in the size of TCP header, windows having 20 bytes while linux using 32 bytes. The reason for the size difference was the "TCP Options" field in linux holding "TCP timestamps". Thus I have disabled the TCP timestamping in sysctl.conf:

net.ipv4.tcp_timestamps=0

Then "sudo sysctl -p" command to reload the configuration and it started to work! My big thanks to the Wireshark developers.

---

### Post by jimv on 2008-05-06
Your network prowess is impressive.

---

