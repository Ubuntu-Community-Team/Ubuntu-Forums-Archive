---
title: "How to network with a dialup connection"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-11-24
Computer#1 has 8.04 with all updates applied, and uses a dialup connection, running wvdial, plus I use Firestarter as a firewall. It works okay, but very slow of course.

Computer#2 has 8.04, but not with all updates applied.

I want to be able to ..

1.  Use Computer#2 to connect to the internet via the connection on Computer#1
2.  Have both computers being able to browse each others file systems, and also copy files from one to the other.
3.  Have sufficient security in place.

I have an ethernet setup, an 8 port hub/swich, with the LAN cables just plugged into port1 and port 2, and have adjusted the network settings on bot computers, but I can't do any of the objectives listed above.  :(

Does anyone know how to do this please ?

---

### Post by oygle on 2008-11-24
[This thread]("http://ubuntuforums.org/showthread.php?t=660457") has a very similar setup, although one computer was Ubuntu, the other Windows.

My situation is 2 Ubuntu computers, so which one needs the ipmasq and dnsmasq packages installed ?

---

### Post by mal on 2008-11-24
oygle,

I can't really help much with the network sharing, but I can say that ipmasq and dnsmasq need to be set up on your computer with the modem connection.  You need to share its connection with your second computer.

An alternative option might be to temporarily connect the modem to your second computer while you carry out the package upgrade, if this is physically possible.

Regards,

Mal

---

### Post by oygle on 2008-11-24
> **mal said:**
> I can't really help much with the network sharing, but I can say that ipmasq and dnsmasq need to be set up on your computer with the modem connection.  You need to share its connection with your second computer.


Okay thanks. I did have a quick look at those 2 packages, one said something about compiling a kernel, but I assume it's just a straight install.

Certainly, if I can add extra security to a dialup computer (I think one of those packages had NAT), it will be a real bonus, as the other option would have to be something like IPCOP.

> **mal said:**
> 
An alternative option might be to temporarily connect the modem to your second computer while you carry out the package upgrade, if this is physically possible.


Yes, that's a good option, and fairly easy, they are side by side, just a matter of switching the COM port cable, and install wvdial (and maybe Firestarter, etc) on the second computer.

Each computer can ping each other, but can't use Firefox, or ping any outside IP addresses or domains from the second one.

Thanks a lot,

Oygle

---

### Post by oygle on 2008-11-24
mal,

I installed ipmasq and dnsmasq, then tried the second computer with FF, and did see a few lights busy on the modem, checked the Firestarter log, and it had port 80 from the second computer listed. Had a quick read on policies on the Firestarter site, then added one, guess what, the second computer has internet now.   :popcorn:

But then the first computer had no internet, had to add another policy, no doubt will have to read up a bit on Firestarter, to twek the settings, but all looks great.

Thanks very much,

Oygle

---

