---
title: "Cisco Aironet PC4800 not being recognized"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by somu76 on 2008-06-17
Hi,
  I just installed Ubuntu 8.04 desktop version on my IBM Thinkpad T21, and am not seeing my card being picked up.. It is a PCMCIA card.. By looking through some of the threads here, it seems like lot of people were asking for output of lspci to start troubleshooting, so here is it below:

laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:02.0 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:02.1 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:03.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 09)
00:03.1 Serial controller [0700]: Xircom Mini-PCI V.90 56k Modem [115d:000c]
00:05.0 Multimedia audio controller [0401]: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] [1013:6003] (rev 01)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
01:00.0 VGA compatible controller [0300]: S3 Inc. 86C270-294 Savage/IX-MV [5333:8c12] (rev 13)



Please let me know how I should go about getting this added to my system.

Thanks,
somu.

---

### Post by chili555 on 2008-06-17
With the card in the slot, please let us see:```
sudo lshw -C network
lspcmcia -v
```Thanks.

---

### Post by somu76 on 2008-06-17
thanks.. here is the info you requested.. seems like the card does show up (to an extent), but I don't see it in the Network connections list... 

aptop:~$ sudo lshw -C network

[sudo] password for vasu: 

  *-network               

       description: Aironet

       physical id: 0

       version: PC4800

       slot: Socket 0

  *-network

       description: Ethernet interface

       product: 82557/8/9/0/1 Ethernet Pro 100

       vendor: Intel Corporation

       physical id: 3

       bus info: pci@0000:00:03.0

       logical name: eth0

       version: 09

       serial: 00:10:a4:78:1f:ff

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s



vasu@mummy-laptop:~$ lspcmcia -v

Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:02.0)

	Configuration:	state: on	ready: unknown

			Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V

Socket 0 Device 0:	[-- no driver --]	(bus ID: 0.0)

	Configuration:	state: on

	Product Name:   Aironet PC4800 

	Identification:	manf_id: 0x015f	card_id: 0x0007

			function: 6 (network)

			prod_id(1): "Aironet" (0x207bb848)

			prod_id(2): "PC4800" (0xbf73f7ef)

			prod_id(3): --- (---)

			prod_id(4): --- (---)

Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:02.1)

	Configuration:	state: on	ready: unknown

			Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V

vasu@mummy-laptop:~$

---

### Post by chili555 on 2008-06-17
Please see this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398)

The fix here has helped quite a few Aironet owners:> I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aesReboot and then post back and let us know.

---

### Post by somu76 on 2008-06-17
thanks a bunch.. i got that part working, and am able to see my card now.. any tricks to get it work with WEP? I have WEP 128 bit privacy, and it doesn't seem to be able to connect to my wireless network...

---

### Post by chili555 on 2008-06-17
I do it the old fashioned way. I set up */etc/network/interfaces* like this:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid mylilrouter
wireless-key <26-character-hex>
```Then, with a:```
sudo ifdown eth1 && sudo ifup eth1
```I then connect.

I think a lot of problems here are actually Network Manager issues. Post back if you get stuck.

---

### Post by somu76 on 2008-06-17
nope.. didn't work.. here is what I got... 


```
laptop:~$ sudo ifdown eth1 && sudo ifup eth1
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5552
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:40:96:28:e6:7a
Sending on   LPF/eth1/00:40:96:28:e6:7a
Sending on   Socket/fallback
grep: /etc/resolv.conf: No such file or directory
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:40:96:28:e6:7a
Sending on   LPF/eth1/00:40:96:28:e6:7a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
```


my interfaces file looks like this:


```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid somunet
wireless-key ########(26bitkey)
```


I also ran the following commands :

```
laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:a4:78:1f:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:40:96:28:e6:7a  
          inet6 addr: fe80::240:96ff:fe28:e67a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:884 dropped:0 overruns:0 frame:884
          TX packets:3 errors:5 dropped:0 overruns:2 carrier:0
          collisions:76 txqueuelen:1000 
          RX bytes:8354 (8.1 KB)  TX bytes:1944 (1.8 KB)
          Interrupt:3 Base address:0x100 

eth1:avahi Link encap:Ethernet  HWaddr 00:40:96:28:e6:7a  
          inet addr:169.254.7.223  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109776 (107.2 KB)  TX bytes:109776 (107.2 KB)
```

and

```
laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"somunet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:33:69:E4   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-** [2]   Security mode:open
          Power Management:off
          Link Quality=88/100  Signal level=-52 dBm  Noise level=-98 dBm
          Rx invalid nwid:3883  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:5767   Missed beacon:1

wifi0     IEEE 802.11-DS  ESSID:"somunet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:33:69:E4   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-** [2]   Security mode:open
          Power Management:off
          Link Quality=88/100  Signal level=-52 dBm  Noise level=-98 dBm
          Rx invalid nwid:3883  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:5767   Missed beacon:1
```


Not sure what I am doing wrong here.. I even tried replacing eth1 with wifi0 (wild guess), but with same results... 

any idea as to what might be wrong? I know that my wireless router is working coz I have other machines that are connecting fine... 

any ideas are much appreciated.

thanks,
somu.

---

### Post by chili555 on 2008-06-17
> Encryption key:****-****-****-****-****-****-** [COLOR="Red"][2][/COLOR]  Security mode: openI wonder what [2] means here? Does it mean that your router is broadcasting key #2 of the four available keys? I wonder how it knows! I sure have never seen this. Just in case it is key #2 and you are certain your router is using key #1, please do:```
sudo iwconfig eth1 key [1]
sudo dhclient eth1
```I will be utterly fascinated to read your reply.

---

### Post by somu76 on 2008-06-18
unfortunately, that didn't work.. it did remove the [2] though... I tried connecting a wire to it, to verify if the DHCP stuff is working and to check if the router can see this laptop, and I did end up getting an IP through eth0. so, I know that the dhcp is working.. however, I can't seem to be able to get through using wireless... 

tried removing the entries in /etc/network/interfaces, restart networking using "/etc/init.d/networking restart", specifying the essid and key directly using "sudo iwconfig eth1 essid somunet key <key>", and doing "sudo dhclient eth1", but the same result everytime... does the output from iwconfig and ifconfig show anything special here? or problematic here?

since my router used channel 6, added that also above to the iwconfig command, with no luck... 

any other commands/stuff to try?

thanks for looking into this.
somu.

---

### Post by somu76 on 2008-06-18
bump up to the front.

---

### Post by chili555 on 2008-06-18
Does your router use 'Authentication Type' Shared Key or Auto? Please restore your *interfaces* items and add:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid somunet
wireless-key ########(26bitkey) **restricted**
```Then do:```
sudo ifdown eth1 && sudo ifup eth1
```Thanks.

---

### Post by somu76 on 2008-06-18
no dice... and my router uses Auto as its auth type.

---

