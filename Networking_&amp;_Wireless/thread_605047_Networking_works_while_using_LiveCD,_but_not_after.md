---
title: "Networking works while using LiveCD, but not after installing 7.10"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by Robertjm on 2007-11-06
Hi all,

Got a strange one. Have an Asus A2500H notebook computer. Tried the LiveCD for a few days and had absolutely no problem copying stuff to and from the laptop to my networked PC (Vista no less!!). 

Well, today I went ahead and installed the actual 7.10 on the notebook's drive and restarted the computer. NADA! What's funny is that it sees the local WIFI connections that are around here, and it even looks like there is receiving traffic coming in after "connecting" to it. However, when I try to connect out I'm timing out almost immediately.

Anyone have any thoughts? I'm baffled since it worked with the LiveCD.

Robert

---

### Post by kalabp on 2007-11-06
I have the same problem with my Asus A9RP laptop, but with the wired network. It was fine in Feisty, it is fine using the Gutsy Live-CD (what I am using now) but will not work from the Gutsy hard disk installation. Using an AirLink 101 USB network adapter works with WPA security but the connection is not reliable even when I am in the same room as my D-Link DI-614+ router.

Peter

---

### Post by kalabp on 2007-11-06
Well, comparing the /etc/network/interfaces from the Live CD session and my hard disk, I decided to try removing references to eth0 from the hard-disk installation of Gutsy. This sort of works for the wired network interface now, but I seem to have to manually run "sudo dhclient" before I can actually connect to the internet. Progress of sorts...

---

