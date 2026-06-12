---
title: "bcm4309 recognized as 4306 with fresh 7.04"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by nae5 on 2007-06-24
sudo lspci

02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

this is after a fresh install of 7.04 on a dell inspiron 600m with 1.5 pentium M proc. 512 before installing updates or anything else.

I have read much in the forums on the topic and it seems the increased wireless support in 7.04, has a hole here. I am still new to ubuntu and want to help as well as gain wireless, which is the only thing i cant get working on this computer. 

im new and dont know much, but it seems the software for the wireless card is incorrect, can i just change the to the right one or do i have to wrig something up?

i have tried ndiswrapper and fwcutter in the past, but was unable to get them to work because i did not fully understand what i was doing and messed up everywhere im sure. i have my original driver cd as well as a winxphome partition on this hard disc. 

so if someone would like to help it would be much appreciated and i would try to post a documentation for this specific card and computer.

.. i have checked supported cards lists in the past and found this card to be on ndiswrapper or fwcutter or something, but not the original 7.04 install.. i will check up on those.

---

### Post by Ayuthia on 2007-06-25
You might try checking lspci -n at the terminal.  It should look something like: 14e4:4311 (that is mine--yours will be slightly different).  Just look for the 02:03.0 number on the left from your lspci output:
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

That will help you find the right driver.  In some cases the Broadcom card number is different than the chipset.

---

### Post by acadiansteph on 2007-06-25
You might want to try this!. I have a Broadcom 4318 (bcm4318)  and followed the instructions. It might work on your Broadcom chipset. The installation as a script already written for it.And I believe the tar.gz file includes many Broadcom chipsets in the scripts. I hope it helps. Here is the url:   [http://ubuntuforums.org/showthread.php?t=197102&highlight=Howto+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=Howto+4318) . But if you are unsure if this will work or not I suggest you do a search for bcm4309. Doing this worked for me, but it may not for you; I do not have enough experience to know this. In any case let me know of the outcome of your wireless.

---

