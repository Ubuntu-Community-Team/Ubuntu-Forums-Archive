---
title: "[SOLVED] Remote Connections"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2008-02-24
I'd like to be able to connect to my computer from any computer in the world. For example from work to my home computer. Here's how I want it:
1. desktop interface from my account,
2. that my connection doesn't bother any user that is already working on that computer logged on as another user (that we can work independently of each other) ,
3. since I don't have static IP, my ISP provides me another IP every now and then, so it would be inpractical if I had to know my ip adress every time I want to connect. I don't know what do I need for that, a domain or what? And how do I do that? This is probably the most important question.

So the question is.... how do I do all that?

---

### Post by newlinux on 2008-02-24
i would go with nxserver or freenx [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) for 1 and 2. FreeNX can be accessed with NoMachine's NX client from multiple platforms. For 3 you need a dynamic dns service like no-ip.com.

---

### Post by ene_dene on 2008-02-24
Thanks.

---

### Post by ene_dene on 2008-02-24
One more thing, is it possible to connect to remote computer as user that is already logged in? So that there is no need to create another account for remote users.

---

### Post by newlinux on 2008-02-24
Yes it is. A user can be logged into the same machine more than once.

---

