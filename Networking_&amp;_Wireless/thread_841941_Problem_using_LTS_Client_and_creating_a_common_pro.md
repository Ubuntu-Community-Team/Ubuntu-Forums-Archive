---
title: "Problem using LTS Client and creating a common profile for all clients"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Avinash.Rao on 2008-06-26
Dear all,

I thought it was appropriate to post this here.


1) I have installed Ubuntu 8.0 with LTS on AMD 64-bit dual core machine with 2GB RAM. Is a brand new machine and this hardware is recommended in LTSP documentation to support 64 users.

The client is P4 machine and has 512MB RAM locally. The client boots through the network without any problems, but after logging in, working through different windows is a bit slow. Sometimes it behaves as if there is lack of RAM. 

The network is a 100Mbps LAN. The network runs fine under windows without any problems. 
Is it something to do with the display adpater? Should i configure LTSP client to use a particular adapter? The display adapter on the server is Nvdia 3D graphics enabled adapter. 

2) Also, how can i use a common desktop profile for all the users? I used the 'user profile editor" on the server made a few changes and added the users. But didn't work. Infact when i opened the user profile editor again, the changes made previously disappeared.

Please help
Avinash

---

### Post by Tallwood on 2009-03-24
Did you ever resolve this problem?

First thing to check would be the profile editor. Did you apply the profile to any users?

---

### Post by Avinash.Rao on 2009-03-30
Sorry for the late reply.
Yes i applied this to few users, updated the ltsp image but they didnt work.

---

### Post by Tallwood on 2009-09-15
What changes did you try to enforce specifically?

---

