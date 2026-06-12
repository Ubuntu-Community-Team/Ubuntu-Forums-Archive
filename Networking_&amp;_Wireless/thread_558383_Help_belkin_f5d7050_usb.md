---
title: "Help belkin f5d7050 usb"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by Baconbitsforu on 2007-09-23
i am new to linux and have a belkin f5d7050 usb wifi but i can see the wireless network but it will not connect to it :confused:  HELP!!!

---

### Post by uputer on 2007-09-24
I have the same problem although I had a temporary connection and I'm not sure why it could not be maintained.   However, I haven't been able to get it back.

I am not sure who claims this device works out of the box but one person claimed that here.   It might have worked but I doubt it's ongoing or working properly.

*EDIT:  I now have reason to belive the chipset is zd1211.

Anyway, I will post if I find any more info or a solution (doubt that) but will be watching the thread in case anyone else knows how to get the device to work.  I won't be buying this particular one for another machine, though.   If I am to keep using Linux, I'd want wireless.   I'll welcome any devices that 'just work' or use minimal configuration.   Also, can anyone help setup any wireless usb adapter using the kde network tools?   I want the option of WEP or WPA.

EDIT #2:  OP, this web page appears to be required or may be helpful.   
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)))
This one is also useful:
[http://ubuntuforums.org/showthread.php?t=258578](http://ubuntuforums.org/showthread.php?t=258578)

I hope that helps. 

I guess I'll try it... crosses fingers...


Here are my steps of diagnosing the situation:
EEE 802.11b/g  ESSID:"*NAMENET*"  Nickname:"zd1211"  (NAMENET is the name you give in router settings)
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~$ dmesg | grep zd1211
[   15.820000] zd1211rw 2-3:1.0: firmware version 4725
[   15.892000] zd1211rw 2-3:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--N
[   15.892000] zd1211rw 2-3:1.0: eth1
[   15.892000] usbcore: registered new interface driver zd1211rw

KDE Control Module

Network Interfaces
Available Network Interfaces
Interface  IP Address Protocol State Comment
eth0 192.168.1.X (static) Manual  Enabled Ethernet Network Device  (was wired)
eth2 169.254.X.X            dhcp      Enabled Wireless Network Device   (current setup)

Configure Device eth2 &#8211; KDE Control Module
TCP/IP Address 
( ) Automatic     dhcp
( ) Manual   
IP address:
Netmask:
[x] Activate when the computer starts
Wireless settings
ESSID:   namenet
WEP key:
Key type:  ASCII
Advanced Settings

---

### Post by uputer on 2007-09-27
Bump or followup...

[https://help.ubuntu.com/community/Wi...zd1211b_driver](https://help.ubuntu.com/community/Wi...zd1211b_driver)

I found this:
[http://sourceforge.net/projects/zd1211/](http://sourceforge.net/projects/zd1211/)

[http://www.linuxwireless.org/en/users/Drivers/zd1211rw](http://www.linuxwireless.org/en/users/Drivers/zd1211rw)

[http://www.linuxwireless.org/en/user...1211rw/devices](http://www.linuxwireless.org/en/user...1211rw/devices)

[http://zd1211.wiki.sourceforge.net/](http://zd1211.wiki.sourceforge.net/)

[http://sourceforge.net/project/showf...roup_id=129083](http://sourceforge.net/project/showf...roup_id=129083)

With the info about the Zydas zd1211b taken into consideration, could anyone advise me a little on how to install this driver for my Belkin F5D7050 v. 4000 usb wireless adapter in 7.04 Feisty?  I know the tutorial is designed for Edgy but I thought Feisty might be a different situation.   

I'm using Kubuntu but the install should be very similar to Ubuntu.

I'm just confused on what needs to be done. I had the impression that the driver is pre-compiled into the kernel and that anything above .18 is already there and that I just have to activate the driver or 'turn it on?'

Or do I have to blacklist or build a module?   

Thanks in advance for any info and/or assistance.  I asked the author of the above wiki and am awaiting a response from anyone on the topic.   It would even be great if someone could suggest steps (explain the tar and .bz2 files for e.g.) on how to go about it.   

If I ever get this done, I will post as detailed steps as possible to help any other owners of this adapter or the chipset.  
__________________

---

### Post by defconoii on 2007-09-29
same issue, the belkin:
Bus 004 Device 003: ID 050d:705a Belkin Components 
never worked out of the box, and barely works with latest cvs of serialmonkey drivers, WPA enabled hangs pc, bugs reported....
Gutsy Beta Effected

---

### Post by paradoxni on 2007-09-29
im trying to get a belkin usb F5D7050 v4.0 working too, tried feisty and now gutsy, problem is the device isnt even appearing in the lsusb list, i think its broken!? I havent even gotten to the driver stage yet as the system just doesnt seem to even see the device plugged in.

There are various posts and guides about installing various drivers, but they all require "lsusb" to get the device ID from the list, but its not showing up in there.

*EDIT*

Just checked dmesg after plugging it in and im getting:

```
[45901.718363] hub 7-6:1.0: Cannot enable port 6.  Maybe the USB cable is bad?

```

So perhaps the device is broken afterall

---

### Post by uputer on 2007-09-29
> **defconoii said:**
> same issue, the belkin:
Bus 004 Device 003: ID 050d:705a Belkin Components 
never worked out of the box, and barely works with latest cvs of serialmonkey drivers, WPA enabled hangs pc, bugs reported....
Gutsy Beta Effected
I believe that's a RT73 device.   Did you use instructions concentrating on RT73?

[http://ubuntuforums.org/archive/index.php/t-502526.html](http://ubuntuforums.org/archive/index.php/t-502526.html)

HOWTO: RT73 (RT71) serialmonkey drivers

My USB adapter is the Zydas zd1211.   The problem with the Belkin is recent ones have 1 of 3 chipsets depending on the version but v.4000 have either Ralink or Zydas.

---

### Post by defconoii on 2007-10-10
yes I have done all instructions regarding the belkin usb dongle:
Bus 001 Device 003: ID 050d:705a Belkin Components
rt73 belkin 7050 ver 3002
gutsy never worked out of the box with this, and serialmonkey wpa enabled causes complete system lockup, wep works with serialmonkey drivers, just not wpa like it did on feisty

---

### Post by olbill on 2007-10-14
I have discovered the reason my Belkin 7050 version 2.00 wireless card does not work in Feisty or Gutsy. It reports as a version 1.00 and loads the rt73usb driver as default. I have used ndiswrapper to load the XP driver rt2500usb from the mfg web site. Blacklist rt73usb and the wireless works great. You might try the following link to get the current winxp drivers for your card.

[http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=221](http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=221)

Good luck to all.


desktop:~$ sudo lsusb
Password:
Bus 001 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 001 Device 001: ID 0000:0000

desktop:~$ ndiswrapper -l
drivername : invalid driver!
rt2500usb : driver installed
device (050D:7050) present (alternate driver: rt73usb)
__________________

---

