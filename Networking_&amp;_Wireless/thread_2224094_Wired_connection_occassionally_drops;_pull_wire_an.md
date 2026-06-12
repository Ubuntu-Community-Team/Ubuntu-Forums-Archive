---
title: "Wired connection occassionally drops; pull wire and re-insert fixes the problem."
date: 2014-05-14
forum: Networking &amp; Wireless
---

### Post by brichert on 2014-05-14
I upgraded to 14.04 to try to fix a networking problem. Every so often, the wired connection just drops. I can fix the problem by pulling the ethernet cable out of the wall, and plugging it back in. Sometimes I have to pull a few times, but after a minute or so I'm back online. I've updated the driver for the ethernet card. I suspect it is the card since everything works fine on the old workstation sitting right next to the new one, and except that the old one is running 12.04, everything is configured the same. Actually, I originally install 12.04 on the new machine, but couldn't get it to work, so after a few months, I upgraded to 14.04. Hope springs eternal, but alas, it did not fix the problem.

contents of /etc/network/interface 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address 129.65.56.22
      netmask 255.255.255.0
      gateway 129.65.56.250
      dns-nameservers 129.65.16.254 129.65.21.254

Here's a route -n while things are running:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.65.56.250   0.0.0.0         UG    0      0        0 eth0
129.65.56.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

output of ethtool -i eth0 

driver: e1000e
version: 3.0.4.1-NAPI
firmware-version: 0.13-4
bus-info: 0000:00:19.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no

output of lshw -C network

  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 90:b1:1c:78:87:26
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.0.4.1-NAPI duplex=full firmware=0.13-4 ip=129.65.56.22 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:44 memory:f7f00000-f7f1ffff memory:f7f39000-f7f39fff ioport:f040(size=32)


The network manager thinks things are unmanaged.

Any thoughts? This is an extension of the post [http://ubuntuforums.org/showthread.php?t=2183423](http://ubuntuforums.org/showthread.php?t=2183423). Since updating didn't fix the problem, I thought we could try again. 

Thanks.

---

### Post by praseodym on 2014-05-14
Please show the outputs of:

```
sudo apt-get install ethtool
sudo ethtool eth0
cat /etc/NetworkManager/NetworkManager.conf 
```

---

### Post by brichert on 2014-05-15
Hi praseodym,

Here's the output of all those commands:


brichert@richert:~$ sudo apt-get install ethtool
[sudo] password for brichert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
brichert@richert:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off (auto)
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes
brichert@richert:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
brichert@richert:~$

---

### Post by praseodym on 2014-05-16
```
 dns-nameservers 129.65.16.254 129.65.21.254
```
These nameservers seem to be wrong, change both to one, the router IP 129.65.56.250

Additionally, change "false" to "true" in the "*.conf" file and reboot.

---

### Post by brichert on 2014-05-16
Changing the dns-nameservers kills the connection, alas. I'm at a university and I think that the name-servers as listed are correct. In any event, I'm still waiting on the managed question, and will report back. Thanks for help!

---

### Post by brichert on 2014-05-19
Changing managed from false to true also seems not to make a difference. Actually, things have gotten worse. Today, for the first time, the pull the plug trick didn't fix things. I tried several times, including rebooting. Eventually, I changed my connection from static to dhcp (as shown below) and can get online via reboot. I don't know if this is a fluke however. 

auto lo
iface lo inet loopback

iface eth0 inet dhcp
#address 129.65.56.22
#netmask 255.255.255.0
#gateway 129.65.56.250

auto eth0


One interesting thing. Even when I couldn't get online (via Mozilla, or pinging from the command line) ethtool showed the link as connected, so some part of the computer seems to know that I am plugged in, but then things get hung up in the processing! If anyone has any ideas, your help would be greatly appreciated!

---

### Post by praseodym on 2014-05-19
What does
```
ifconfig -a
cat /etc/resolv.conf
```
show if its working or not working?

---

### Post by brichert on 2014-05-19
Here's what it says when things are down. I can't seem to get things to come back up without going back to dhcp (and it hasn't crashed yet when I forget about my static ip, although who knows what will happen overnight).

brichert@richert:/etc/network$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 90:b1:1c:78:87:26  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:112309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31905254 (31.9 MB)  TX bytes:3168732 (3.1 MB)
          Interrupt:20 Memory:f7f00000-f7f20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:517620 (517.6 KB)  TX bytes:517620 (517.6 KB)

brichert@richert:/etc/network$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 129.65.16.254
nameserver 129.65.21.254
search cosam.calpoly.edu

While the connection was up and running (with an dhcp instead of static ip address per the interfaces file above) those commands yield:

brichert@richert:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 90:b1:1c:78:87:26  
          inet addr:129.65.56.82  Bcast:129.65.56.255  Mask:255.255.255.0
          inet6 addr: fe80::92b1:1cff:fe78:8726/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31343491 (31.3 MB)  TX bytes:3036852 (3.0 MB)
          Interrupt:20 Memory:f7f00000-f7f20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:501207 (501.2 KB)  TX bytes:501207 (501.2 KB)

brichert@richert:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 129.65.16.254
nameserver 129.65.21.254
nameserver 127.0.1.1
search cosam.calpoly.edu

---

### Post by brichert on 2014-05-20
Another bit of news. The ethernet doesn't go down, or at least, didn't go down overnight which is the longest it has ever lasted, when set to dhcp. I still need to get the static ip address up and running, alas.

---

### Post by praseodym on 2014-05-20
You are not getting an IPv4 address. Check "sudo dhclient eth0" when its not working.

---

### Post by brichert on 2014-05-20
Hmm, sudo dhclient eth0 just hangs.

---

### Post by varunendra on 2014-05-21
Have you tried any driver parameters yet? Looks like the card goes to sleep when there is no activity, and fails to resume. Not sure why the dhcp configuration is exceptional, maybe some cornjob or a similar activity keeps invoking dhclient on a regular interval.

Anyway, there are two parameters available with e1000e driver that look interesting to me - "SmartPowerDownEnable" and "KumeranLockLoss". Although the former one already seems to be disabled by default (as per default value information in page 57 of [this guide]("http://ftp.us.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_pedge_srvr_ethnt_nic/intel-pro-adapters_User's%20Guide_en-us.pdf")), so let's try toggling the value -
```
sudo modprobe -rv e1000e
sudo modprobe -v e1000e SmartPowerDownEnable=1
```
Any miracles? If not, repeat the commands with value '0' again. If still no joy, try the next one -
```
sudo modprobe -rv e1000e
sudo modprobe -v e1000e KumeranLockLoss=0
```
The other acceptable value for it is '1', so try it as well if required.

These are blind shots and I have no idea if they can help or not.

---

### Post by brichert on 2014-05-21
Well, I've finally tracked it down, and it turned out to be a local problem. You will all have to forgive my ham-fisted explanation ... when I set up the new workstation, I assumed that I could use the old pinhole. Somehow the old ip address and the MAC address of the old computer were linked, this per the network guy here (Ubuntu is unsupported on campus, but I was chasing down praseodym's suggestion that something was fishy with the dns-nameserver, so I was making sure all those parameters were correct, and he noticed the discrepancy). Why it would sometimes work for a while is a mystery to me. Maybe some network audit that ran occasionally and noticed the difference? In any event, they shifted the ip which somehow matches the new MAC address, and this morning it was still running. Thanks everyone for your help!

---

