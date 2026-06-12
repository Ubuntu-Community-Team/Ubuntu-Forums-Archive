---
title: "[56K] Notebook IBM Lenovo R60e"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by xavierLos on 2007-03-12
Good day,

In first time sorry for my english..  

In second time i ask your help.. 

I have got a notebook and i don't have fast line.. In order to connect to me to Internet I use the inner modem of the notebook..and this is only reason for use windows xp, because with ubuntu 6.06 the internal modem is not found..

But, i go to System - Administration - Networking i watch the wireless, ethernet and modem icon, 
but the modem is not activate, i active the modem but i serch or ddetect this device the S.O. answer "The device is not found".. because??

Then I have executed the command lspci.. this is the output:

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 21)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4227 (rev 02)
0000:15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

	
You can answer some thing??
I have tried on Internet, but I have found little things and inasmuch as they are a newbo you can help me little?
For the exemple i found thi page

	
but I have not understood like making to work the modem. 
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e)
Thank for all..
and still excused my English.

by
alessandro

---

### Post by dstew on 2007-03-12
Your computer has a software-driven modem, also called a WinModem. In order for these types of modems to work with Linux, you need to install some software. See this link, and pay attention to the part labeled Software Modems:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by xavierLos on 2007-03-12
Thank for the reply, 

but i already read this document, for serch the chip set i launch the scanModem softwar, tthi programm created in my home directory one directory with nome Modem.

Into this dir there are a series of files, but I do not know which to read in order to understand the type of chipset. 

You say to me which of these to post and like understanding that modem I have? 
	
I hope you succeed to understand 

thx
alessandro

---

### Post by xavierLos on 2007-03-13
up. .

sorry if to make me therefore. but I want to know if I have possibility in abandoning windows and to only use only linux also to 56K. thanks thousands

---

