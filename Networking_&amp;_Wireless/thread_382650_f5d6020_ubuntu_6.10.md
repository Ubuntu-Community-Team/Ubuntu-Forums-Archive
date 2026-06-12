---
title: "f5d6020 ubuntu 6.10"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by hashwood on 2007-03-12
I am having some trouble with installing the Belkin f5d6020 (don't know what version)
FCC ID: K7SF5D6020
P81116-4
146000013200E R02 MLY

I'm trying to install it on a Thinkpad 600E. I am new to linux, and this is the first time I have real problems (many hours invested and nothing)
So, the card is detected, I can see it in Networking but the status there is Disconnected. The signal strenght is 94%. The card can see the router mac, and the router can see the card :)
I tried first with WEP- nothing, I tried without security still nothing. 
I am doomed :confused: 
 
ifconfig:

Code:
eth1      Link encap:Ethernet  HWaddr 00:30:BD:60:99:E2  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x180 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9877 (9.6 KiB)  TX bytes:9877 (9.6 KiB)

iwconfig:

Code:
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"asus"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:D4:24:F5:BB   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=76/92  Signal level=-33 dBm  Noise level=-149 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


/etc/network/interfaces

Code:
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
gateway 192.168.0.254


iface eth1 inet static
wireless-essid asus
address 192.168.0.17
netmask 255.255.255.0
gateway 192.168.0.254

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0


auto eth1



Thanks

---

### Post by chili555 on 2007-03-12
May we please see sudo iwlist eth1 scan? And you are not doomed...yet.

---

### Post by hashwood on 2007-03-12
eth1     Failed to read scan data : Resource temporarily unavailable

---

### Post by chili555 on 2007-03-12
I don't know why I didn't notice this previously and I'm sorry it therefor took another round of posts to get this moving forward. In /etc/network/interfaces, the gateway is surely 192.168.0.1, not .254. Please sudo gedit /etc/network/interfaces and change it.

What I was trying to get at with 'scan' was to determine that the ESSID is exactly asus. You will not connect if, in your router, it's actually Asus or ASUS.

Please then restart networking: sudo /etc/init.d/networking restart. Then let's ping -c3 192.168.0.1. Let us know the result.

---

### Post by hashwood on 2007-03-12
but my gateway, the router is 192.168.0.254, why change it to 1 ?
one way or another in /etc/network/interfaces the gateway is .254 as in my first post

and the Wireless Network Name (SSID) is: asus  (no capital letters)

---

### Post by chili555 on 2007-03-12
Don't change it. It has been a long time since I made a mistake like that. I will be writing on the whiteboard this evening. "Chili must not assume." 1000 times, please.

Sorry.

This: ```
eth1 Failed to read scan data : Resource temporarily unavailable
``` is mysterious. I am looking for an answer. We will get it.

What does lspci -v | grep Network tell us? Also, could I see lsmod | grep prism2?

The FCC ID: K7SF5D6020 suggests it's a version 1 card which is Prism based. This is ordinarily very easy to get configured but sometimes too many modules try to load.

> eth1 IEEE 802.11b ESSID:"asus" Nickname:"Prism I"

---

### Post by hashwood on 2007-03-12
lspci -v | grep Network - nothing
I did lspci -v and I can't see any network interface...
lsmod | grep prism2 also nothing

Thanks for your help, really it's greatelly appreciated

---

### Post by chili555 on 2007-03-12
Hash-

Every 100 lines on the whiteboard, I stop to Google your problem. I found this: [http://www.mueller.ch.vu/misc/tp600e_en.html](http://www.mueller.ch.vu/misc/tp600e_en.html) and was especially interested in this: > It seems that to get wlan (wireless) cards to see the router you need to totally disable acpi:```
acpi=off pci=noacpi
```

When you restart the computer, you will have the option to press the ESC key to edit the boot menu. Highlight the top line and press e (for edit.) You will see several lines. Highlight this one and press e: ```
/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
``` Move your cursor into the line and change it to: ```
/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro **acpi=off pci=noacpi** quiet splash
``` Press b (for boot) and see if your card shows up under lspci -v and scans.

Back to the whiteboard.

---

### Post by hashwood on 2007-03-12
Thanks again. I did that but with no luck. 
"It seems that to get wlan (wireless) cards to see the router you need to totally disable acpi"
I think that my problem is elsewhere since the card already sees the router:
iwconfig:

Mode:Managed Frequency:2.437 GHz Access Point: 00:134:24:F5:BB

Still nothing with  lspci  and lsmod

---

### Post by tamirtoad on 2007-08-05
Hey hashwood,

I've also got the same card and did a bit of googling: if you or anyone else that stumbles upon this thread sees this, then the installation instructions are at the following website.

[http://www.linuxquestions.org/hcl/showproduct.php?product=1384&cat=128](http://www.linuxquestions.org/hcl/showproduct.php?product=1384&cat=128)

According to a comment at the bottom, it works under ubuntu.

Hope this helps :)

EDIT: Forget I said that. Under feisty fawn, the device is automatically recognized. Just click on the network connections icon at the top right of your screen and choose your preferred wireless network. I'm not sure, but the fact that i had left the card in during install might have helped matters. FOR THE RECORD: winblows needs a driver that comes on a cd in order to use this card, and it works out of the box for linux!

---

