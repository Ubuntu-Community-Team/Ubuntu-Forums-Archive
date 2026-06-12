---
title: "[SOLVED] networking"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by dmancini on 2008-12-04
Let me start by prefacing that I am a complete noob to ubuntu.  

I have installed 8.1 on my pc and have it set up to boot in either windows xp or ubuntu.  I have the pc set up on a home network.  

There is a d-link wda-1320 card on the pc and is connected wirelessly to a 2wire modem-router.  When I am signing onto the network I enter the key for the network and then nothing.  If there is anything more you need to know please let me know.  THankyou in advance for all of your help.

---

### Post by Kellemora on 2008-12-04
Hi DM

Clarify please!

Are you trying to access a LAN, the Internet or the Internet through a LAN?????

TTUL
Gary

---

### Post by dmancini on 2008-12-04
sorry about that.  A LAN and internet over wireless.

---

### Post by Kellemora on 2008-12-04
Hi DM

I've not used wireless, but I know there are many posts here regarding same in 8.10 that might be of help.

Some of the info you will need to post so those in the know about wireless can help you will be.
These are all Terminal commands that you can open and read.
When asked for them, you can copy and paste them to your messages here.

I don't know which ones you will be asked for, but this will give you an idea of what they look like, where they are, and be able to get to them quickly when asked.

You might even see the problem yourself upon viewing them?

sudo ifconfig -a
sudo route -n
lspci
lshw -C
cat /etc/network/interfaces
sudo dhclient eth0 or possibly sudo dhclient eth1
cat /etc/resolv.conf

I have to hit the horizontal side, long day tomorrow!
But some other guru's will be along shortly.

You also may want to mark this thread solved and make a new post with a different title, such as Can't connect to Internet through LAN on wireless, so the right guru will pick up on it faster.

Networking usually refers to LAN based problems!
Having Wireless Internet in the Title will bring help faster I think!

Good Luck my friend and welcome to Ubuntu!

TTUL
Gary

---

