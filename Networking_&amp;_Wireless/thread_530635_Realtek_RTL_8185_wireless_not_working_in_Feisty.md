---
title: "Realtek RTL 8185 wireless not working in Feisty"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by netron on 2007-08-20
fresh feisty install.  
have done all the recommendations - commenting the blacklist and rebooting

/etc/modprobe.d/blacklist
#blacklist r818x
#blacklist r8187


dmesg:
lots of entries like this:
"rtl8180:  WW: No more TX desc, returning 2a of 2a"

lspci:
Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller

ESSID ; add a dummy letter to the end  (bug in ifconfig.c) so that "mynetwork" isnt shortened to "mynetwor" 

i note from the the Wiki that this chipset worked fine in Dapper and Edgy.

Is anyone bug fixing this?  what is the source of the problem? i dont mind doing a fresh Edgy install instead just to get it going, but i am interested in why it isnt working in Feisty.

---

### Post by MinionTech on 2008-02-17
Has anybody had luck with this?  I'm having the same problem and getting the same error message with an Airlink 101 AWLC3028.  Ndiswrapper was installed with the Windows driver available from Airlink's site and I tried another driver with the same PCI ID, as mentioned on ndiswrapper.sourceforge.net.  I'm following the directions from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

If anybody can help it would be greatly appreciated.

Here are some of my details:

03:00.0 Ethernet controller: Realtek Semicondictor Co., Ltd.  RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

03:00.0 0200: 10ec:8185 (rev 20)

---

### Post by MinionTech on 2008-02-18
Got it!  The answer was in kevdog's "My own Personal Ndiswraper Guide - Troubleshooting Tips Included" thread, found here: [http://ubuntuforums.org/showthread.php?t=574501&highlight=rtl+8185](http://ubuntuforums.org/showthread.php?t=574501&highlight=rtl+8185).  It said to use Windows 98 drivers for RTL (Realtek) chipsets.  Kudos to him for the great guide!

---

### Post by generic_idea_machine on 2008-05-04
Realtek release a linux version of the driver in December for the 8185

I just installed it (successfully).

[http://122.146.118.42/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false](http://122.146.118.42/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false)
If the link does not work for some reason, just search on their site for "8185"

---

