---
title: "Home network - Ubuntu and Windows XP - Two NICs and a Crossover Cable"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Murxidon on 2007-03-03
Yelloo, I'm thinking about going back to Ubuntu after a (failed) attempt to set up a simple home network like I can in Windows.

I use ICS in Windows to allow my other Windows XP PC connect to this one and share internet connection, files and the printer that is connected to it. I have a NIC on both machines and connect them using a crossover cable. But I couldn't figure out how to do this in Ubuntu. Could anyone please explain (as you can tell, I am a total noob) how I could go about sharing the internet connection, files and the printer....?

---

### Post by Malac on 2007-03-03
> **Murxidon said:**
> Yelloo, I'm thinking about going back to Ubuntu after a (failed) attempt to set up a simple home network like I can in Windows.

I use ICS in Windows to allow my other Windows XP PC connect to this one and share internet connection, files and the printer that is connected to it. I have a NIC on both machines and connect them using a crossover cable. But I couldn't figure out how to do this in Ubuntu. Could anyone please explain (as you can tell, I am a total noob) how I could go about sharing the internet connection, files and the printer....?
Use Ubuntu on the machine that connects to the internet.
Install Samba (for file sharing) and Firestarter.
Set internet Connection sharing on in Firestarter.
Sort out the Samba settings (there are loads of posts on the forum about this between Ubuntu and Windows machines). It's very easy.
Set Windows Machine to use the LAN for internet connection.

Personally I manually configure the network addresses as I find it less hassle.
set the I.P. of the ubuntu machine to 192.168.0.1 netmask 255.255.255.0
set the windows machine IP to 192.168.0.3 and netmask 255.255.255.0
Then in Firestarter allow connections for lan or this IP specifically.
and away you go.

---

### Post by Murxidon on 2007-03-03
Oh thanks, sounds easy enough...?

Knowing me it won't go according to plan, but I shall try anyway.

Thanks.

---

### Post by Malac on 2007-03-03
> **Murxidon said:**
> Oh thanks, sounds easy enough...?

Knowing me it won't go according to plan, but I shall try anyway.

Thanks.
Most of the time setting up ICS is the easy part. It's trying to navigate round the various security of passwords and so on, so that the machine you want can get access to the other without letting anyone else in. :)
Any problems post back with output of ```
ifconfig /all
``` on ubuntu machine and ```
ipconfig
``` on Windows machine.

Good Luck.

---

### Post by Murxidon on 2007-03-03
Erm... Hi again, I've installed Ubuntu and Firestarter now, but having troubles with the ICS.

I have set static IP addresses for both my USB modem and NIC, but I am recieving messages like "Unknown error" and "The device is not ready (my NIC)" in Firestarter. How do I "allow connections for lan or this IP specifically" in Firestarter and how would I get windows to connect to the IP?

Thanks

---

### Post by Neobuntu on 2007-03-03
Yep, use 192.168.0.1 for the gateway computer/ICS NIC and (via crossover cable) to your second computer because the Internet is best connected through a router/gateway/firewall/NAT box (non-wireless given away for free) and re-set to 192.168.1.1 toward your ICS gateway computer. So with broadband cable "modems", they should go to a router (first) that you may have to change to 192.168.1.1.

This allows a wireless device (or another wired NIC) in your computer to access a router somewhere (as 192.168.1.1) and then still your hardwired Ethernet NIC can be a sharing Gateway too (when ICS is on) as 192.168.0.1 else the two gateways will not work.

So if you ever want to use an old laptop (with WiFi and wired NICs) as a gateway (from a remote room/location without cat5 cabling) to install/upgrade another computer with just a wired NIC, the laptops Wifi will see an Internet router as 192.168.1.1 and set it's wired NIC (ICS) to 192.168.0.1 as gateway for any other computer (crossover cable if directly; with out a hub.)

---

### Post by J4DED on 2007-05-15
I am having a similar problem with a twist...

I have an XP box with a wireless connection and I am trying to connect to my Xubuntu laptop via a cross-over cable.

I am unable to connect to the desktop with the laptop but my laptop is visible in my workgroup in Windows - It shows up as:
[laptopname] server (Samba, Ubuntu)
(User name)

I am then prompted to login but it is never accepted - It keeps prepending the username with the computer name but that isn't accepted either...

Does this ring a bell to anyone?

---

