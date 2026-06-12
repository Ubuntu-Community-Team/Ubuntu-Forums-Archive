---
title: "[Ubuntu 14.04 LTS] Cannot connect to internet trough router"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by lymphor on 2014-08-21
Hi everybody!

I'm using **Ubuntu 14.04 LTS** and today a family friend installed a **router** so that I could also use internet via wireless connection. My PC, however, is still receiving internet from the router trough a wire that enters into the **LAN** of the PC. I was not at home at the moment of installation, and my friend didn't know how to use Ubuntu. Therefore he set up the connection only for **Windows 7** (which I am also using).
Could anybody please help me set up my Ubuntu connection so that I can use internet?
I have attached a screenshot of the settings I was able to catch from Windows.

Thank you in advance!

---

### Post by roger_1960 on 2014-08-21
Hi

I think you are saying thatUbuntu works over the wired connection.  It should if W7 does.

To enable wifi click on the up/down arrows in the top right of the task bar.  Click on enable wireless and wait.  The network card should scan for and find the wireless network.  Select it and enter the password when needed.  Once connected to wifi you can unplug the lan cable afetr clicking disconnect under the ethernet network line at the top of the drop down.  This should work so long as auto DCHP is enabled on the router (which it appears to be)

Roger

---

### Post by ajgreeny on 2014-08-21
I think you will have to unplug the cable and possibly reboot before you will get wireless to connect; I certainly do with my router and hardware as the wired ethernet LAN takes priority over wireless and will not let it start.

It would be useful to know the chipset of your wireless adapter so show us the output of command ```
lspci
``` in terminal please.

---

### Post by lymphor on 2014-08-22
Hi Roger, hi ajgreeny, thank you both for your answers :)

I unplugged the cable and reboot but no **up/down arrows** in the top right of the **task bar** were displayed (I'm usity **GNOME** desktop, not UNITY).
I don't have a **wireless adapter** connected to my **desktop PC**, I use wireless only for the **laptop**.
My PC is connected through a wire that goes from the router to the **LAN** of the PC.

Here is the output of **lspci**:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Qualcomm Atheros Attansic L1 Gigabit Ethernet (rev b0)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
```

I hope you can help me further, thank you!

---

### Post by ajgreeny on 2014-08-22
I am confused about which computer that lspci output is from, and whether or not you can get a connection at all with your Ubuntu OS.

More clarification please and details of both machines.

---

### Post by lymphor on 2014-08-23
The lspci output is from the **desktop PC** (the one that is connected to the router trough LAN. It's also the one that has both Ubuntu 14.04 LTS and Windows 7 installed). My desktop PC gets a connection to internet on Windows 7 (connection was set up by a friend of mine) but does not on Ubuntu 14.04 LTS (because I don't know how to set it up).
As for the** laptop**: that one is fine, it uses a wireless connection and it has only Windows installed.
Hope this info helps :)

---

### Post by ajgreeny on 2014-08-23
Using a cable connection should usually connect to the web with no input from you, so I am surprised you are getting a problem with that Qualcomm Atheros Attansic L1 Gigabit Ethernet (rev b0) ethernet card.

Do a search for that card using [UbuntuSearch]("https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao") as I have found that it has happened before, but as I am about to leave the house I do not have a chance to do more than offer you my custom search engine that I have made  for ubuntu related queries.


Have a good look through that and see if it gives you any clues.

---

### Post by lymphor on 2014-08-31
Hi ajgreeny, and thank you for your help.

I have solved the problem by simply replacing the Network Manager with **Wicd Network Manager**. I have used the default settings for a wired connection and had no problem ever since!

Thank you once again for your support ;)

---

