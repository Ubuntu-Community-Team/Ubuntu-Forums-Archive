---
title: "tcp socket data loss ?"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by afopv3123l on 2008-02-18
Hi all,
    I have been using a server and multiple clients which communicate using tcp socket.The server creates a separate thread for each client and receives the data.But the thing is that the data which is successfully sent at the client side is not received at the server.I have been using the socket send() and recv() system calls .I have even tried the TCP_NODELAY to disable nagle's algorithm and increased the read and write buffer sizes of the socket but they showed no improvement.Ant suggestions could bo of greathelp to me.
Thanks and regards,
Nanlu.

---

