---
title: "Serial dialup modem connects (i think) but no access to internet?"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by boredman on 2007-05-25
I'm using feisty, and have managed to get the modem to produce reassuring noises and lights, but when i open Firefox, it's not connecting to internet. 
 
I've created the necessary ISP account & modem port settings in System > Administration > Networking, but i'm also confused as to why mine doesn't show any Activate or Deactivate buttons like i've seen in all of the how to's. Mine just has a green tick button in the top right corner, that when clicked, fires up the modem.
 
Any advice much appreciated.

---

### Post by Pocito on 2007-06-06
Hi,

I have the same problem. Does anyone know how to fix this?

Pocito

---

### Post by poe503 on 2007-06-07
Did you check the "set modem as default route to the internet" and "use the internet server provider nameservers" (under modem properties>options)?  

When you do get a connection to the internet, open the "add/remove" interface that is under "applications".  

Let it do its update thing, then find "Gnome PPP" which can be found by toggling "all open source applications" and download and install that.

  Disable the original network modem setup because it's crap and use Gnome PPP.  Works like a charm.

---

### Post by boredman on 2007-06-13
Thanks poe503,

Yes i did set the dialup modem as default, and entered all the relevant ISP details, but still had the same problems. And i agree, the setup program that comes with Ubuntu isn't great. 

So after a bit more searching on the interweb i came across Gnome PPP - i'll give that a whirl and post how i get on.

It would be nice if dialup was better supported, there seems to be a huge amount of people who have dialup issues, and like me, can't get ADSL.

---

