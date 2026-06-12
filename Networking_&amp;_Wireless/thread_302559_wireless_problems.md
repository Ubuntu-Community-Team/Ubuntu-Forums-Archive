---
title: "wireless problems"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by aam-aadmi on 2006-11-18
I have just installed Ubuntu 6.06 on a Gateway laptop. The installation was pretty smooth; but now I cannot connect to the internet via the wireless. Can someone advise me how to fix the problem. Below I am giving output from some relevant commands in the terminal.

```
iwconfig

lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


```

```
ifconfig

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)



```

```
ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:E0:B8:54:04:DF
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

```
route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




```


```
cat /etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



```

```
cat /etc/resolv.conf

```
NO OUTPUT for this command.



```
cat /etc/dhcp3/dhclient.conf

# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


```

Thanks in advance.

---

### Post by Kamy on 2006-11-18
I've only done this a couple of times, both with linksys cards (broadcom chipsets) and it's not too easy.  I guess it depends on what wireless card you are using and what chipset it uses as to how you go about setting it up.  You may have to use ndiswrapper and the correct windows driver to get it running if Ubuntu didn't pick it up right away.

Just some food for thought from a noob.

Do a lspci and look for something like this:

03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


that'll tell you what chipset your wireless card is using and you can go hunting from there.

Good luck,

Kamy

---

### Post by aam-aadmi on 2006-11-18
Here is the output from lspci

```
lspci

0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host B ridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bri dge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02 )
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Fir eGL 9000] (rev 01)
0000:02:02.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controlle r (rev 01)
0000:02:02.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controlle r (rev 01)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 1 2)
0000:02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 02)
0000:02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE ( LOM) Ethernet Controller (rev 42)
ravindra@laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)
0000:02:02.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:02.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
0000:02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
0000:02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)


```

I cannot figure out what I need to do to get the internet working over the wireless. Can someone proveide any suggestions?

Thanks.

---

### Post by FrodoB on 2006-11-19
There are two ways to proceed. 

1) Using native drivers, which I would suggest trying first using the bcm43xxx-fwcutter program.

2) Using ndiswrapper, which is not perfect, but should work also.

I have a Compaq Presario laptop that has a builtin Broadcom mini-PCIe 4311 chipset. I did get ndiswrapper working yesterday, but I need to go back and try the bcm43xxx-fwcutter program, again, because the secret with both of them is get the correct NDIS files from Windows, the cutter to extract the firmware, and ndiswrapper to use it as well.

On my ndiswrapper I had to eventually install the conf file for my chip set and disable some parameter called Afterburner which is evidently some Broadcom extention for improving throughput that is not part of one of the 802.11x standards.


Have you looked at this instruction? I did not know about it yesterday, but it seems to get things going in the correct direction.

---

### Post by Kamy on 2006-11-19
FrodoB, 

Thanks for the info on that, I didn't realize there was a native driver written for the Broadcom43xx chipset cards.  As a noob I just kind of blundered around the web until I got it working  :) however no problem using ndiswrapper. 

aam-aadmi,

Here's some info on the items FrodoB mentioned,

fwcutter or ndis prefered for broadcom wirelesss cards?
[http://ubuntuforums.org/showthread.php?t=288980&highlight=bcm43xx-fwcutter](http://ubuntuforums.org/showthread.php?t=288980&highlight=bcm43xx-fwcutter)

WifiDocs/Driver/bcm43xx/Dapper
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

Good luck,

Kamy

---

### Post by aam-aadmi on 2006-11-19
Thanks for the information. I will try them and get back to the forum if needed.

---

