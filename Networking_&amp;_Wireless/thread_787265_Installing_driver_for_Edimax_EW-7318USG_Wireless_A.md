---
title: "Installing driver for Edimax EW-7318USG Wireless Adapter"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Lourie2 on 2008-05-08
Having given up hope on the Belkin adapter (F5D7050 v5000UK) which I impossibly could not get to work in Hardy (It worked in Gutsy!), I got myself an Edimax EW-7318USG Wireless Adapter.  Trying to install the driver with "HOWTO: RT73 (RT71) serialmonkey drivers
Posted by alex - 2007/10/08 04:57", I have reached a point where my hardware is not detected.  Any help on this? Here is where I got:
```
name@name-IBM:~$ cd /usr/src
name@name-IBM:/usr/src$ ls -alh rt73.ko
ls: cannot access rt73.ko: No such file or directory
name@name-IBM:/usr/src$ ls -d rt73*
rt73-cvs-2008050815  rt73-cvs-daily.tar.gz
name@name-IBM:/usr/src$ cd /usr/src/rt73-cvs-2008050815/Module
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo make
[sudo] password for name: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
*** Module rt73.ko built successfully
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ ls -alh rt73.ko
-rw-r--r-- 1 root root 246K 2008-05-08 22:33 rt73.ko
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo make install
*** Install module in /lib/modules/2.6.24-16-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  INSTALL /usr/src/rt73-cvs-2008050815/Module/rt73.ko
  DEPMOD  2.6.24-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check old config ...
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -r rt73usb
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -r rt2570
FATAL: Module rt2570 not found.
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -r rt2500usb
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -r rt2x00lib
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ gksu gedit /etc/modprobe.d/blacklist
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -v rt73
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:25:67:08:b7  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe67:8b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13739931 (13.1 MB)  TX bytes:712383 (695.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39300 (38.3 KB)  TX bytes:39300 (38.3 KB)

name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$
```

---

### Post by stansford on 2008-05-09
> **Lourie2 said:**
> Having given up hope on the Belkin adapter (F5D7050 v5000UK) which I impossibly could not get to work in Hardy (It worked in Gutsy!), I got myself an Edimax EW-7318USG Wireless Adapter.  Trying to install the driver with "HOWTO: RT73 (RT71) serialmonkey drivers
Posted by alex - 2007/10/08 04:57", I have reached a point where my hardware is not detected.  Any help on this? Here is where I got:
```
name@name-IBM:~$ cd /usr/src
name@name-IBM:/usr/src$ ls -alh rt73.ko
ls: cannot access rt73.ko: No such file or directory
name@name-IBM:/usr/src$ ls -d rt73*
rt73-cvs-2008050815  rt73-cvs-daily.tar.gz
name@name-IBM:/usr/src$ cd /usr/src/rt73-cvs-2008050815/Module
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo make
[sudo] password for name: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
*** Module rt73.ko built successfully
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ ls -alh rt73.ko
-rw-r--r-- 1 root root 246K 2008-05-08 22:33 rt73.ko
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo make install
*** Install module in /lib/modules/2.6.24-16-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  INSTALL /usr/src/rt73-cvs-2008050815/Module/rt73.ko
  DEPMOD  2.6.24-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check old config ...
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -r rt73usb
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -r rt2570
FATAL: Module rt2570 not found.
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -r rt2500usb
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -r rt2x00lib
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ gksu gedit /etc/modprobe.d/blacklist
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ sudo modprobe -v rt73
name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:25:67:08:b7  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe67:8b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13739931 (13.1 MB)  TX bytes:712383 (695.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39300 (38.3 KB)  TX bytes:39300 (38.3 KB)

name@name-IBM:/usr/src/rt73-cvs-2008050815/Module$
```


I think that you might be doing some of these steps in the wrong order. eg from the instructions I was given you need to blacklist first. Here are the instructions I use:

1.	sudo rmmod rt73usb (remove old drivers)
2.	sudo gedit /etc/modprobe.d/blacklist and add these lines to the end of the file:
blacklist rt73usb
blacklist rt2570
blacklist rt2x00lib
3.	sudo apt-get install build-essential
4.	sudo apt-get install linux-headers-`uname –r`
5.	get the latest version of the driver source from the serialmonkey site. The name is rt73-cvs-daily.tar.gz. I saved it in my user dir:
6.	sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) -O ~/rt73-cvs-daily.tar.gz
7.	sudo tar -zxvf rt73-cvs-daily.tar.gz
8.	cd ~/rt73*/Module
9.	sudo make
10.	if the file produced is 2Mb in size there is a problem as it should be about 250Kb. To fix this, use the "strip" command:
strip –S rt73.ko 
11.	sudo make install
12.	sudo modprobe rt73
13.	as sudo, edit /etc/modules – add the text rt73 at the end
14.	as sudo, create text file called rt73 in /etc/modprobe.d
15.	put the text “alias wlan0 rt73” in this file
16.	remove /etc/modprobe.conf as it’s no longer needed (back it up first – but note I didn’t have one)
17.	add the following to /etc/network/interfaces file. You might need to customise this to suit your particular situation (eg if you don't use WPA encryption):

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid yourSSID
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set Channel=11
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="yourkey"
pre-up ifconfig wlan0 up

18.	reboot


I hope this helps. I've got to say that I'm having trouble myself with this in Hardy. I can follow all the above steps and get no errors, but I still can't connect to my router. I get no DHCPOFFERS and I'm not sure why, but see how far you get anyway.

---

### Post by stansford on 2008-05-09
see the following thread for much better info:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+hardy](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+hardy)

---

### Post by Lourie2 on 2008-05-09
> **stansford said:**
> see the following thread for much better info:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+hardy](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+hardy)
Thanks for this, I'll give it a try tonight.  Just need to know, do I start from Step 1, or is there something I need to do beforehand, perhaps to undo wrongs I have done sofar?  I'm a newbie, so please excuse my ignorance.

---

### Post by Lourie2 on 2008-05-09
Thanks to the Forum and stansford... it works!!!

---

### Post by stansford on 2008-05-11
> **Lourie2 said:**
> Thanks to the Forum and stansford... it works!!!

Lourie2 - no problem, glad you got it working. I've got a few of these edimax cards (pci, usb, pcmcia etc) and they do seem to work ok once you get the right drivers loaded...but it would be nice if they were supported out of the box.....oh well, maybe in intrepid ibex eh???....(well I can hope!)

---

