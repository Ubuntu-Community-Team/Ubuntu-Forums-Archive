---
title: "wireless card active, but not working"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Tanja on 2007-05-23
Hi there,

I am trying to set up a wireless connection on my laptop (Dell Inspiron 1300).

In system/administration/networking my Wireless Connection is detected. I can activate it clicking on Activate. However, after setting up the properties for the my wifi network, it will not work.

I have installed wlassistant. When I open it, this is the output:
> 
tanja@tanja-laptop:~$ sudo wlassistant
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): eth1
Permissions checked.
ifconfig_status: /sbin/ifconfig eth1
ifup: /sbin/ifconfig eth1 up
==>stderr: SIOCSIFFLAGS: No such file or directory
scan: /sbin/iwlist eth1 scan
==>stderr: eth1      Interface doesn't support scanning : No such device

No networks found!

Any ideas?

By the way, this is the output for iwconfig:
> 
tanja@tanja-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"2WIRE145"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


THANKS A LOT!

---

### Post by tomiu on 2007-05-23
what is output from:

**egrep -v "^$|^#" /etc/network/interfaces**
**egrep -v "^$|^#" /etc/resolv.conf**
**egrep -v "^$|^#" /etc/hosts**

**ifconfig**
**iwlist scan**
**lspci**

---

### Post by musab on 2007-05-23
> **tomiu said:**
> what is output from:

**egrep -v "^$|^#" /etc/network/interfaces**
**egrep -v "^$|^#" /etc/resolv.conf**
**egrep -v "^$|^#" /etc/hosts**

**ifconfig**
**iwlist scan**
**lspci**

Hello, I'm sorry for sticking my nose in here but i am having the exact  same problem.  whats what I get after these commands

[COLOR="Red"]**egrep -v "^$|^#" /etc/network/interfaces**[/COLOR]

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
auto eth0

[COLOR="Red"]**egrep -v "^$|^#" /etc/resolv.conf**[/COLOR]

nameserver 24.93.41.125
nameserver 24.93.41.126

[COLOR="Red"]**egrep -v "^$|^#" /etc/hosts**[/COLOR]

127.0.0.1       localhost
127.0.1.1       musab-laptop
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

[COLOR="Red"]**ifconfig**[/COLOR]

eth0      Link encap:Ethernet  HWaddr 00:03:25:33:23:D2  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe33:23d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:91999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127173010 (121.2 MiB)  TX bytes:5021404 (4.7 MiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7880 (7.6 KiB)  TX bytes:7880 (7.6 KiB)


[COLOR="Red"]** iwlist scan**[/COLOR]

lo        Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

[COLOR="Red"]**lspci**[/COLOR]

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by tomiu on 2007-05-23
musab, what is output for:

**iwconfig **

---

### Post by freak101 on 2007-05-23
Which driver are you using?
Have you configured your wlan?
try this:
[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom)

---

### Post by musab on 2007-05-23
> **tomiu said:**
> musab, what is output for:

**iwconfig **

[COLOR="Red"]**iwconfig**[/COLOR]

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by musab on 2007-05-23
> **freak101 said:**
> Which driver are you using?
Have you configured your wlan?
try this:
[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom)

I have a built in wireless card on a gateway laptop !

---

### Post by freak101 on 2007-05-24
I have the same card. Try following the link I posted previously. It should work fine.

---

### Post by musab on 2007-05-25
> **freak101 said:**
> I have the same card. Try following the link I posted previously. It should work fine.

After doing the steps I don't see my wireless device any more in System-->Admin-->Network :(

As a programmer I don't feel like going back to windows ;) ... I will wait here for help !

---

### Post by musab on 2007-05-25
I'm using the 64 bit, may be this could help

---

### Post by musab on 2007-05-28
No ?!

---

### Post by freak101 on 2007-05-30
musab, I'm also running a 64 bit version, may be the firmware included in the post I sent you is not the correct one for 64bit.
Try to post your experience also on that thread, may be they can include a 64bit patch to the install procedure if is needed.
Also you can try to configure your nic by hand:

get fwcutter:
$ sudo apt-get install bcm43xx-fwcutter

get windows firmware:
[ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)

Once unzipped look for bcmwl5.sys and run:
$ sudo bcm43xx-fwcutter -w /lib/firmware/$(uname -r) bcmwl5.sys

Now you can find the firmware in  /lib/firmware/$(uname -r) , to check:
ls -l//lib/firmware/$(uname -r)| grep bcm

reload the broadcom driver:
$ sudo modprobe bcm43xx

If also this fails, post the dmesg output or at least the last 40 lines.

---

### Post by musab on 2007-05-31
Ok. I'll try that.

Thanks freak101 and all of u for ur help and time.

---

### Post by musab on 2007-06-02
> **freak101 said:**
> musab, I'm also running a 64 bit version, may be the firmware included in the post I sent you is not the correct one for 64bit.
Try to post your experience also on that thread, may be they can include a 64bit patch to the install procedure if is needed.
Also you can try to configure your nic by hand:

get fwcutter:
$ sudo apt-get install bcm43xx-fwcutter

get windows firmware:
[ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)

Once unzipped look for bcmwl5.sys and run:
$ sudo bcm43xx-fwcutter -w /lib/firmware/$(uname -r) bcmwl5.sys

Now you can find the firmware in  /lib/firmware/$(uname -r) , to check:
ls -l//lib/firmware/$(uname -r)| grep bcm

reload the broadcom driver:
$ sudo modprobe bcm43xx

If also this fails, post the dmesg output or at least the last 40 lines.

Hello freak101...  I think I'm giving up with this

The link you provided me with does not have bcm43xx-fwcutter

here is my typescript

[COLOR="Red"]**$ sudo apt-get install bcm43xx-fwcutter**[/COLOR]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter

//After downloading the zip file, here is the list
[COLOR="Red"]**ls**[/COLOR]

bcm43xx.cat  BCMWL564.SYS  bcmwl5.inf  Setup.exe

[COLOR="Red"]**sudo bcm43xx.cat -w /lib/firmware/$(uname -r) /home/musab/Desktop/win_drivers/bcmwl5.sys **[/COLOR]

bcm43xx.cat: command not found


[COLOR="Red"]** ls -l /lib/firmware/$(uname -r)| grep bcm**[/COLOR]

-rw-r--r--  1 root root   3504 2007-05-24 23:17 bcm43xx_initval01.fw
-rw-r--r--  1 root root     16 2007-05-24 23:17 bcm43xx_initval02.fw
-rw-r--r--  1 root root   3504 2007-05-24 23:17 bcm43xx_initval03.fw
-rw-r--r--  1 root root     16 2007-05-24 23:17 bcm43xx_initval04.fw
-rw-r--r--  1 root root   2536 2007-05-24 23:17 bcm43xx_initval05.fw
-rw-r--r--  1 root root    248 2007-05-24 23:17 bcm43xx_initval06.fw
-rw-r--r--  1 root root   2536 2007-05-24 23:17 bcm43xx_initval07.fw
-rw-r--r--  1 root root   2536 2007-05-24 23:17 bcm43xx_initval08.fw
-rw-r--r--  1 root root    248 2007-05-24 23:17 bcm43xx_initval09.fw
-rw-r--r--  1 root root    248 2007-05-24 23:17 bcm43xx_initval10.fw
-rw-r--r--  1 root root  21672 2007-05-24 23:17 bcm43xx_microcode11.fw
-rw-r--r--  1 root root  16352 2007-05-24 23:17 bcm43xx_microcode2.fw
-rw-r--r--  1 root root  20088 2007-05-24 23:17 bcm43xx_microcode4.fw
-rw-r--r--  1 root root  22272 2007-05-24 23:17 bcm43xx_microcode5.fw
-rw-r--r--  1 root root   1312 2007-05-24 23:17 bcm43xx_pcm4.fw
-rw-r--r--  1 root root   1312 2007-05-24 23:17 bcm43xx_pcm5.fw


---------------------------------------

I appreciate your help. Thanks

---

