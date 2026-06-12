---
title: "WPA appears a no go, plan B -Drapper release"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by waynepr72 on 2006-12-05
Hi All,

I have tried a number of things to get my wireless card in Ubuntu to work with WPA security with my TP-Link card but to no avail.  If anyone is in the same boat and worried about WEP, here are a couple of things I thought of that will make your network more secure using WEP encryption.

* Allow access by MAC address and deny any other wireless cards not in the list. 

* Limit the number of IP addresses on your router, i.e. allocate permant IP addresses to your MAC addresses on the network. My router allows me to set up an IP range, from 

* Turn off the Broadcast of your Network unless adding machines.

These are a few of the ideas I thought may make my wireless network more secure and give anyone thinking of trying to access a few hurdles to overcome.  I am sure with over 1/3 of all wireless network not secured with any security they will go on and find an easier target, with any luck!

---

### Post by handaxe on 2006-12-05
The steps you list will all help - particularly the MACs and hidden ESSID.

Have you tried the following link

[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462) for a wpa capable connection manager?  No promises tho'

HA

---

### Post by waynepr72 on 2006-12-05
Thanks for the link, I did see that amongst quite a few others.  I personally think the native driver in Linux for my PCMCIA LP-link card just does not support it as far as I can tell. I did try ndiswrapper and the Windows drivers for the card but I could not get them to install for some reason.

My network is working will all my PC's, Windows and Linux machines and I have I think added decent security by limiting MAC addresses and IP address plus turning off broadcast, it should give anyone trying to get into my network a bigger hurdle than just encryption with WEP.  

I just didn't want to get frustrated with this and give up on Ubuntu, I will sit back and take stock then re-look at it at a later time when more in tune with the new OS. I am happy my security is stronger set up like this.

Hope this improves other networks who are in the same boat as me.

Regards,

Wayne

---

