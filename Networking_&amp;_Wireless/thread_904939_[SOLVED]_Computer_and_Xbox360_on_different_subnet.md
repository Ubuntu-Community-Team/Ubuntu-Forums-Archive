---
title: "[SOLVED] Computer and Xbox360 on different subnet"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by suzypeppercorn on 2008-08-29
Here is my setup right now. I am in my college dorm and my computer is connected to the network via wireless. My xbox360 is connected to the network with a cable.

My computer's addresses:
ip address: xxx.xxx.213.99
subnet mask: xxx.xxx.240.0

My xbox's addresses:
ip address: xxx.xxx.250.85
subnet mask: xxx.xxx.254.0

I am trying to stream video from my computer to my xbox360 using ushare. Right now my xbox doesn't even see my computer. Is the problem with the different subnet masks?

I've tried pinging my xbox with the command ping xxx.xxx.250.85. It failed.

Anyone have any ideas? How can i stream my videos to my xbox?

---

### Post by suzypeppercorn on 2008-09-02
Anyone have any ideas? Should it matter that the subnets are different even though they are on the same network?

---

### Post by MJRehrig on 2008-09-02
As far as I know, you will not be able to communicate with your XBox if it has a different subnet mask. I really doubt there is anything that you can do about this, save getting a router or hub to connect the two together.

---

### Post by suzypeppercorn on 2008-09-02
ya i think i am going to have to go that route. i just wanted to see if anyone had any other info about it.

thanks

---

### Post by mellowd on 2008-09-02
If they have different masks it means they essentially on different networks. Unless they know how to get to each other they wont.

---

