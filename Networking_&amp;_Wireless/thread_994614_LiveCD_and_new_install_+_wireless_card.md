---
title: "LiveCD and new install + wireless card"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by cferg590088 on 2008-11-26
I'm want to install gutsy from the LiveCD but the only thing holding me back right now is that it does not recognize my wireless card.  What I plan to do is install the wireless stuff I need after the install.  I have a windows box I can download to, and transfer the files with a flash drive.  What I'm wanting to know is what files do I need to enable my wireless card.

---

### Post by Ayuthia on 2008-11-26
We will need some information about your wireless card.  Do you know the make and model of the card?  If you have a wired connection that works in the liveCD, can you post the results of lspci -nn?

---

### Post by spcwingo on 2008-11-26
You really have to know the the make and model of the card.  With the Ubuntu live CD in open up a terminal and run either lspci if you have an internal card or lsusb if you have a USB card.  Copy and paste the results in your next post.

Edit:  Sorry Ayuthia, you beat me by about a few seconds.

---

### Post by cferg590088 on 2008-11-26
My wireless card is:
Linksys Rangeplus
Model WMP110

The results of lspci:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) 
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) 
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] 
01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary) 
02:01.0 Network controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01) 
02:02.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02) 
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by spcwingo on 2008-11-27
Since it's an Atheros based card see here for setup info:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Let me know how it works out for you.

Edit:Please disregard the the above.  That is for Intrepid.  I think for Gutsy you need madwifi.  I'll do some looking and see if I can find a how-to for you.

---

### Post by spcwingo on 2008-11-27
Ok, I have not found anything yet, but I got to thinking...have you tried ndiswrapper?  If you need the driver files I have downloaded them from here:

[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1175244795392&packedargs=sku%3D1175244562248&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=9539280708B06&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1175244795392&packedargs=sku%3D1175244562248&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=9539280708B06&displaypage=download#versiondetail)

After that I used Winrar (that I have running under wine) to extract the .inf and .sys files from the .exe file.  If you need those just let me know.  After you have those files ndiswrapper can be installed from the live CD.  Or you can download the files for ndiswrapper from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Just download the three files for Gutsy on your xp system and transfer them via your flash drive.  Install them in this order:

1)ndiswrapper-common
2)ndiswrapper-utils
3)ndisgtk

After that you can go to system>administration>install windows wireless drivers.  Choose install new driver and choose the driver inf file.  Hopefully that will get you up and running.  Let me know if that works or not.

---

### Post by cferg590088 on 2008-11-29
Sorry it's taken me so long to get back.  We had a bit of a family emergency and this is the first I've been online in a few days.

I installed ndiswrapper and loaded it with the inf file from the driver.  It tells me that the hardware is present, but nothing else.  No internet connection, nothing showing wireless networks available.  Am I missing something?

---

### Post by spcwingo on 2008-12-01
Try to manually configure connection settings through system>administration>network

---

