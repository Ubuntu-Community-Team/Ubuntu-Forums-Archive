---
title: "Home networking... how?"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by gironja on 2006-09-27
Hi!

I was thinking is there's a way to have connected my Desktop and Laptop via a twisted pair cable or any other way. I know there's possible in Windows (I know is possible, but for me has been impossible, since none of the PC has seen each other). 

I want to do it to avoid having to use my USB Flash Drive to pass all files I have downloaded (or a backup) from the lap to the desk. or vice versa, and avoid having to remove the lap's hdd to put it on the desk. 

I appreciate your help on this!

btw. Both, desktop and laptop, are running AT LEAST ubuntu 6.06.

Thanks!


jNa

---

### Post by mips on 2006-09-27
First you need a cross-over LAN cable.

---

### Post by Iowan on 2006-09-27
Are you talking about a network-type connection (via NIC), or a direct-type connection (serial or parallel port).  My router has a serial TTY option - fine for "remote" login, but file transfer would be painfully slow.

---

### Post by mips on 2006-09-27
Well twisted pair was mentioned so i assumed a normal UTP Cat5 cable or something of the sorts.

---

### Post by Iowan on 2006-09-27
Certainly no argument that the LAN-type connection would be preferred (faster and easier to set up)... unless the 'puters don't have NICS - and most have them built-in anymore.

---

### Post by gironja on 2006-09-27
Sorry for leaving things unclear...:( 

Iowan: yes, it is via NIC.

Now that you mention it, with windows, I was able to connect to the other's computer (at home... right now I'm at college's home... "hospedaje" in Spanish.. really don't know its translation for English) via my router, but it was a long time ago. Since that last time (for more than a year) I had no chance to do it. But right now I want to do it via the Desktop's and Laptop's NIC, since I think is faster than serial or parallel (well... I don't know, neither, how to do it via those). One question comes to my mind... is it possible through USB connection?

mips: Yes, it is a "normal UTP Cat5 cable" :)

---

### Post by mips on 2006-09-27
I've never tried USB networking so cannot comment.

If you go the PC-PC lan route it is pretty simple, all you need is a cross-over lan cable.

---

### Post by gironja on 2006-09-27
Is the cross-over==twisted-pair?? 

I must have one at home; if not, I have cable to do it. But (sorry for the comparison... I'm kind of noob here, and my backgound wasin m$...) I once tried in Win, but no luck: The PC's din't saw each other... 

The question is, Ubuntu is able to see the other PC once it has been plugged on with the cross-over cable?

---

### Post by mips on 2006-09-27
A cross-over cable is a normal UTP lan cable **BUT** the tranmit & receive pairs are swopped over on one side of the cable.

[http://www.zytrax.com/tech/layer_1/cables/tech_lan.htm](http://www.zytrax.com/tech/layer_1/cables/tech_lan.htm)
[http://www.incentre.net/incentre/frame/ethernet.html](http://www.incentre.net/incentre/frame/ethernet.html)
[http://psacake.com/web/fd.asp](http://psacake.com/web/fd.asp)

---

### Post by Iowan on 2006-09-27
[http://en.wikipedia.org/wiki/Crossover_cable]("http://en.wikipedia.org/wiki/Crossover_cable")
Quick reference.  Once the PC's are connected via crossover, they'll still both need to be set up to the same subnet (but different addresses, of course). If you have another straight cable and a hub, you're set too.

---

