---
title: "Unrecognized wifi card [On ASUS P5Q3 Deluxe Wifi@n]"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by Gorion on 2008-09-11
Hi, 
Would like to know what to do when the command line :
lspci 
don't show the wifi card. (Which is on my Asus P5Q3 WIFI-AP@n deluxe motherboard)

I googled and found some threads where the card wasn't recognized but none of them where the card wasn't even recognized when typing : lspci.

Nothing more with iwconfig and ifconfig... As if I hadn't any wifi card... :
```
$ iwconfig

lo    no wireless extensions.


eth0  no wireless extensions.


eth1  no wireless extensions.


$ ifconfig

eth0  Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
      UP BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
      Interrupt:19


eth1  Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
      UP BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
      Interrupt:17 

lo    Link encap:Local Loopback  
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:1722 errors:0 dropped:0 overruns:0 frame:0
      TX packets:1722 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0 
      RX bytes:86100 (84.0 KB)  TX bytes:86100 (84.0 KB)

```
How can I get my wifi working ?

---

### Post by Gorion on 2008-09-12
The very strange thing is that my mobo has the 'Express Gate' technology, which is based on a linux OS, and that I get the wifi working on it...

I don't stop my searches.
If anyone could help...

---

### Post by glittalogik on 2008-09-19
Courtesy of [http://inatie.wordpress.com/2008/09/04/p5q3-deluxe/](http://inatie.wordpress.com/2008/09/04/p5q3-deluxe/) :

> Asus seems to have taken lots of effort to hide what kind of WiFi chip is in this motherboard  . A bit of a surprise: the thing is connected to USB. If you read this long after I posted this, it&#8217;s probably a good idea to check if you get an identical line (everything to the right of ID, the left part may vary) in the output of lsusb (in a terminal):
Bus 004 Device 002: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter

Actually&#8230; if you read this sometime far in the future, the driver should come included with the linux kernel, I guess.

The driver can be found here: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html), it&#8217;s the RT2870USB(RT2870/RT2770). I&#8217;m not sure what the RT2870WebUI in the same table cell is, not what you need apparently, so be sure to click the correct link.

Unpack the archive you downloaded (in the terminal: tar xjf thefile.tar.bz2) and enter the newly created directory.

Edit os/linux/config.mk and set both HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT to y .

Type make (in the terminal; be sure to be in the directory created while unpacking the archive)

&#8211; at this point, make sure you are root &#8211;

Copy  RT2870STA.dat to /etc/Wireless/RT2870STA/RT2870STA.dat (I think this is probably unnecessary, but whatever)

Copy os/linux/rt2870sta.ko to /lib/modules/currentlinuxkernelversion/kernel/net/wireless .

Edit /etc/modules and add a line containing rt2870sta .

Run depmod (in a terminal).

Restart the computer. You should now be able to use/configure the wireless network in the usual way.

---

### Post by berman56 on 2008-09-22
Gorion,

I wonder if you might be so kind as to share the details of your PC build and Ubuntu version.  Many of us with p5q3 motherboards have had no luck getting Ubuntu (any version including current 8.10 alpha 6) installed.  See thread:

[http://ubuntuforums.org/showthread.php?t=915165](http://ubuntuforums.org/showthread.php?t=915165)

Did you have any trouble getting Ubuntu installed?  Any tricks you might share?  Many thanks!

---

### Post by Azzir on 2009-02-20
Hi All :-)

I too have a P5Q3-Deluze motherboard and was having issues getting the motherboard until I found this page (MASSIVE thanks to glittalogik for pointing me in the right direction!)

Just something I thought I'd add... don't forget that when you update/upgrade your kernel, you'll need to re-do the steps that were listed in this part:

> Copy os/linux/rt2870sta.ko to /lib/modules/**currentlinuxkernelversion**/kernel/net/wireless

Once I copied that file over, all was well :)

---

