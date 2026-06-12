---
title: "Need some help with this network hardware!"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by serverCrazy on 2008-05-31
hi all, 

i want to setup a ubuntu server which will serve basic web applications. However, my motherboard has a small problem with the keyboard on the boot process. So, what i did was, i took the HDD out of the machine, put in another PC and installed ubuntu server. However, when i plug it back to the server machine, the network was not working, i said that it was not matching with a pid file on /var/run/, however i deleted that file and the problem is still on.

So, i would like to know if someone, knows how to configure the current network card in order to ubuntu work properly. Basically is a network card swap problem.

---

### Post by supremedalek on 2008-05-31
If you type ifconfig, as in (output from my laptop)

```
raub@monaco:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0e:9b:48:39:5d  
          inet addr:192.168.1.125  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe48:395d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4703795 (4.4 MB)  TX bytes:724333 (707.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:0d:56:e0:85:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73500 (71.7 KB)  TX bytes:73500 (71.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0E-9B-48-39-5D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46958 errors:0 dropped:0 overruns:0 frame:3062
          TX packets:5383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:8121355 (7.7 MB)  TX bytes:851482 (831.5 KB)
          Interrupt:5 

raub@monaco:~$ 

```

what does it give back? All I want to see is if your machine is seeing the card.

---

### Post by serverCrazy on 2008-06-01
no, my machine is just giving the lo connection which is a loopback. eth0 is not working. i tried ifup eth0 but giving a error: NO FLAG, NO SUCH DEVICE.

also tried the dpkg-reconfigure networking, but says that networking is not installed, so, no idea how i can fix that!!

---

### Post by serverCrazy on 2008-06-01
ok, i have fixed my self!!!!

1st-) open the file /etc/udev/rules.d/70-persistent-net.rules
2nd-) remove the lines:
        #PCI device xxxxxxxxxxx (module)
        SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="xxxxxxx", NAME="eth0"

and save the file.
3-) stop udev engine: sudo /etc/init.d/udev stop
4-) start udev engine: sudo /etx/init.s/udev start
5-) open the file /etc/udev/rules.d/70-persistent-net.rules once again
6-) have a look ok the device module will be on the parenteses #PCI device xxxxxxxxxxx (module name)
7-) load the module: sudo modprobe -r module name and modprobe module name and modprobe -r
8-) open the file /etc/network/interfaces and make sure that the network connection is the same on the /etc/udev/rules.d/70-persistent-net.rules file.
example: 
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="xxxxxxx", NAME="eth0" on the etc/udev/rules.d/70-persistent-net.rules, must match the 
auto eth0
iface eth0 inet static

on the /etc/network/interfaces 

9-) stop the network daemon: sudo /etc/init.d/networking stop
10-) start the network daemon: sudo /etc/init.d/networking start


and then your network should be working properly..

and doubts, please ask me.

---

