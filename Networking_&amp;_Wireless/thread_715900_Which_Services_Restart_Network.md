---
title: "Which Services Restart Network?"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-03-05
My question is as follows: if my ethernet connects into my T61p through a USB port replicator and the cable becomes disconnected, what services can I restart to re-establish network connectivity without having to reboot? 

The particulars are as follows:

1) My network comes connects to my T61p via a USB Port Replicator. Mistakenly, the USB cable to the T61p became disconnected. 

2) I reconnected the cable, and network manager re-established a dhcp address. I did not look at the output of ifconfig.

3) I tried to ping a known host and get no route to host. 

4) Rebooting fixed the problem.

Before rebooting, I tried restarting networking and openbsd-inetd. Doing this had no effect. I still had to reboot.

I don't go around every day unplugging my USB cable, and I can always reboot, but with Linux rebooting is often not necessary, so that's why I am trying to find out the services to restart.

tnx
cmn

---

### Post by user-unit on 2008-03-05
I'm also interested in finding out since i have more things that use the network then plug ins, which means a restart every time i switch things around.

---

