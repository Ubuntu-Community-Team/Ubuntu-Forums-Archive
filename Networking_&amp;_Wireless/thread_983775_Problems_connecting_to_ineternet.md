---
title: "Problems connecting to ineternet"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Shishant on 2008-11-16
I have problems connecting to internet via ubuntu, i have to use web dialer to conect to internet in windows configuration is done in network connections (tcp/ip>properties) there i input ip address and dns server after these configurations i connect to internet using web dialer but in ubuntu my web dialer page doesnt open i guess there are problems in my settings.

this is the screen shot of where i configure in windows.

[IMG]http://i35.tinypic.com/33117ko.jpg[/IMG]

just in case:

[https://loginbom.tataindicombroadband.in:8443/](https://loginbom.tataindicombroadband.in:8443/)

this is my web dialer link.


Please help me configuring my ubuntu settings would appreciate detailed procedure in configuring and sorry for my bad english.

The setting made by me in ubuntu:

[IMG]http://i38.tinypic.com/23v1apv.png[/IMG]

[IMG]http://i35.tinypic.com/1zd9jed.png[/IMG]

[IMG]http://i34.tinypic.com/f3gspx.png[/IMG]
I even tried to ping from network tools but i wasnt getting any response

Thanks.

---

### Post by Shishant on 2008-11-16
Please help me i am sick using windows and i liked ubuntu very much.
[COLOR="Red"][B]
Person helping me will get a copy of Codeweaver Linux Pro ([http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/))[/B][/COLOR]

---

### Post by markg48 on 2008-11-16
are you using dialup?

if your using dialup u need drivers

if you your using wireless u can install madwifi or ath5k and or ndiswrapper if u need help choosing 
or arnt very confident installing from source ill upload  the deb package for u

---

### Post by Shishant on 2008-11-16
I am using broadband connection and i am connected through lan.

---

### Post by markg48 on 2008-11-16
thats odd then my broadband lan connects to the net automatickly

---

### Post by markg48 on 2008-11-16
try this [http://ubuntuforums.org/showthread.php?t=206185](http://ubuntuforums.org/showthread.php?t=206185)

---

### Post by Shishant on 2008-11-16
shishant@shishant-desktop:~$ sudo modprobe 8139too
sudo: unable to resolve host shishant-desktop
shishant@shishant-desktop:~$ sudo modprobe 8139cp
sudo: unable to resolve host shishant-desktop
shishant@shishant-desktop:~$ sudo ifconfig -a
sudo: unable to resolve host shishant-desktop
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:64:28:8c  
          inet addr:10.xx.xxx.xx(changed to xx)  Bcast:10.11.239.255  Mask:255.255.254.0
          inet6 addr: fe80::21b:b9ff:fe64:288c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229488 (224.1 KB)  TX bytes:229488 (224.1 KB)

shishant@shishant-desktop:~$ dmesg|tail
[  841.344687] eth0:  Tx descriptor 3 is 0008203c.
[  841.344712] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  850.338729] NETDEV WATCHDOG: eth0: transmit timed out
[  853.337107] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  853.337115] eth0: Tx queue start entry 4  dirty entry 0.
[  853.337122] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  853.337127] eth0:  Tx descriptor 1 is 0008203c.
[  853.337132] eth0:  Tx descriptor 2 is 0008203c.
[  853.337136] eth0:  Tx descriptor 3 is 0008203c.
[  853.337162] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1


this is what i got i have changed above ip address to xx just for safety, is there anything wrong? i am using linux for first time in my life

---

### Post by markg48 on 2008-11-16
i dont no its meant to work

---

### Post by markg48 on 2008-11-16
go to application accessories then terminal and type each of these seperate

sudo rmmod 8139too
sudo modprobe 8139cp
sudo ifconfig eth0 up

If you don't get any errors, wait a few seconds and see if you can connect to the Internet. If you do get errors, try this:

sudo rmmod 8139cp
sudo modprobe 8139too
sudo ifconfig eth0 up

if this doesnt work then i dont no what will

---

### Post by markg48 on 2008-11-16
your using ubuntu hardy heron  download interpid  and try again if that doesnt work to

also if your box is already  connected to the internet before your turn on your computer u generaly dont need to configure a connection

---

### Post by Harry_Iyer on 2008-12-11
[FONT="Tahoma"]Hi Shishant!

Thank you for posting this problem so nicely with screen shots etc. I am facing the exact same problem with the _Tata Indicom Web Dialer_ here in Bangalore.

I installed Ubuntu:Intrepid Ibex today (dual booted with XP SP3,_[COLOR="Red"]using Linux for the first time[/COLOR]_) and am able to use the internet connection from windows XP; but not from Ubuntu.

I think it has got something to do with _ports_ & how Tata Indicom (ISP) handles them. Tried calling the customer care and they say it is possible to use their connection multi booting any operating system(s), whether static IP(postpaid) or dynamic(prepaid).

Will try out the suggestions given here and report back . . .

> **Shishant said:**
> 

i have to use web dialer to conect to internet in windows configuration is done in network connections (tcp/ip>properties) there i input ip address and dns server after these configurations i connect to internet using web dialer but in ubuntu my web dialer page doesnt open



Be very sure to log off from your TI WEB DIALER page when using it in windows. Most of us just close the tab once we are connected. I have tried and found that if you don't duly log off the connection, you wont be able to make the same connection from ubuntu.

By the way, power cycling my modem solved the problem for me.

You might also want to do steps in posts #2 & #3 given here : -

[http://ubuntuforums.org/showthread.php?t=401247]("http://ubuntuforums.org/showthread.php?t=401247")

Or, follow the official documentation (much better)

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")

-[/FONT]

---

### Post by Harry_Iyer on 2008-12-11
> **markg48 said:**
> try this [http://ubuntuforums.org/showthread.php?t=206185](http://ubuntuforums.org/showthread.php?t=206185)

[FONT="Tahoma"]Not a driver issue (as the creator of the thread observed later) since the connection works in any live environment. Shishant, you might want to check that out[/FONT]

---

