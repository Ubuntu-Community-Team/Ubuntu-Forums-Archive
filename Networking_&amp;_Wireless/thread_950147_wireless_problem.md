---
title: "wireless problem"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by johnshentiro1 on 2008-10-16
when i start my laptop,I always find the error message
Error:module b43 does not exist in /proc/module
Error:module b43ledge does not exist in /proc/module

there is my infomation about my laptop:
==========================================================================
john@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:c3:9f:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:09:e2:62
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.136 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
john@ubuntu:~$ lspci -v | grep Ethernet
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
john@ubuntu:~$ lsmod | grep ath
john@ubuntu:~$ 
john@ubuntu:~$  sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=-44 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

john@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:09:e2:62  
          inet addr:192.168.1.136  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe09:e262/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4433832 (4.2 MB)  TX bytes:610657 (596.3 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1f:e1:c3:9f:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:96
          TX packets:45 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7877 (7.6 KB)  TX bytes:6482 (6.3 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77600 (75.7 KB)  TX bytes:77600 (75.7 KB)

john@ubuntu:~$ 
======================================================================

i am a tyro on Ubuntu,i am not know how to solve the problem.could anybody help me to fix this? :(

---

### Post by Ayuthia on 2008-10-16
> **johnshentiro1 said:**
> when i start my laptop,I always find the error message
Error:module b43 does not exist in /proc/module
Error:module b43ledge does not exist in /proc/module

This looks like you have a script that is trying to remove the b43 and b43legacy modules.  By any chance did you add anything to /etc/rc.local or possibly /etc/init.d/wirefix.sh?  If you are not sure, can you post the results of (from the Terminal):
```
grep b43 /etc/rc.local
grep b43 /etc/init.d/*.sh
```This will search through /etc/rc.local and the /etc/init.d/*.sh files to see if there is any information about b43 in them.  If there is, that is most likely the file that is causing the problem.

By the way, is your wireless working?

---

### Post by johnshentiro1 on 2008-10-17
yes,I add the following text into my wirelessfix.ssh
there are the content added in it:
#!/bin/bash
#this script unloads the ssb module so that it doesn't claim the Broadcom card

rmmod b43
rmmod b44
rmmod b43legacy
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
ifconfig wlan0 up

========================================================================
here is the result :

john@ubuntu:~$ grep b43 /etc/rc.local
john@ubuntu:~$ grep b43 /etc/init.d/*.sh
/etc/init.d/wifi-fix.sh:rmmod b43
/etc/init.d/wifi-fix.sh:rmmod b43legacy
/etc/init.d/wirelessfix.sh:modprobe -r b43
/etc/init.d/wirelessfix.sh:modprobe -r b43legacy

thanks,what is to do next?

---

### Post by johnshentiro1 on 2008-10-17
> **Ayuthia said:**
> By the way, is your wireless working?

By now,I still not find some way to solve the problem. while there is no error appears,could you help me fire this problem? 

oh,thanks for your reply.

---

### Post by Ayuthia on 2008-10-17
> **johnshentiro1 said:**
> 
Error:module b43ledge does not exist in /proc/module

Is this a misprint?  Was it supposed to say b43legacy?

The error message that you are seeing is because the b43 and b43legacy modules are not loaded.  Since it is not there, rmmod shows this message.  

However, the wirelessfix.sh is causing the problem with your wl driver that you are trying to use.  It is loading the ndiswrapper module which will conflict with the wl module.

> john@ubuntu:~$ grep b43 /etc/rc.local
john@ubuntu:~$ grep b43 /etc/init.d/*.sh
/etc/init.d/wifi-fix.sh:rmmod b43
/etc/init.d/wifi-fix.sh:rmmod b43legacy
/etc/init.d/wirelessfix.sh:modprobe -r b43
/etc/init.d/wirelessfix.sh:modprobe -r b43legacyThis shows that you have two files (wifi-fix.sh and wirelessfix.sh) that are trying to do something for your wireless card.  I would recommend commenting out the lines in those two files for now because if you want to use the wl driver, those two files will cause problems.

To see if you wl module works, you can try the following (will only work for the current session):
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper
sudo modprobe wl
```It might take a few seconds for network manager to see the wireless module change.

---

### Post by johnshentiro1 on 2008-10-19
as you metioned,I comment out the two line in wifi-fix.sh and wirelessfix.sh
there is the result:

john@ubuntu:/etc/init.d$ less wifi-fix.sh
#!/bin/bash
#this script unloads the ssb module so that it doesn't claim the Broadcom card

#rmmod b43
rmmod b44
#rmmod b43legacy
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
ifconfig wlan0 up
 ESC

john@ubuntu:/etc/init.d$ less wirelessfix.sh 
#!/bin/bash
#modprobe -r b44
#modprobe -r b43
#modprobe -r b43legacy
#modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

But what confuse me is can I remove the wirelessfix.sh?
I removed the wirelessfix.sh.Is that right?

and when i login after remove the wirelessfix.sh and press ctrl+alt+F1.There is all the error message.
is There something wrong?could you help me to clear this?

========================================================================
Starting powernowd...
Error:Module b44 does not exist in /etc/modules
Error:Module ssb does not exist in /etc/modules
wlan0:ERROR while get interface flag:No such device
...
Runing local boot scripts(/etc/rc.local)
Error:Module b43 does not exist in /etc/modules
Error:Module b44 does not exist in /etc/modules
Error:Module b43legacy does not exist in /etc/modules
Error:Module ssb does not exist in /etc/modules
Error:Module b43 does not exist in /etc/modules
Error:Module b43legacy does not exist in /etc/modules

========================================================================

what's next step?

---

### Post by Idefix82 on 2008-10-19
Please follow Ayuthia's advice:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper
sudo modprobe wl
sudo ifup eth1
sudo iwlist eth1 scan

```
and see if you get connected. Let us know, before you do anything else. If this works then all you will need to do is make sure that ndiswrapper is not interfering with your wireless driver. If it doesn't work then we will have to try the ndiswrapper way.

---

### Post by johnshentiro1 on 2008-10-19
> **Idefix82 said:**
> Please follow Ayuthia's advice:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper
sudo modprobe wl
sudo ifup eth1
sudo iwlist eth1 scan

```

yes,I follow it,I can see the connection,but I can not get connect.there is the result
==================================================================
john@ubuntu:~$ sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper
john@ubuntu:~$ sudo modprobe wl
john@ubuntu:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
john@ubuntu:~$ sudo iwlist eth1 scan
eth1      Failed to read scan data : Invalid argument

john@ubuntu:~$ 
==================================================================
pls help me!I don't like get connect only with my wired network

---

### Post by Ayuthia on 2008-10-19
I forgot to have you clear out the wl module also.  Please try the following:
```
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper wl bcm43xx
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

EDIT:
If it still does not work, please post the results of lshw -C network.

---

### Post by johnshentiro1 on 2008-10-20
Thanks,Ayuthia.
I do what you tell me ,but it still can not work,Ooops!
here is the result:

==========================================================================
john@ubuntu:~$ sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper wl bcm43xx
[sudo] password for john: 
john@ubuntu:~$ sudo modprobe wl
john@ubuntu:~$ sudo ifconfig eth1 up
john@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 6E:3C:23:0F:1D:05
                    ESSID:"SpeedStream"
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Quality:2/5  Signal level:-70 dBm  Noise level:-91 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:03:7F:1E:F7:D8
                    ESSID:"TENDA"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-88 dBm  Noise level:-15 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:18:39:6F:49:46
                    ESSID:"Siloon_Linksys"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-44 dBm  Noise level:-27 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 00:1B:11:8C:17:BA
                    ESSID:"CDZH"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-13 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 54 Mb/s

john@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:c3:9f:d6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:09:e2:62
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
==========================================================================
how can i do next step?

---

### Post by Ayuthia on 2008-10-20
It looks like your card is able to see wireless sites now.  The next step is to see if you can connect.  I don't have too much experience with WPA so I am not going to be able to help you too much there.  

The next step that you should try to do is turn off your encryption and see if you can connect to the router.  I am guessing that yours has WPA on it because of the signal strength (Siloon_Linksys shows a signal strength of 5/5).  If you are able to connect, you will then need to figure out how to connect using WPA.  Also, if you are able to connect, you might want to get the system updated so that you can have the most up-to-date version of your wireless driver.

---

