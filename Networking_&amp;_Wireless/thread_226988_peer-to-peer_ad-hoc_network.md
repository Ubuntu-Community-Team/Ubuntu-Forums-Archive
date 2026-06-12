---
title: "peer-to-peer ad-hoc network"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by civetta on 2006-08-01
Hello everybody

I'm trying to set up an ad-hoc network between two laptops. One runs Dapper, the other is a Mac. I'm having trouble creating an ad-hoc network using the linux laptop. I changed my settings so that I have a static IP address (192.168.0.1), subnet mask (255.255.255.0) and use the following command to create an ad-hoc network:

sudo iwconfig eth1 essid mynetwork mode Ad-Hoc

iwconfig shows that everything has been set up properly except there is no signal strength and the Mac laptop can't find "mynetwork". BTW I have Intel Proset Wireless 2200b/g and I have no trouble picking up wireless signals otherwise.

I'm pretty new to this stuff but I've done quite a bit of forum searching. Can anyone give me a hint as to whether I'm up to the right stuff?

---

### Post by civetta on 2006-08-05
OK, here are some steps I'm taking to try to solve this myself:

(I'm really new to this stuff so I may be making obvious errors)

I connected to an ad-hoc network I created on the apple laptop. Here's what I got using iwconfig:

eth1      IEEE 802.11g  ESSID:"mynetwork"  Nickname:"nathan"
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: 66:D9:21:F6:7E:A2
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-33 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0

I can ping the apple computer from my computer and the apple computer knows I'm accessing the network because it sends warning messages that my ubuntu laptop is on the network. Only when I use ssh, I can't log in from either side. (I know ssh works because I can use it to log on to each account on the individual computers, I just can't log on from a remote computer).

Now I'm confused. Is there anything else I need to do e.g. allow remote login for ubuntu (I've followed instructions for allowing remote ssh login from the apple)? And I still can't set up an ad-hoc wireless network FROM the ubuntu laptop that the apple can see. :confused: 

thanks for your help

---

