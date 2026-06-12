---
title: "Connecting a private ubuntu network to the internet"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by DrCoolSanta on 2008-03-29
I have a private network of some computers, with the fastest computer as a server for various applications. Since these computers are on a private network they are allowed to communicate with each other (rsh, ssh, nfs, etc.), and passwords for the machines are kept easy so that everybody in our lab, can remember them. I would like to have them be able to connect to the internet. If I use the internet our institiution uses, then our machines could be at a risk of being accessed by people of other labs.

In the institution, we get an internet connection that follows the 10.x.x.x series to make the IP addresses, but our private network uses 192.168.0.x. I thought I would firewall the server to not allow any access to the computers outside the network, and have it act as a gateway to all the other machines. Another thing, if it could matter, the internet is behind a proxy server in the institution.

I know it is a bit hard to understand, but should make atleast some sense.

---

### Post by SpaceTeddy on 2008-03-29
it sounds like you want to do **internet sharing** (having one machine that hides a network of computers behind it)...

i have written down a few steps on how to set this up with ubuntu. you can find the post [here]("http://ubuntuforums.org/showthread.php?t=713874").

also, as sonn as your gateway has connection to the internet, it should not matter to the rest of the computers... i think (nit much experience with proxy)

---

### Post by DrCoolSanta on 2008-03-29
Thanks a lot, thats what I wanted :)

This basically means I have to get another lan card installed, which is a tedious job, since all net cards I have, do come with linux drivers but need thousands of dependencencies, and without internet it's difficult, I cant even temporarily remove it from the network, manuel packages then -_-

---

### Post by SpaceTeddy on 2008-03-29
if you already have one working lan card, you can use that to configure the second one... besides, almost all cards i had so far worked right out of the box with ubuntu and a fairly new kernel... 
but i am no real help there... i am better at the routing/firewalling stuff :)

---

### Post by DrCoolSanta on 2008-03-29
> **SpaceTeddy said:**
> if you already have one working lan card, you can use that to configure the second one... besides, almost all cards i had so far worked right out of the box with ubuntu and a fairly new kernel... 
but i am no real help there... i am better at the routing/firewalling stuff :)
Well mostly they do get detected, but I had tried connecting the same card to another PC to add it to this private network. Unfortunately it didn't work, and I need to fix the dependencies to compile the driver that came with it.

---

