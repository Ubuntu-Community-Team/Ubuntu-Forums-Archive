---
title: "Newbie Wireless Question"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by swampkat on 2009-04-09
Hi:

I am trying to used a new install of Jaunty Jackalope, to pick up the local libraries wireless connection, on an hp laptop. I have never set something like this up before.  After playing around with it, I finally got it to connect on "ad-hock" and shared to other computers -- however I can't get to the Internet.  Because I am not using Windows or a Mac nobody there can help me, so I am hoping someone here can.  Thanks in advance. 	](*,)

---

### Post by amitabhishek on 2009-04-09
Since I work on Hardy LTS am not sure what "connect on "ad-hock"" means. BTW Which HP laptop is this? Can you type lspci at terminal and paste the output here?

---

### Post by HereInOz on 2009-04-09
Ad-hock normally means a wireless connection to another computer, rather than to a wireless access point.  That is probably why you are unable to connect to the Internet.

If the library runs a wireless service with no password, as they often do, it should be a matter of clicking on the Network Manager icon, selecting the particular wireless network SSID, and it will connect.  

If it needs a password, then you need to find out what type of security they are using (WEP, WPA-PSK, etc) and perhaps post back here with the information and any errors you get and describe what happens when you are unable to connect.

---

### Post by kiridude on 2009-04-09
If you're a noob with Ubuntu, I would suggest installing 8.10 as Jackalope is still in testing.

---

### Post by superprash2003 on 2009-04-09
how were you connecting to the internet when on windows?

---

### Post by bbala2020 on 2009-05-19
Output of lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

What is the value for SSID and BSSID should i enter to create a wireless connection??

---

