---
title: "Internet Connection Sharing (Vista Host) dial-up"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by Nixarter on 2011-01-30
I've been searching (google and this site) for two hours now, and I have not found a tutorial/thread that I think applies to my situation either because of different setups, or different needs.  Well, at least, I don't think any applied... they are extremely hard to follow for me.  Anyway, I am on vista now via a dial-up connection.  I need to use synaptic on ubuntu (9.10 I think) and (to save a convoluted explanation) I have to go though vista to get to the internet.

So, I have the 3 network devices needed (modem and an ethernet card on vista, and an ethernet card on Ubuntu).  I have connected the ethernet cards with a lan cable, and it seems to be physically fine (vista says network present, though limited connectivity).  It is on private network, and firewall settings are fine, but Ubuntu still says no connection available.  I know ubuntu is connected to this computer because when I disconnect it, vista looses connection on the network.  What am I missing?  If there is some software I need, I can only use what I already have installed (catch 22: I can't get anything else until I have an internet connection... and if I had one, I wouldn't need the software).  Please, please help! :'(  link to tutorials is fine.  anything! lol

---

### Post by sikander3786 on 2011-01-30
So if I understood you correctly, you have got a Dial-up internet connection on Vista and want to share it to Ubuntu via the LAN card. So,

Internet Connect > Vista Modem > Vista LAN Card > Ubuntu

First of all, you need to run the internet connection sharing wizard on Vista. Choose your modem as the Internet Connection and choose your LAN card as the Network. Once completed, the wizard should automatically assign 192.168.0.1 as IP to your Vista's Lan card and will enable dhcp server on that. So, you won't need to set an IP address on your Ubuntu box.

In your case, everything needs to be done from Vista. Only in case dhcp server is not enabled, you might need to assign the same netmask to your Ubuntu box. But I don't think you need it.

Did you try running wizard on Vista?

---

### Post by Nixarter on 2011-01-30
I just searched around, and it appears the "internet connection sharing wizard" stopped with xp.  would just the internet connection wizard work?

If I'm wrong (which I hope I am), how do I get to the ics wizard?

---

### Post by Nixarter on 2011-01-30
after checking the connection more, the vista ip for that card is already 192.168.0.1.  how do I tell if dhcp is enabled?  On the ubuntu box, it is set to automatically do everything via a dhcp server (which, hopefully could be the vista box)... but something's not working.  either the vista box isn't acting as a dhcp server, or something else is wrong.  :(

---

### Post by P4man on 2011-01-30
ICS is still there. Have a look here:
[http://windows.microsoft.com/en-US/windows-vista/Using-ICS-Internet-Connection-Sharing](http://windows.microsoft.com/en-US/windows-vista/Using-ICS-Internet-Connection-Sharing)

---

### Post by Nixarter on 2011-01-30
yeah, the ics is there, but the wizard for it is not (at least, not that I can find).  And I've already been on that page (it helped me to get to wher eI am now).

In my nic card properties, it shows the correct ip addy 192.168.0.1, and subnet mask... but it says "DHCP Enabled [space] No".  Why is it not enabled?  How do I enable it?

---

### Post by P4man on 2011-01-30
You mean the nic on the windows machine? You dont want DHCP enabled on it, as you have no DHCP server for it. It needs a static IP like it already has.

If for some reason the ubuntu machine isnt getting an IP address from the windows machine, try setting a fixed IP for it, like 192.168.0.2

---

### Post by sikander3786 on 2011-01-30
As the IP on your Vista NIC is 192.168.0.1 as you mentioned above, set the Ubuntu IP as 192.168.0.2 and gateway as 192.168.0.1. Subnet mask would be the same.

You can right click the network icon in Ubuntu's system tray > Eth0 > Edit > IPv4 Settings > Choose Manual under Method > Add.

---

### Post by Nixarter on 2011-01-30
YAY!  You were right about DHCP, so I checked the ubuntu box and there was one box still able to be edited after setting everything to automatic... and it was regarding DHCP... so I changed that value to 192.168.0.1 (the ip addy of the vista box, ie the dhcp server on the lan) and it worked!  So it just didn't know where to look for the DHCP server.  Ohh, well.

It was bitter-sweet, though.  The packages I needed to update the program (the whole reason for this several-hour-long fiasco) aren't available for my version, and my version is no longer supported... and I can't update it on dial-up, obviously.  *sigh*  Ohh, well.  I guess I'll have to go by a library at some point.

Thanks again for the help guys!  Hopefully someone can put it to to better use than I did hahaha

---

### Post by P4man on 2011-01-30
You could also request a free cd here:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Although it takes several weeks,so a trip to the library is probably a better idea. Consider downloading ubuntu 10.04.1, its long term supported. Since you dont seem to upgrading very frequently, stick to LTS versions, so at least you can upgrade several years later.

---

### Post by Nixarter on 2011-01-30
yeah, 10.04 is probably what I'll go to.  I just hope I can go directly to it from 9.04...

---

### Post by P4man on 2011-01-30
Nope you cant since 9.04 wasnt a LTS version either. You can upgrade to 10.04 directly from either 8.04 (previous LTS) or from 9.10 (which is still supported for a few months). 9.04 is end of life:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

That said, I tend to prefer clean installs anyway and do dual boot until I know its okay with my hardware.

---

