---
title: "Belkin + Ubuntu 6.10?"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by Sleep on 2007-01-15
I have a bit of an issue... I recently installed Ubuntu 6.10 to my former Windows Machine, when I did that I chose to delete everything that was on the HD prior because I backed everything up to a old iPod :P.

The install went very smoothly and whatnot. When I logged in for the first time and tried to configure the Wireless Card that was working just a few hours ago prior to Ubuntu, it Activates I'm pretty sure it does, I put in my network name and pass but when I load FF it doesn't work.

If anyone can help me out that would be very much appreciated. :)

-Sleep

---

### Post by floke on 2007-01-15
Make sure you have enabled wireless (ie checked the box)
Make sure the name is entered correctly (along with the encryption method - eg Hex - for the password)
Make sure you have selected the right option for connection settings  - for me the problem was that I was trying to enter everything that I needed to in Windows - when all I needed to do was select automatic DHCP and that was it - no IP address, no submask etc. - so try it without the details - i.e. select automatic and leave the boxes below empty

Good luck

---

### Post by floke on 2007-01-15
If this doesn't work it will help if you post the results of your 'iwconfig' and 'lspci' settings (enter the commands into a terminal and cut/copy and paste the outcome).

---

### Post by Sleep on 2007-01-15
Alright, I'll check on that. Thanks.

---

### Post by Sleep on 2007-01-15
lspci
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by floke on 2007-01-15
You could try getting wifi-radar (enter 'sudo apt-get install wifi-radar' into a terminal and use this to scan and connect). Also, you should try it with your encryption turned off, just until you manage to connect.

Good luck

---

### Post by floke on 2007-01-15
Also try 'sudo apt-get install network-manager' (I think this is a better one)

---

### Post by Sleep on 2007-01-15
Alrighty, one sec.

---

### Post by floke on 2007-01-15
Ooops - should have been network-manager-gnome

Sorry!

---

