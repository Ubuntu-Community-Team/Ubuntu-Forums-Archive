---
title: "Dell 1450 USB Adapter and ndiswrapper problems"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by mtbiker on 2006-11-08
Hello,
  I've got ndiswrapper 1.8 installed.  All seems well, but I can't get my dell 1450 to show up in the network setting area to configure it. 

I've also tried setting it up per the install documents on sourceforge with no luck.

I don't really know what else to put on here, because I'm not getting any errors, the driver is loaded, it just doesn't work.  The adapter works fine in windows.  No problems at all on the same ap and computer, I'm duel booting with windows xp.  So I know the adapter works.

I've followed the like 3 tutorials on getting it working, still no luck. 

Any help you could lend would be greatly appreciated.  I really don't want to only use windows.

Please keep in mind I'm a complete newbie to linux.

Thanks
Mark

---

### Post by mtbiker on 2006-11-09
Ok, let me clarify some stuff here.
Going from the install documentation for ndiswrapper ( [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) ):

I've loaded the new ndiswrapper v1.28.  It installed without incident. 

I then installed the windows drivers from the cd as recommended from the list ( [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D)) and when I do a  ndiswrapper -l I get this:

     installed drivers:
    dellnic         driver installed, hardware (413C:8104) present

So I'm thinking I'm in good shape at this point, the drivers are loaded as far as I can tell.  No errors yet.

I type "depmod -a", and get no errors so I type "modprobe ndiswrapper" with no errors, then "dmesg" per the installation instructions and I see "[ 17179588.412000] ndiswrapper version 1.28 loaded (preempt=no,smp=yes)".

Problem at this point is, according to the install documentation, I should also see "ndiswrapper: driver ''driver1'' added" in the system log.  I don't see that anywhere in the log.  I tried "dmesg | grep ndiswrapper" and only got 2 lines: 

"[17179588.412000] ndiswrapper version 1.28 loaded (preempt=no,smp=yes)
[17179588.448000] usbcore: registered new driver ndiswrapper"

Remember I'm new to linux, so I may not have done the dmesg grep correctly, so I scanned thru the file and still don't see that line. 

So, i check the /etc/ndiswrapper directory and I see a dellnic directory with 4 files in it.  dellnic.inf, prisma02.sys, 413c:8102.F.conf and 413c:8104.F.conf.

Next thing the install doc says is I should see "wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx". 

I don't see that either.  At this point it looks like the driver isn't loading, but I'm clueless, so please let me know if I'm missing something. I don't know if it helps if I continue with the install directions, but just in case I did continue, and here's what I ran into.

So I run through the configuration of the card real quick, and here's what I get:

mbrown@mbrown-desktop:~$ sudo iwconfig eth2 mode Managed
mbrown@mbrown-desktop:~$ sudo iwconfig eth2 essid home123
mbrown@mbrown-desktop :~$ sudo ifconfig eth2 up
mbrown@mbrown-desktop:~$ sudo iwlist eth2 scan
eth2      No scan results
mbrown@mbrown-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:73:2F:B5 
          inet addr: 192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe73:2fb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:304122 (296.9 KiB)  TX bytes:199560 (194.8 KiB)
          Base address:0xcf40 Memory:fe8e0000-fe900000

eth2      Link encap:Ethernet  HWaddr 00:14:A5:3D:05:8C 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 ( 100.0 b)

mbrown@mbrown-desktop:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11b  ESSID:"" 
          Mode:Managed  Channel=1  Access Point: Invalid  
          Sensitivity=0/200 
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


Now I'm stuck.  Don't know where to go for here.

Thanks in advance for any light you can shed on this.

Mark

---

### Post by Mischief on 2007-07-01
I've done the exact same steps with dellnic.inf and prism02.sys in ndiswrapper and come up with nothing. This worked back in version 6 out of the box but with 7.04 I cannot get "413c:8102" to work either.

Have you made any progress since this was posted 6 months ago?

Thanks!

---

