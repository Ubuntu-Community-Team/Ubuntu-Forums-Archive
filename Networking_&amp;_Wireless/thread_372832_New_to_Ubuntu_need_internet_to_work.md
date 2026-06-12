---
title: "New to Ubuntu need internet to work"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by PsychoticSheep on 2007-02-28
Installed a couple of days ago. Overall I am ipressed and I am DESPERATE for the internet to work. I feel i could really get my teeth into linux but... Doesnt seem to pick up an internet connection. Can somebody please help! I have tried everything possible. Hopefully someone might spot something wrong in my settings. If i cant get the internet working its pointless really and bye bye linux :(

This is the iwconfig command

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"WILLIAMSNET"  Nickname:"WILLIAMSNET"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: B6:A5:BD:5F:47:85
          Bit Rate=11 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-59 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```


This is what i got from the lspci command 

```
matthew@matthew-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

As a noob i do not have much understanding of these outputs but i do have a network key I thought maybe it would show up in iwconfig?

---

### Post by haricharan on 2007-02-28
as far as i know the mode:Ad-Hoc means peer to peer connection it has to be mode:Managed... It shows managed in mine. Also try ifconfig command and see if a proper ip has been assigned to your computer.

---

### Post by wireddad on 2007-02-28
It looks like your wireless connection is not active.  Check to make sure your wireless card is installed properly, disable the NIC and able the wireless.
My connection is an ath0.

---

### Post by PsychoticSheep on 2007-02-28
I do not have a router it uses an ad-hoc connection. And yes an ip address on 168.192.0.1 is assigned which seems to be right. Easy wifi seems to find no problems either. Thanks for the help though. It did work once for like 5 mins. Then stopped for no apparent reason. :S I have disabled firewalls etc but still no joy.

---

### Post by PsychoticSheep on 2007-02-28
It looks like it is active. Wireless strength indicator goes to 100 and packets are occasionally sent back and forth. I will try the steps you suggested though. Thanks a lot for your time! Im really wanting to get this to work.

---

### Post by PsychoticSheep on 2007-02-28
Can nobody see anything wrong? Looks like im stuck with xp then... *sigh*

---

### Post by haricharan on 2007-02-28
the output of lspci shows the wireless card too in mine...but it doesnt show up on urs...reinstall ur wireless card modules and check...if you could post what wireless card u use.it wud be easy for others to help...

---

### Post by PsychoticSheep on 2007-02-28
Its a Dell wireless 1370 WLAN mini PC card

---

### Post by haricharan on 2007-02-28
this should sort out ur problem i guess
[http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")
referenced in this thread 
[http://www.ubuntuforums.org/showthread.php?t=315979]("http://www.ubuntuforums.org/showthread.php?t=315979")

---

### Post by PsychoticSheep on 2007-03-01
Thanks but that isnt the problem. Iv done that... And there is a connection - just no internet...   Ill prob reinstall ubuntu and start again..

---

