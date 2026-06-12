---
title: "cant surf the net"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by james.a.t.g on 2007-01-15
(just installed unbuntu)right so i can't surf the net on my wireless boradband conection

what i do ?

---

### Post by teaker1s on 2007-01-15
terminal
[COLOR="Red"]lspci
lsusb[/COLOR]
[COLOR="Red"]iwconfig[/COLOR] see if the interface is running
find out what chipset you have then you will need to find out what driver is required

---

### Post by james.a.t.g on 2007-01-15
> **teaker1s said:**
> terminal
[COLOR="Red"]lspci
lsusb[/COLOR]
[COLOR="Red"]iwconfig[/COLOR] see if **"the interface is running"**
find out what chipset you have then you will need to find out what driver is required

what do u meen by that ?

---

### Post by teaker1s on 2007-01-15
on desktop panel click 
applications
accessories
terminal

this brings up a terminal box to enter the commands in red it will print a load of text which you need to copy and paste here

---

### Post by james.a.t.g on 2007-01-15
how can i copy and paste the code, when I have to reboot my pc to change OS?

---

### Post by teaker1s on 2007-01-15
your making this really difficult-this is not paid support and I can only help if you help yourself

how am I to know your ubuntu is duel boot without an ethernet cable and router for internet access?


print it 
or
pen/pencil paper

---

### Post by james.a.t.g on 2007-01-16
is this what u wanted ?

james@james-desktop:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)0000:00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
0000:00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
0000:00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
0000:00:0f.0 Communication controller: ESS Technology ES2898 Modem (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
james@james-desktop:~$ lsub
bash: lsub: command not found
james@james-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

:confused: :confused: :confused:

---

### Post by teaker1s on 2007-01-16
> **james.a.t.g said:**
> is this what u wanted ?

james@james-desktop:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)0000:00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
[COLOR="RoyalBlue"]0000:00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/COLOR]
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
0000:00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
0000:00:0f.0 Communication controller: ESS Technology ES2898 Modem (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
james@james-desktop:~$ lsub
bash: lsub: command not found
james@james-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

:confused: :confused: :confused:
first can you in any way shape of form connect your ubuntu box to an ethernet connection for internet access? otherwise it will be a pain and you will need to burn cd's for software?

if yes we can see that you have a broadcom 4306 wireless chip, I've highlighted in blue.
Please read the link through before starting and then follow it to the letter only possible issue is driver file which you may need to extract from manufacturers driver cd or download from their site and you should have  
wireless-if you have any problems please post again ;) 

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by james.a.t.g on 2007-01-21
would i be able to use a laptop conected to the net then a internet conection lead goinon into back of pc ?

---

### Post by teaker1s on 2007-01-21
possibly but I don't know how to do this

---

### Post by james.a.t.g on 2007-01-27
ok so i cant connect to the net any other way, what can i try and do now pleas ?:D :D :D

---

