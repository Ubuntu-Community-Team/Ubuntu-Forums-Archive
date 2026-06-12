---
title: "Wireless wont work and im crying"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by De Kennis Slevin Angel on 2006-11-08
i have the driver installed using the windows wireless driver install and it says the driver is present but nothing is connecting to think i set up networks on cento's and freebsd and i cant get a wireless driver to install on my system im using 6.10 someone mind helping me get it to work ndiswrapper is installed i even tried using kwifimanager help me please maybe i can repay somehow with some of my knowledge. my head is killing me like i have been doing ](*,)  this all day and in reality its me setting up a wireless card

---

### Post by dmizer on 2006-11-08
does it say the driver is present and that the hardware is present? should look something like this:
```
$ ndiswrapper -l
Installed ndis drivers:
lsbcmnds                driver present 
lstinds         driver present, hardware present 
```
might help very much to know what your wireless adapter is.  so please post the output of:
```
lspci
```

---

### Post by De Kennis Slevin Angel on 2006-11-08
the driver does say its present

---

### Post by dmizer on 2006-11-09
yes ... you said this before.  does it say **_BOTH_** "driver present" **_and_** "hardware present"?

again ... please post the output of lspci.  there's not much we can do to help you if you don't provide necessary information like this.

---

### Post by De Kennis Slevin Angel on 2006-11-09
```

$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
```

```
$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

---

### Post by insub2 on 2006-11-09
what do you get for ```
iwconfig
``` and ```
ifconfig
```?

I have the same wifi card and am having similar problems.

---

### Post by trubblemaker on 2006-11-09
if you just upgraded and things went boom.  uninstall the driver
```
 ndiswrapper -e bcmwl5 
```
then [try out this script that installs it from source]("http://ubuntuforums.org/showpost.php?p=1699287&postcount=451").  I've helped alot of people recently that upgraded and had everyting go boom.

Also since your using bcm4306 so that means bcm43xx, so if you haven't blacklisted it. the script will show you how.  don't  have more time to explain bcm43xx fights with ndiswrapper....

Cheers

---

### Post by De Kennis Slevin Angel on 2006-11-09
gonna try those scripts i think i have done it and for the iwconfig and ifconfig there is the output


```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.
```

```
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0D:56:78:EA:92  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:805172 (786.3 KiB)  TX bytes:201444 (196.7 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:64:75:5E  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:fafee000-faff0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276 (5.1 KiB)  TX bytes:5276 (5.1 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.14.1  Bcast:172.16.14.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.163.1  Bcast:172.16.163.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by dmizer on 2006-11-09
you don't have to do squat.  you're connected wirelessly.  according to iwconfig, your wireless card is eth1.  if you look at ifconfig, eth1 HAS AN IP.  this means that if you disable eth0, you should be able to browse wirelessly.

that is ... unless you've statically assigned that ip address.  you could also be having interference with your vmware's network bridge.

---

### Post by finite9 on 2006-11-09
see my sig.  assumes you've not messed too much with scripts :)

---

### Post by De Kennis Slevin Angel on 2006-11-09
> **dmizer said:**
> you don't have to do squat.  you're connected wirelessly.  according to iwconfig, your wireless card is eth1.  if you look at ifconfig, eth1 HAS AN IP.  this means that if you disable eth0, you should be able to browse wirelessly.

that is ... unless you've statically assigned that ip address.  you could also be having interference with your vmware's network bridge.

Disable my wired in what? network manager i did that and no internet. 
only reason i think it shows my ip is because i config it instead of using dhcp

---

