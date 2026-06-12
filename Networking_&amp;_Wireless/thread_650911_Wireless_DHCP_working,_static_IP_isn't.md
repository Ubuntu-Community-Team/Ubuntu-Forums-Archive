---
title: "Wireless DHCP working, static IP isn't"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by SINZAR on 2007-12-26
I've been using Ubuntu on my laptop for awhile now and haven't had any problems. Yesterday I set up Ubuntu on an old desktop computer and today I bought a wireless card for it and everything is working fine for the most part.

I can connect to my network with no problems when I find the network name in the list and connect. However when I try to connect using manual configuration it doesn't work. I know the settings I'm entering are correct because I use the same ones on my laptop and theres no problem. I'm assuming its my wireless card for some reason but I'm still not adept at troubleshooting network errors with linux.

Strangely, If I enter manual configuration and set the option there as dhcp it doesn't work either. The network only works when roaming is enabled and I connect threw the network list.

I'm using gutsy and the wireless card is a tp-link, model tl-wn551g using the atheros chipset.

Any kind of help would be appreciated.

---

### Post by Dark Hornet on 2007-12-27
Just wondering...your router is set for DHCP..right?  If so, try changing it to static, then configure your pc.....just a thought.

---

### Post by SINZAR on 2007-12-27
Gave it a try, still nothing.

Here's some more information.

Ping results with manually configured IP

ben@ben-ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.111 icmp_seq=2 Destination Host Unreachable
From 192.168.1.111 icmp_seq=3 Destination Host Unreachable

Ping results with manually configured network/key, dhcp settings

ben@ben-ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.6.46 icmp_seq=2 Destination Host Unreachable

Not even getting an ip on the network.

---

### Post by Dark Hornet on 2007-12-27
ok...a few things to try (forgive me if some of these seem obvious--please don't get insulted).

1.  Try and see if a wired connection will work and, make sure your CAT5 cable is a crossover, and not straight through--and working.

2.  When your router is set to DHCP, can your router "see" your computer--you will be looking for a MAC address.  **NOTE**--some NIC's send out their MAC address in reverse, and some routers have an issue "reconstructing" it...just something to think about.

3.  Check your NIC--make sure you are able to ping yourself...this is most likely going to be a 127.0.0.1 address.

---

### Post by boboyo on 2007-12-27
same thing for me. but i use a wireless router and i cant connect, i have to plug my internet cable in my laptop and then, i can connect. i dont know what to do..... on the vista part of mt laptop, everything works fine.


and btw waht is a ping?

---

### Post by Dark Hornet on 2007-12-27
A "Ping" is a way of determining if you have what is called "layer 3" or "IP" connection.  For example, If I typed "ping 192.168.1.1" in my terminal, and I got a response such as !!!!!, or 64 bytes sent and received, etc. then that means I am able to connect to the device that has the IP address of 192.168.1.1.  If I get the response of "Host unreachable", then that usually means that I am unable to "see" that particular device, or that device is blocking ICMP (pings, etc).  I hope this helps! :)

---

### Post by wieman01 on 2007-12-28
The current version of Network Manager which you use for wireless networking, does NOT support the use of Static IP Addresses. If you need it, please take a look at my WPA tutorial (signature). It will show you how to configure your client.

---

