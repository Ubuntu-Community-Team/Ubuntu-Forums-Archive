---
title: "Wireless on HP Pavilion:  what's 'child returnd status'?"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by NoMorVista on 2008-08-30
Hi, I'm a brand new linux Newbie, since I hate vista with a fiery passion and I was forced away from XP.  I'm happy so far except for everybody's favorite problem: Wifi.  I have an HP Pavilion...tells me it's a dv6700, a dv6915nr specifically.  I'm running Hardy on this baby, I've got 4 gigs of ram, though I upgraded from three adn I haven't double checked to ensure that Ubuntu's seeing it.  I still have it able to dual-boot with vista, and the card is fine in there.  I tried lspci, got: 

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)




on trying the instructions for i386

 grifter@grifter-laptop:~$ sudo apt-get install build-essential
[sudo] password for grifter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
grifter@grifter-laptop:~$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--16:00:18--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz.1'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [application/x-gzip]

100%[====================================>] 485           --.--K/s             

16:00:19 (29.33 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz.1' saved [485/485]

grifter@grifter-laptop:~$ tar xfz madwifi-ng-r2756.tar.gz
tar: madwifi-ng-r2756.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



I'm pretty savvy in general,  but I know nada about linux specifically.  I just know that right now the button stays off even when switched on, and my card doesn't work, so any help would be very appreciated! Thanks!

---

