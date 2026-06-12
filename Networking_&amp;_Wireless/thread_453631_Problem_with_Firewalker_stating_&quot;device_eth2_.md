---
title: "Problem with Firewalker stating &quot;device eth2 is not ready&quot;"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by uofs on 2007-05-24
I'm trying to build a small, secure network for cleaning virus'(re. MS) laden machines for work.  I am using a Thinkpad T42 laptop.  I have installed Ubuntu with the latest version of firewalker.  I have my internet connection coming in on eth0 and can successfully connect without any problems, I have a Startech UE1205CB pcmcia wired network card going to my 4 port router (D-link).  I followed the install/config instructions for the firewall and every time I try to start, it indicates "The device eth2 is not ready".  I have verified that this card works by trying to connect to the internet as well.  I have connected another computer directly to this card (using a crossover cable) and can see a small amount of network traffic on this card in the Network area of Firestarter.  If anyone can assist me, it would be greatly appreciated.  

Thanks.

---

### Post by elmerfud on 2007-10-25
I am having the same problem, doing essentially the same thing.

$ firestarter -v
Firestarter 1.0.3

$ uname -a
Linux xxx 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux

I had this working once upon a time.  I'll figure it out and report back.

---

### Post by elmerfud on 2007-11-05
In case anyone is watching this or searches it later, I figured out what was wrong.

It turns out that Firestarter throws that error if the interface doesn't have an IP address.  In my case, I set eth2 to have an IP address manually and all is now well.

---

