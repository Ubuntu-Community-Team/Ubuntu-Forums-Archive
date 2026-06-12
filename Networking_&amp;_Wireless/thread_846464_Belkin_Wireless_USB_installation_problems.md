---
title: "Belkin Wireless USB installation problems"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by TangledVeins1208 on 2008-07-01
Hi everybody.  I have been scrounging these forums as well as Google for a successful guide to making my new Linux box wireless.  I bought a Belkin F5D7050 version 5 and have lost the installation CD that came with the device.  I went to the support site @ Belkin and downloaded the driver files for WinXP2K, extracted the driver files BLKWGU.sys, BLKWGU.inf, and BLKWGU.cat into /MyAccount/home/belkin.

I am running Ubuntu 8.04 i386 Hardy Heron with an Intel Celeron 430 processor, 2 gigs of PC-5300 and have been at this for days trying to get this rig wireless.  I do have access to an internet-ready computer and have been transferring files via USB flash drive.  Absolutely love Ubuntu and Fedora, but am so lost when it comes to simple tasks such as this one (still green) and am calling on you for pearls of wisdom.  

In all the tutorials I've seen, when my Belkin F5D7050 is mentioned, the driver file cited in those tutorials is something like RT73, RT2500, and so forth, but if I'm not mistaken, I have BLKWGU.  Despair, how heavy my heart is for a way!  This is a fresh install of 8.04, and I even tried it in Fedora Core 9, same loose ends.

---

### Post by chili555 on 2008-07-01
> driver files BLKWGU.sys, BLKWGU.inf, and BLKWGU.catThese are the Windows drivers you would use with ndiswrapper, and these:> RT73, RT2500are the built-in Linux drivers which may or may not work with your card and may or may not work well.

If you download and install *ndisgtk, ndiswrapper-common* and *ndiswrapper-utils-1.9* for Hardy from here: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndis](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndis) you will get a new menu item, probably under System-Admin-Windows Wireless drivers. Point it at /MyAccount/home/belkin and it should do all the messy parts for you. 

You will download .deb files which may refuse to install because they depend on each other. You may be able to do:```
sudo dpkg -i ndis*
```or, you may have to force like this:```
sudo dpkg -i **--force** ndisgtk-blah-whatever.deb
```Then do the others as well.

---

### Post by TangledVeins1208 on 2008-07-03
Thank you kindly, I'm so mystified about all of this, after all the failed attempts and dead ends I've been fumbling through.  Now that you've helped me understand what I've got, I can figure out how to put it all together.  Thank you, wish me luck!  ^_^

---

### Post by TangledVeins1208 on 2008-07-04
WELL glad to say something you mentioned went perfectly; ndis* installed, was missing the GUI for the Windows Wireless Drivers which, by the way, is amazing. THANK YOU.  However, I'm still not yet wireless.  v_v

To walk you through what I did immediately after seeing your reply, I cabled up my new Cat6 ethernet cable to the PC, plugged in the Belkin USB adapter, and booted up the Windows Wireless Drivers app.  The first thing I saw was an entry for my Belkin, with a red X through it saying "Invalid Driver Installed".  Naturally I removed the driver, and reinstalled the exact same BLKWGU.inf file from MyAccount/home/Belkin as you directed.  It went back in, but this time the app loved the driver.  ?  Anyway, I was able to see my wireless connection (I'll refer to it as WiL0 from here on in) and am receiving the signal at 67%, which is fine.  I went into Network Settings (System>Administration>Network) and entered in the ESSID, Password type, and my network password.  I left the connection settings to Automatic configuration DHCP and hit OK, at which point the app changed connection settings to my selection.  I disconnected the Cat6 cable from the PC, and crossed my fingers for WiL0.

Here's where it gets weird.  I go into Network Tools (System>Administration>Network Tools) and check out the Devices tab.  In the drop-down list for Network Device I have 2 Wlan entries, wlan0:avahi (has my settings I applied above) and wlan0.  The latter, wlan0 is absolutely dead, not active, no packets sent nor received, no collisions (wouldn't expect any since I'm not in a bus topology).  Wlan0:avahi is successfully connected, active, I got my MAC Address listed, Link Speed is 54 Mbps (speed G) but again dead as far as packets sent/received.  My IP address is listed, protocol IPv4, my Netmask/Prefix is listed, my Broadcast is listed, and I'm stuck again.  ^_^  THANK YOU for a push in the right direction, at least I've got this far!  I'm sure there's something dubious I've not selected yet.  C'mon WiL0, I can see you.

I'm borrowing my friend's CAT6 while his PC's in the shop for virus removal.  Can't wait to FDISK /all my Windows partition before mine contracts HIV.  Gotta get this WiL0 up and then it's off with the M$ shackles!

---

### Post by chili555 on 2008-07-04
> wlan0:avahiThis is a placeholder interface that's created when the computer cannot get a valid connection from your router or access point. It tried to associate but failed. Either it doesn't like your ESSID (Linksys is not linksys is not Linksys2) or your encryption. Please double-check whether you have WPA or WPA2, whether your WEP is Hex or ASCII, etc. and try again.

---

### Post by TangledVeins1208 on 2008-07-05
Fail.  I fail.

In order to have 100% precision for the network settings, I have gone over to the Windows PC that the router is hard-wired to and gone into the Linksys WRT54G Wireless Settings app.  I Print Screen, and save the capture in M$ Paint onto my USB flash drive.  I am now back over at my Linux box.

My Linksys WRT54G Router by screenshot is the following (SSID=Panther):

Security Mode:  WEP
Default Transmit Key:1
WEP Encryption: 64 bits 10 hex digits
Passphrase: ***********
Key 1: asdf123456
Key 2: fdsa123456
Key 3: asdf654321
Key 4: fdsa654321

This being said, I launch the Network app (System>Admin>Network), go into wlan0 Properties:

  Wireless Settings
Network Name (ESSID): Panther
Password Type: WEP key (Hex)
Network Password:  I've tried all keys one at a time

  Connection Settings
Configuration:  Automatic configuration (DHCP)

And to think Tux could just frown on my PC and all would be magically fixed...

I also disable ROAMING mode as I'm not roaming, and hit OK.

I then launch the Wireless Windows Drivers app you suggested (love it) and my blkwgu.inf reports "Hardware Present: Yes".

I then launch Network Tools (System>Admin>Network Tools) and under the Devices tab the default Network Device is set to Loopback Interface (lo).  I have no idea what this is, but it's not my wireless.  I use the drop-down menu to select wlan0 instead of Loopback and there is no IP information, I'm transmitting 1710 packets, 0 errors, 0 received, 0 collisions.  

In addition to all this, while in wlan0 Properties (where I've configured my ESSID and all) if I click on the drop-down menu for Network name, my other router shows up at 23% signal strength.  There is no password for that router, and has WEP encryption as well.  I am unable to connect to it all the same, running into the exact slew of loose ends I get with my Linksys WRT54G SSID=Panther.

I am still very optimistic about finding a resolution; someone I'm sure has already run into this problem, and others who know what they're doing avoid whatever problem I'm in ^_^  Again, thank you for helping me out Chili555

---

### Post by chili555 on 2008-07-05
> Thermaltake Big Water 735 w/ '79 Chevette heater-coreFar out, man! 

Please try, in a terminal:```
sudo iwconfig wlan0 essid Panther
sudo iwconfig wlan0 key asdf123456
```Substitute your actual key #1 here.```
sudo iwconfig ap 99:9F:CC:E6:EA:7C
```Since we have two or more wireless routers that the machine might want to connect to, let's specify the MAC address of the one we actually want. The MAC address is easily found with:```
sudo iwlist wlan0 scan
```> wlan0      Scan completed :
          Cell 01 - Address: 99:9F:CC:E6:EA:7C
                    ESSID:"mylilrouter"
                    Protocol:IEEE 802.11bg
---snip---Or, the old-fashioned way; it's on a sticker on the bottom of your WRT54G.

Now do:```
sudo dhclient wlan0
```Let us know.

---

