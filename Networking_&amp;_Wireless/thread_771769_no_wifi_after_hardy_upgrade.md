---
title: "no wifi after hardy upgrade"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by mikeric on 2008-04-27
I just upgrded to hardy and now I can't connect to the internet. if I go to edit wireless netwroks my old network is listed, but I cant find anything else about wireless.

---

### Post by Wharf Rat on 2008-04-27
Does your wifi net have security installed?  WPA, etc?  If so, remove the security and see if you can connect.  

I had could see my wifi but no connection.  After removing security, I could connect.

After hours of playing with this, I decided to remove and reinstall the Atheros drivers on my T-61.  All is well and good now and we have a secure wifi connection.

---

### Post by villindesign on 2008-04-27
Which network card are you using? I have a R61 laptop with the intel 4965AGN network card. I can not connect to a network secured with WPA. How did you enable your connection?

---

### Post by mikeric on 2008-04-28
its my girlfriends old computer, not laptop. there isn't  any security on the wireless, I'm connected to it right now on my phone. I'm not sure what the wireless card is since the computer wsnt originally mine. it worked with with version 7.10 though.

---

### Post by formol on 2008-04-28
open a termimal and type "lspci" to know witch wifi card you have.  then search over internet and this forum, you may have to use madwifi or nidwrapper as driver.

---

### Post by mikeric on 2008-04-28
I ran that, but didn't get nything listed for wireless or wifi, would it be one of the ethernet controllers?

---

### Post by formol on 2008-04-28
run in terminal "lspci" and "lsusb" and post the result here

---

### Post by mikeric on 2008-04-28
I'm online on my phone so I cant type it all, any part in prticular I should look for?

---

### Post by formol on 2008-04-28
> **mikeric said:**
> I'm not sure what the wireless card is ... find witch wireless card you have

---

### Post by mikeric on 2008-04-28
nothing that comes up when I run that sys anything about wireless. it hs all the others listed but that's all. that's why I ws wondering if it was called something else on that.

---

### Post by formol on 2008-04-28
that's why i asked you to post the result, it will not say "i'm a wireless card" directly... i assume here that you are sure to have one.

---

### Post by Feenix3k on 2008-04-28
In Hardy a lot of the drivers for wireless have been changed. bxm43xx is no longer used it has been replaced with the following I got from my laptop:

configuration: driver=b43-pci-bridge latency=32 module=ssb

This driver blocks me from using ndiswrapper to run my wireless with the bcmwl5.inf. But I am finding in the forums that a lot of wireless is not working due to driver upgrades. The following link may help:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by mikeric on 2008-04-28
i got my laptop now, i ran what you said and this is what i got.
> mike@mike-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:04.0 Multimedia controller: Sigma Designs, Inc. REALmagic Hollywood Plus DVD Decoder (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
01:06.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
01:06.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

mike@mike-desktop:~$ lsusb 
Bus 004 Device 006: ID 1058:0401 Western Digital Technologies, Inc. 
Bus 004 Device 004: ID 0461:4d10 Primax Electronics, Ltd 
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 413c:5106 Dell Computer Corp. 
Bus 002 Device 003: ID 413c:5105 Dell Computer Corp. 
Bus 002 Device 002: ID 043d:007a Lexmark International, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:000


---

### Post by formol on 2008-04-29
your wifi card is:
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

here is the page description on the realtek website :[http://152.104.125.41/products/productsView.aspx?Langid=1&PFid=5&Level=6&Conn=5&ProdID=37]("http://152.104.125.41/products/productsView.aspx?Langid=1&PFid=5&Level=6&Conn=5&ProdID=37") and here is the driver page from realtek : [http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L]("http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L")

also, this webpage [https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L]("https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L") tell to use the .inf driver from win98 with ndiswrapper, you should take a look at it.

otherwise, there is other information here (naturally) [http://www.google.ca/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=a7W&q=RTL8180L+ubuntu+hardy&btnG=Search&meta=]("http://www.google.ca/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=a7W&q=RTL8180L+ubuntu+hardy&btnG=Search&meta=")

---

### Post by mikeric on 2008-05-04
I can swap files from my laptop to my external hardrive, is there any way with that i can do this without connecting to the internet?

---

### Post by formol on 2008-05-04
a priori, there is no need to use internet for this kind of operation.  use usb or firewire...

---

