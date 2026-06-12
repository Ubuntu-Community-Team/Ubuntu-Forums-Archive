---
title: "Configuring Belkin's Wireless Pre-N Notebook Network Card  Model No.F5D8010"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Jadey on 2006-09-16
Hi,

I am trying to configure the Belkin's Wireless Pre-N Notebook Network Card  Model No.F5D8010 but I haven't been able to find any documentation in Google, anyone knows if there is a driver or proggram to configure it in Ubuntu?:confused:

---

### Post by dbeckler on 2006-09-19
I am using Belkin pre-n notebook card (same as yours I think) with the pci slot adapter.  You should be able to use the same drivers that everyone else are using for there pre-n Belkin cards, which are the netgear rangemax drivers

[http://http://www.netgear.com/Products/Adapters.aspx?for=All]("http://http://www.netgear.com/Products/Adapters.aspx?for=All")

Not sure exactly which driver I am using as I have deleted all non essential parts of the driver file.  After you get the driver you should be able to get it working with ndiswrapper

PS Keep the driver somewhere safe since you will be needing it after some kernel updates.

---

### Post by Jadey on 2006-09-21
Thanks dbeckler,

I have already installed the correspondant Netgear Driver wich i found in [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B) 

Card: Belkin F5D8010

    * Chipset: Airgo networks Pre-N
    * pciid: 17CB:0001
    * Driver: Driver for Netgear WPNT511 [38], version 06/30/2005, 1.5.0.147. Tested with snapshot of 2006-02-02 with WPA2-PSK 

I've installed the driver downloaded from this site following the instruction from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The network card is well recognized but it seems to have problems dealing wit DHCP I even tried  wpa_supplicant but I am not able to initialize it.

Could you please tell me how you made it to work? How did you install it?

Thanks

---

### Post by Danni on 2006-09-21
Hey there :)

I got this to work by compiling the newest version of ndiswrapper, using the instructions found at the bottom of this page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

That solved the DHCP problem for me. Hope this helps :)

---

### Post by stanman on 2006-09-23
I have also a F5D8010, after installing de drivers that is on the CD from belkin, mij wlan led starts blinkins, wlassistant also detects my AP, but i can't get any connection, looks like there is a problem using a wep key.

Anyone that has solved this problem??

THX

---

### Post by Danni on 2006-09-23
I don't think it's the wep key causing the problem, and you should use the drivers from the Netgear website, not the ones on the Belkin cd. Also, did you install the ubuntu ndiswrapper or compile the new version? If you used the version with ubuntu it isn't going to work.

I wrote a how to for getting it working, though you'll have to enter the wep key yourself (but using wlassistant will work there).

[http://www.ubuntuforums.org/showthread.php?t=262465](http://www.ubuntuforums.org/showthread.php?t=262465)

---

### Post by stanman on 2006-09-24
> **Danni said:**
> I don't think it's the wep key causing the problem, and you should use the drivers from the Netgear website, not the ones on the Belkin cd. Also, did you install the ubuntu ndiswrapper or compile the new version? If you used the version with ubuntu it isn't going to work.

I wrote a how to for getting it working, though you'll have to enter the wep key yourself (but using wlassistant will work there).

[http://www.ubuntuforums.org/showthread.php?t=262465](http://www.ubuntuforums.org/showthread.php?t=262465)

Whani install de NETANI.inf you suggest, i get invalid driver

---

### Post by stanman on 2006-09-24
Update Driver ok hardware present.

Still noting

after iwconfig

Auto  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
stany@Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:6E:D1:4A
          inet addr:192.168.100.56  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe6e:d14a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:686392 (670.3 KiB)  TX bytes:153047 (149.4 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:46306 (45.2 KiB)  TX bytes:46306 (45.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:29:19:A8
          inet addr:192.168.100.34  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:24000000-24080000

stany@Ubuntu:~$

Any suggestions

TY

---

### Post by stanman on 2006-09-24
I just don't get it, i am so close but still no connection

wlan0     Scan completed :
          Cell 01 - Address: 00:11:95:C2:8D:8B
                    ESSID:"bokenani"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:47/154  Noise level:0/154
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

:confused: What else to try

ty  for helping me out

---

### Post by Danni on 2006-09-24
Could you type ndiswrapper -v into a terminal for me, and post the results?

---

### Post by stanman on 2006-09-25
> **Danni said:**
> Could you type ndiswrapper -v into a terminal for me, and post the results?

It's working :D 

Ty Ty Ty for your help

stany@Ubuntu:~$ ndiswrapper -v
utils version: 1.8
driver version:        1.23
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0


Greetz

---

### Post by Danni on 2006-09-25
I'm glad it's working for you :)

---

### Post by lister171254 on 2007-01-03
Do any of you experience performance problems with this card?

My router is on the second floor of my house and after installing the card, I got everything working, but when I move the PC into my garage (about 20m/60ft) away, the signal degrades to the extent that it becomes unusable (ie. even getting to load a web page takes minutes.

Thanks,

Leo

---

