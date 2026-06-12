---
title: "Unable to get wireless working"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by smccroskey on 2008-10-11
Hi,

I am completely new to Linux and am trying to get it setup on a laptop for me to learn and use. I downloaded Ubuntu and installed it. I am unable to get the wireless working. I have searched through other posts, but most of their recommendations I am unable to do (e.g., it tells me to go to a screen I don't have). I also have not seen the same problem documented.

I enable roaming and set up my network (enter network name and key). I tell the system to connect, it tries for a minute and then pops up a message "Passphrase required by wireless network" I select the security setting (WEP 64-bit hex) and enter the key. It tries for a minute and then pops up that same message. It is an endless loop. It is the correct network name, the correct security setting, and the correct key. I can't turn off security on the network as it screws up all of the other computers running in the household (and makes other family members unhappy).

My wireless card is Linksys WPC54G.

I have no idea how to proceed.

---

### Post by smccroskey on 2008-10-11
Bump. Seriously, have no idea how to proceed.

---

### Post by stormcrow_wolf on 2008-10-11
In order to help you out any, we'd need to know what revision (version) of the WPC54G you have.  Different revisions have different chipsets and are, or can be, 100% incompatible with each other at the driver level.  Some have broadcom chipsets which are a problem on a good day (see my b43 woes post), some are ralink, some are... *shrugs*.  Anyway, we need the version number and if you can get it the chipset it uses.

---

### Post by smccroskey on 2008-10-11
It doesn't say, but given that the FCC ID is PKW-WPC54G-2 my guess is version 2.

---

### Post by Ayuthia on 2008-10-11
Can you go into the Terminal and post the results of lspci -nn (if you have a card) or lsusb (if it is a USB device)?  It will help us see what the card is using.

---

### Post by stormcrow_wolf on 2008-10-11
According to what I've googled that's a TI ACX 111 chipset.  Even including broadcom they are the LEAST supported chipmaker in the wireless realm in linux.  You can try the ACX linux driver [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

Remember this is a reverse engineered driver and it may or may not work for you.  I'd suggest either getting a new card with a ralink or atheros (52xx) chipset or trying ndiswrapper if that doesn't help you..  There's a link in this forum using that with Ubuntu... requires some extra fudging around not everyone is prepared to handle tho.

---

### Post by stormcrow_wolf on 2008-10-11
> **Ayuthia said:**
> Can you go into the Terminal and post the results of lspci -nn (if you have a card) or lsusb (if it is a USB device)?  It will help us see what the card is using.

Linksys models starting with WPC are all PC-cards.  AFAIK neither command will give you information about a PC-card.  However, come to think of it, watch dmesg or /var/log/messages when you plug it in each time and it may tell you.  If it's a v2 with an ACX chipset, see my above post.

---

### Post by Ayuthia on 2008-10-11
> **stormcrow_wolf said:**
> Linksys models starting with WPC are all PC-cards.  AFAIK neither command will give you information about a PC-card.  However, come to think of it, watch dmesg or /var/log/messages when you plug it in each time and it may tell you.  If it's a v2 with an ACX chipset, see my above post.

Thanks for the information about the WPC portion.  However, if it is a PCI card, lspci should be able to find it.  I did do a quick search on the WPC cards and lspci and it did bring up a few cards.  For this card, I did see one listed as a Broadcom 4306 rev 02 [14e4:4320]. 

If lspci -nn does produce a result, please post it.  It will help us be sure that you have the right solution for your card.

---

### Post by stormcrow_wolf on 2008-10-11
> **Ayuthia said:**
> Thanks for the information about the WPC portion.  However, if it is a PCI card, lspci should be able to find it.  I did do a quick search on the WPC cards and lspci and it did bring up a few cards.  For this card, I did see one listed as a Broadcom 4306 rev 02 [14e4:4320]. 

If lspci -nn does produce a result, please post it.  It will help us be sure that you have the right solution for your card.

PC Card != PCI card.  One goes in laptops, they used to be called cardbus, the other is... well, a normal PCI card for a desktop/server/etc.  Would be interesting if it does work tho... anyway... our lives would be so much easier if Broadcom would just play ball and release the hardware interface specs! :mad:

I've yet to see Linksys do this, but Netgear has been known to change chipsets without even changing the hardware version numbering on the product or device, (one reason i no longer buy their stuff), so there may be no substitute as to what dmesg/messages/ls* will tell us.

---

### Post by smccroskey on 2008-10-12
> **Ayuthia said:**
> Can you go into the Terminal and post the results of lspci -nn (if you have a card) or lsusb (if it is a USB device)?  It will help us see what the card is using.

I've attached the screenshot

---

### Post by GrandpaLeaman on 2008-10-12
Try following the instructions at this site.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope this helps!

---

### Post by smccroskey on 2008-10-12
I am unable to get past the first step. I get the error "Couldn't find package ndiswrapper-utils-1.9"

I am not able to get files from the Internet on this computer as the ethernet port is also not working.

---

### Post by Ayuthia on 2008-10-13
> **smccroskey said:**
> I am unable to get past the first step. I get the error "Couldn't find package ndiswrapper-utils-1.9"

I am not able to get files from the Internet on this computer as the ethernet port is also not working.

If you have the install CD, you should be able to install it by doing the following:
```
sudo apt-cdrom add
```It will ask you for the CD.  Once that is complete, do the following:```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by smccroskey on 2008-10-13
Okay, have ran through all of the steps given and while receiving no errors, also have no change in behavior. It sees the network, but won't connect.

---

### Post by Ayuthia on 2008-10-13
Is the router using WEP/WPA?  If so, can you test it without WEP/WPA enabled?

---

### Post by smccroskey on 2008-10-13
Yes, it is using 64 bit hex WEP. I prefer not to change the settings on the router as it affects 6 other computers some of which are running things required to have an internet connection. Besides, due to my lack of knowledge on Linux, I'm not exactly what it proves for the hassle.

---

### Post by Ayuthia on 2008-10-13
> **smccroskey said:**
> Yes, it is using 64 bit hex WEP. I prefer not to change the settings on the router as it affects 6 other computers some of which are running things required to have an internet connection. Besides, due to my lack of knowledge on Linux, I'm not exactly what it proves for the hassle.

I can't remember what network manager uses for default when it asks for the passphrase.  I was thinking it was 128.

You might try connecting from the Terminal:
```
sudo iwconfig wlan0 essid <myrouter> key <key>
sudo dhclient wlan0
```


The reason why I asked you to turn off encryption is to see if it is ndiswrapper that is giving you problems or if it is WEP.

---

### Post by thomasboleyn on 2008-10-13
Hi, sorry to kick a dead dog but my card doesn't seem to work in anything newer than feisty..lspci -nn tells me this..

00:09.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5212 802.11abg NIC [168c:0013] (rev 01)

I tried ndiswrapper and madwifi while in Hardy and Intrepid and could never get any joy out of either. Madwifi kept going on about 'previous modules' needing removal, even after a fresh install (must be related to the HAL driver I think). 

:confused:

---

### Post by smccroskey on 2008-10-13
Well, I've given up on Ubuntu. I've been messing with it for too long and it's requiring me to spend way too much time in terminal mode typing in commands I don't understand. I downloaded Madriva this afternoon and had wireless working within 20 minutes without having to go into terminal mode once. I could do everything through it's Network Center. So, thanks everyone for trying to help me, but I need to go to a version of Linux that works for me.

---

