---
title: "Wired connection--can't connect to internet!"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by Lekhesis on 2007-08-17
I just installed 7.04 on my computer; I recently purchased a laptop with Windows Vista pre-installed and after butting heads with it for two days I decided I was going to make the switch to Linux and, hopefully, not look back.  Unfortunately, in spite of the fact that my DSL connection has worked perfectly for months, I can't seem to get online with Ubuntu.

Here's my situation:

I had an XP machine on which my internet connection was happy and functional--the only issues I had with it were related to something being filtered improperly, or a rogue line splitter messing everything up until I found it and unplugged it.

Ever since I've been using Vista, with the exact same setup as before, my internet's been spotty--it's incredibly slow even though I'm getting reported speeds of 864kbps/160kbps, and boots me offline whenever it feels like it and won't let me back on until I run the network diagnostic (interestingly, once I uninstalled Norton and replaced it with my own antivirus program, it's been doing that less frequently; wtf?).  After Googling around a bit, though, I'm writing this off as a Vista problem--it seems like everyone and their grandmother is having the same difficulties.

I'm dual-booting Ubuntu and Vista, and even though the internet works under Vista--just not incredibly well--it doesn't seem to want to work in Ubuntu.  At all.  Whenever I run sudo pppoeconf, I get this bewildering message:

> Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond.  Please check your network and modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem.

I should think that my cabling is fine, given that it works in another operating system on the same computer, and I have no idea what this mysterious "other" pppoe process could be.  I can't obtain an IP address through DHCP; I just end up with a 169.254.x.x address and a bunch of failed DHCPREQUEST and DHCPDISCOVER attempts.  I've tried setting a static IP address, but even though I've double- and triple-checked the subnet mask, default gateway and so on, that's been a no-go as well.

I don't have a router, wireless or otherwise; the only thing I've got is a Westell 6100 modem.  My computer is an Acer Aspire 5050-3785 with a Realtek RTL8139/810x Family Fast ethernet card.

I'm completely stumped.  I'm also getting the feeling that I've missed something terribly obvious since I'm a total newbie to Linux and don't know my way around yet, but I haven't got a clue what that could be.  Help?  :confused:

---

### Post by Nexus... on 2007-08-17
I'm not an expert, but when I had to set my internet up with Ubuntu I had to do something strange.

Left click on the network icon in the top right hand corner of the screen. 
Right click on the "Wired Connection" 
>>>Choose the option of "Static IP"

>>>>Fill in the boxes (I am not 100% sure on what you personally would put in there as I connect through a Router) 

>>>>>When you have filled in the boxes go choose change the "Static I.P" to "DHCP" 

I don't know why this worked on mine but I sincerly hope this works on yours, like I said I am no expert and sorry if my instructions are a bit sketchy. :) Good Luck.

---

### Post by matthew.lns1 on 2007-08-17
Did you look in restricted drivers manager to se if your card needs and driver that need to be enabled? Did you enable the card in network manager?

---

### Post by Nexus... on 2007-08-17
Yeah make sure it has a tick in the box next to the wire connection....

---

### Post by NutrOn on 2007-08-17
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)
check ect./resolv./config. and try sudo touch on the resolv dir. Try using wvdial and gnome ppp
--NutrOn

---

### Post by Lekhesis on 2007-08-17
Yes, my NIC is enabled.

I checked the restricted drivers, and the only ones on the list were the Atheros Hardware Abstraction Layer (enabled) and the ATI accelerated graphics driver (disabled).  Nexus, I actually did try entering my IP address statically and then enabling DHCP without erasing anything last night, out of sheer laziness--it didn't seem to do anything.  :(

I ran sudo dhclient eth0 while I was set to a static IP (didn't notice I wasn't set as a DHCP client, heh) and got this:

> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/00:1b:24:40:a5:9a
Sending on   LPF/eth0/00:1b:24:40:a5:9a
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.43 -- renewal in 40129 seconds.

Yay!, said I.  It's finally working!

...Not quite.  I tried pinging 192.168.1.1 and got 'Destination Host Unreachable,' then noticed I wasn't a DHCP client.  Set myself to DHCP and tried again.  Nothing.  DHCP server won't acknowledge me anymore.

What.  :???:

Also, I'm not too sure how a dial-up app is going to help my DSL connection.

---

