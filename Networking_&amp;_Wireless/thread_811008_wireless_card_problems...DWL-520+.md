---
title: "wireless card problems...DWL-520+"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by UltraDangerLord on 2008-05-28
Hello All,

So I've been trying to connect to the internet using this wireless card a d-link DWL-520+.

Obviously I'm missing a step on just not doing something right...
I think it recoginizes the card now. it just cant find the networks. also the network i am connecting to is unsecured to make it easier....however i never entered this info anywhere...

I found some info on the driver needed and instructions on making this work properly here.

[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

which tells me to do this...(basically disable network manager)

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
echo "exit" > /etc/default/NetworkManager
echo "exit" > /etc/default/NetworkManagerDispatcher
sudo ifdown wlan0
sudo ifup wlan0

now at first when i entered 

sudo ifdown wlan0
sudo ifup wlan0

it gave a message saying wlan0 is not configured

so i added it to the /etc/network/interfaces file.

after that i rebooted the system... and it gave me this...

ultradangerlord@ultradangerlord-desktop:~$ ifconfig
wlan0     
Link encap:Ethernet  HWaddr 00:80:c8:11:f5:b1  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 

RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
Interrupt:19 Base address:0xe800 


wlan0:avahi Link encap:Ethernet  
HWaddr 00:80:c8:11:f5:b1  
          
inet addr:169.254.9.141  Bcast:169.254.255.255  Mask:255.255.0.0
          

UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
Interrupt:19 Base address:0xe800 



ultradangerlord@ultradangerlord-desktop:~$ sudo ifdown 

wlan0
[sudo] password for ultradangerlord: 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5493
killed old client process, removed PID file


Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/wlan0/00:80:c8:11:f5:b1
Sending on LPF/wlan0/00:80:c8:11:f5:
b1
Sending on   
Socket/fallback
grep: /etc/resolv.conf: No such file or directory
ultradangerlord@ultradangerlord-desktop:~$ sudo ifup wlan0 


There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/wlan0/00:80:c8:11:f5:b1
Sending on   LPF/wlan0/00:80:c8:11:f5:b1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
ultradangerlord@ultradangerlord-desktop:~$ 


apparently all version of ubuntu 6 and later have the driver on it by default you just have to turn off the network manager.. but after that the documentation gets pretty vague

---

### Post by UltraDangerLord on 2008-05-29
Bump

---

### Post by prshah on 2008-05-30
> **UltraDangerLord said:**
> 
So I've been trying to connect to the internet using this wireless card a d-link DWL-520+.

Obviously I'm missing a step on just not doing something right...


Why not try my step-by-step guide (with expected outputs) ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)) to set up your wireless? If you're sure your card is detected, you can jump straight to step 9. If you run into any problems, post back here with which step you are stuck at.

---

### Post by Dji on 2008-11-30
Hello everyone,

I've got a big trouble with my wireless card. I have a DWL-520+ card and it doesn't work with ubuntu (it works well with my windows XP).
I've tried with 8.04 and 8.10 (and even with 7.10 lol) but ... nothing :(


I've installed ndiswrapper and tried to install the windows driver. I tried with the one on the CD and I've tried with the last release of D-LINK too but nothing :/. I've probably missed something. Maybe Someone could help me? ^^

Here is what I did:

I get my INF file "wrapped" with ndiswrapper 
```
**sudo ndiswrapper -i GPLUS.inf**
```
I verify my device has been found 
```
**sudo ndiswrapper -l**
gplus : driver installed
	device (104C:9066) present

```

I add information about my "wrapped" device driver to the module library
```

**sudo ndiswrapper -m**
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

```
here i don't know what I have 3 answers xD . Something wrong ? :s



```
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

eth0 is my ethernet wired card (i.e not my wireless one :) I'm sure about that.
About pan0 I don't know what it is. I suppose it's my wireless but not recognized very well.
Anyway no wireless extensions :( so somehitng is going bad :'(

here are some informations about my hardware that may help

```

**sudo lshw -C network**
  *-network UNCLAIMED     
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 8
       bus info: pci@0000:05:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:c9:8e:19:83:c0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
Thank you for having read and for your help :)

---

### Post by prshah on 2008-12-01
> **Dji said:**
> ```
**sudo ndiswrapper -l**
gplus : driver installed
	device (104C:9066) present

```

```

**sudo ndiswrapper -m**
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

```
here i don't know what I have 3 answers

```
**iwconfig**


```


You are getting three lines for "-m" because you probably have more driver installed with ndiswrapper; I suspect you've tried a number of drivers. In any case, this is not a problem.

After "modularizing" ndiswrapper, but _before_ iwconfig, you have to load the ndiswrapper module```
sudo modprobe ndiswrapper
``` You should have a wireless interface within a few seconds of this command, which will be seen with iwconfig.

If you don't have one, then check for errors with ```
dmesg | tail
``` and post back any error seeming messages.

pan0 refers to bluetooth networking (personal area network), and you can ignore that, it will not cause any kind of conflicts.

---

### Post by Dji on 2008-12-01
Thank you for your reply prshah :)

I loaded the ndiswrapper module but I forgot to write it in my last post, sorry ^^'
```
**sudo modprobe ndiswrapper**

```
and this command returns nothing to the terminal now but I don't remember if there was something written when I did it yesterday :s

And of course iwconfig gives still no wireless :(


Concerning dmesg | tail I got that  (I confess I understand nothing about it :confused: )
```
 **dmesg | tail**
[  141.944312] type=1503 audit(1228131398.690:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944323] type=1503 audit(1228131398.690:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944330] type=1503 audit(1228131398.690:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944337] type=1503 audit(1228131398.690:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944343] type=1503 audit(1228131398.690:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944350] type=1503 audit(1228131398.690:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944356] type=1503 audit(1228131398.690:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944363] type=1503 audit(1228131398.690:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944426] type=1503 audit(1228131398.690:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5979/net/dev" pid=5979 profile="/usr/sbin/cupsd"
[  152.052006] eth0: no IPv6 routers present
```

---

### Post by prshah on 2008-12-01
> **Dji said:**
> 
```
**sudo modprobe ndiswrapper**

```
and this command returns nothing to the terminal 

That is correct, it should return nothing if there is no error. Also, the dmesg lines you posted are not relevant (did you do that immediately after give the modprobe command?)

You can try giving the command```
sudo depmod -a
``` to refresh all module information and then using the modprobe command again.

Remember it will take about 5~10 seconds (but not more) for the wireless interface to show up in iwconfig.

---

### Post by Dji on 2008-12-01
[quote=prshah](did you do that immediately after give the modprobe command?)[/quote]
yes I did the **dmesg | tail ** "immedialty" after the **sudo modprobe ndiswrapper** (After 10 sec around , not immediatly immediatly ^_^ )

And after the 
```
**sudo depmod -a**
```
*I wait 10 seconds*
I get 
```
**dmesg | tail**
[  141.944312] type=1503 audit(1228131398.690:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944323] type=1503 audit(1228131398.690:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944330] type=1503 audit(1228131398.690:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944337] type=1503 audit(1228131398.690:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944343] type=1503 audit(1228131398.690:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944350] type=1503 audit(1228131398.690:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944356] type=1503 audit(1228131398.690:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944363] type=1503 audit(1228131398.690:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5979 profile="/usr/sbin/cupsd"
[  141.944426] type=1503 audit(1228131398.690:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5979/net/dev" pid=5979 profile="/usr/sbin/cupsd"
[  152.052006] eth0: no IPv6 routers present
```
nothing has changed it seems :(

```

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```
And still no wireless :(

---

### Post by Dji on 2008-12-03
up  8-[

---

### Post by prshah on 2008-12-04
> **Dji said:**
> up  8-[

```
cat /etc/network/interfaces
``` please?

---

### Post by Dji on 2008-12-04
```
**cat /etc/network/interfaces**
auto lo
iface lo inet loopback
```
thank you for your help :-)

---

### Post by Dji on 2008-12-06
Hi
I've downgraded to 8.04 thinking maybe I could be more lucky because it's a LTS. So I've done all upgrades ...  but nothing new.

As ndiswrapper didn't seem to work (I really wonder why), I've tried to follow this how to [http://www.houseofcraig.net/acx100_howto.php#trouble_compiling]("http://www.houseofcraig.net/acx100_howto.php#trouble_compiling"). But when I compile 
```

**make**
Kernel version file: /lib/modules/2.6.24-19-generic/build/include/linux/version.h
Kernel configuration file: /lib/modules/2.6.24-19-generic/build/.config
Make damn sure these really match your currently running kernel!!

Kernel configuration found, performing sanity checks
All of the following items are required by the driver:
    Loadable modules support is enabled.
    [COLOR="Red"]Wireless LAN (non-hamradio) support is DISABLED![/COLOR]
    [COLOR="Red"]Wireless extensions support is DISABLED![/COLOR]
The following is needed for PCMCIA/CardBus cards:
    PCMCIA support is enabled.
    CardBus support is enabled.
The following is needed for USB card support:
    USB support is enabled.
The following is needed for PCI card support:
    PCI support is enabled.
Kernel configuration lacks needed options, please correct! ABORTING.
make: *** [config.mk] Error 1

```
I had been able to enalbe **wireless extensions support** during a time but no way with **Wireless LAN**.
This wireless card makes me crazy ](*,)](*,)
ho, and by the way I've discovered that it's a dwl-G520+ and not a dwl-520+ . But both of them have a Texas Instrument acx 111 chip so I think it doesn't matter.

---

### Post by Dji on 2008-12-14
I GOT IT :guitar:
I've finally got it !! omg I'm happy !! This fu... card works ^_^
I've given up to try to compile the kernel and I've come back to the ndiswrapper solution. I've tried a dozen of versions and the one working for me was
[ftp://ftp.dlink.fr/DWL/DWL-G520+/Driver/dwl-g520_drv_v1.0]("ftp://ftp.dlink.fr/DWL/DWL-G520+/Driver/dwl-g520_drv_v1.0")

dunno why this one only <_<. Even the one from my CDROM given with my card didn't work lol

Thank prshah for your advised commands :)

---

