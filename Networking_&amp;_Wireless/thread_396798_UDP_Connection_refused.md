---
title: "UDP Connection refused"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by kikazaru on 2007-03-29
I've been trying to establish a UDP connection, but every time I try, I get Connection Refused.

I established using tcpdump that requests are being received, but they don't seem to get as far as a piece of software I wrote which opens a socket as a server (tested and confirmed on Debian), nor nc.

I checked that firestarter isn't blocking the connections, so somehow they are being dropped internally before they reach the application. Any ideas what might be causing this, or how to debug/track it down?

Thanks!

---

### Post by Mr. C. on 2007-03-29
If you get connection refused, the UDP datagrams can't possibly reach their destination.

You say you've opened the socket.  Is the open a success, and do you see the open connection on the other end?

Once the socket is open, you should not get connection refused errors.

MrC

---

### Post by kikazaru on 2007-04-02
Thanks for your help! 

You were right, in that I wasn't opening the socket correctly, or so it seems. I rewrote the code for opening the socket and it started working. The socket and bind calls didn't give me errors, but I couldn't see the socket in the output of "netstat --inet -a | grep udp" so I changed the code.

---

