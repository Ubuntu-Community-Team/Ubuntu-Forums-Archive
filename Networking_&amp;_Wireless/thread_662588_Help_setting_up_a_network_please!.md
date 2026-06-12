---
title: "Help setting up a network please!"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by DAE_JA_VOO on 2008-01-09
Hi there guys

I can't seem to get an Ubuntu PC networked properly. It's currently running off the live CD. It's actually a windows machine that i'll be installing ubuntu on, i just wanted to make sure i'd get it networked with the windows network it's connected to.

Here are the network settings for the windows machine:

I.P. Address: 192.168.16.14
Subnet: 255.255.255.0
Default Gateway: 192.168.16.1
DNS: 10.0.0.2

That's the only info i have. Now, i've managed to get this LIVE session of ubuntu HALF setup, but not enough. The only application that connects is Firefox. Here's how i did it:

I went to **System -> Admin -> Network** And i entered the network settings exactly the way they were in windows. After that, i entered the DNS address in the DNS tab.

After that, i went to **System -> Preferences -> Proxy** and entered 192.168.16.1 as the addy, and the port seemed to default to 0. Even with the port on 8080 i still get trouble. 

Once i had done this, nothing worked. I then opened up Firefox's proxy settings and entered 192.168.16.1 as the proxy and 8080 as the port, which worked perfectl, as i'm typing this from that very machine. 

The ONLY think that can access the net is Fx, everything else gives me errors.

Any suggestions? Thanks guys :)

---

### Post by ubutufan on 2008-01-09
[QUOTE=DAE_JA_VOO;4102025]Hi there guys


After that, i went to **System -> Preferences -> Proxy** and entered 192.168.16.1 as the addy, and the port seemed to default to 0. Even with the port on 8080 i still get trouble. 

Are you using a proxy?

---

### Post by DAE_JA_VOO on 2008-01-09
Well, i didn't THINK there was a proxy until i entered the gateway address into firefox's proxy settings, which allowed Fx to work, so now i ASSUME that there is a proxy.

---

### Post by ubutufan on 2008-01-09
May I suggest the following

I.P. Address: 192.168.16.14
Subnet: 255.255.255.0
Default Gateway: 192.168.16.1
DNS: 10.0.0.2
DNS: 192.168.16.1 (this is accessing your router directly)

Alternatively enter as DNS 208.67.222.222 (from opendns.com)

To make things work without rebooting, save the configuration in the Network Manager and then in the taskbar network icon, disable it first and then enable it again.
Let us know of the progress

---

### Post by DAE_JA_VOO on 2008-01-09
> **ubutufan said:**
> May I suggest the following

I.P. Address: 192.168.16.14
Subnet: 255.255.255.0
Default Gateway: 192.168.16.1
DNS: 10.0.0.2
DNS: 192.168.16.1 (this is accessing your router directly)

I did that and then disabled the proxy and now it all works PERFECTLY :D

Thanks SO much for the help!

---

### Post by ubutufan on 2008-01-09
You are welcome. Enjoy ubuntu

---

