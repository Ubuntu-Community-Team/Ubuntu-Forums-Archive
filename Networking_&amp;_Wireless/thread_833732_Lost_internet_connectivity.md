---
title: "Lost internet connectivity???"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by flyinggreg on 2008-06-18
I am a newb that needs some networking help.  I just ran an update on Hardy and now my networking connectivity is gone!  It seems like every time I run a kernel update from the update manager, I lose eth0 connectivity.  In the past I have gotten so frustrated, I would just reinstall Ubuntu.  The reason I switched to Ubuntu is I had so many problems with Windows locking up and needing to reinstall it every few months.  I never had problems with Dapper or Feisty.  It's pretty much started in Gutsy for me.  I have tried Pinging on my network without any luck.  I know something in the configs is changing because I am using a dual-boot system and the Windows boot is working.

Please HELP!!!

Thanks
Greg

---

### Post by SpaceTeddy on 2008-06-19
i sometimes have the problem that the driver for my internal network card is not loaded properly. Since i do not know what kind of network hardware you have, i need to know this first in oder to tell you the right command to test this. 
can you please run the following command:
```
lspci
```
and paste the output here. This will show all devices in your computer, including your network card. From there, i might be able to tell you a command to reload the config.

On the off chance that this is NOT a problem with the driver, but the configuration, please post the output of these commands:

```
ifconfig
cat /etc/network/interfaces
```

the first will show your currently active network cards, the second will show the configuration for the network card that is loaded when booting. 

hope we can figure this out :)

PS: i am usually not helping with hardware issues, and i am not really good at it. This just seems similar to problems i ran into the past.
So, if anyone else has an idea, **PLEASE POST IT**

---

### Post by flyinggreg on 2008-06-19
ok, here's the info requested:
```
golah@desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0c.0 Communication controller: Conexant HCF 56k Data/Fax/Voice Modem (Worldwide) (rev 08)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
02:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
golah@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:d6:bc:f7  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fed6:bcf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3106 (3.0 KB)  TX bytes:11344 (11.0 KB)
          Interrupt:24 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61676 (60.2 KB)  TX bytes:61676 (60.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:8c:59:74  
          inet6 addr: fe80::212:17ff:fe8c:5974/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:13076 (12.7 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:12:17:8c:59:74  
          inet addr:169.254.5.141  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-8C-59-74-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

golah@desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



iface wlan0 inet dhcp
wireless-key s:2432633612
wireless-essid 2WIRE704

auto wlan0

iface eth0 inet static
address 192.168.1.66
netmask 255.255.255.0
gateway 192.168.1.0

auto eth0

mapping hotplug       
script grep       
map usb0

iface usb0 inet static
address 192.168.0.200      
netmask 255.255.255.0      
broadcast 192.168.0.255
pre-up /etc/network/ipaq

#

```
To me, it looks like the eth0 is loaded and reporting.  FYI...I checked the network card and the cable looks connected (lights on) and the router looks ok also.

---

### Post by cfmunster on 2008-06-19
> **flyinggreg said:**
> I am a newb that needs some networking help.  I just ran an update on Hardy and now my networking connectivity is gone

I'm not a newb, but I have had the same exact problem in the last couple of days. Ever since I ran an update two or three days ago, my networking settings have gone haywire. I had a bridged interface set up a la the KVM community HOWTO page for virtual machine support. That stopped working completely. I reverted to dhcp on eth0, but the system is constantly deleting my nameserver settings and default gateway and leaving me with no routing. 

Ubuntu has been really good so far, especially compared to older Linux distros, but this is just ridiculous.

---

### Post by SpaceTeddy on 2008-06-20
mhm... this is indeed very strange. The interface should be there. Btw. is there a reason why both your networks are configured are statically ? Anyway, lets run some more tests.
first off, is your routing set correctly ? you can find that by typing 
```
route -n
```
also, check the nameservers, with:
```
cat /etc/resolv.conf
```

but i suspect they are find too...
besdies that, i only have one more idea before i am out... check your iptables setup please. Can you post the output of the following commands here:
```
iptables -L -vnx
iptables -L -vnx --table nat
```

if i cannot see anything there, i am as hopelessly lost as cfmunster.

let's pray a little and see if we can (still) figure this out...

---

### Post by cfmunster on 2008-06-20
Thanks for the reply. Here are the diagnostics. Worth noting- whenever I reboot, and perhaps when I go idle as well (because it just happened) I lose my default gateway and my nameserver settings and I have to add them back in manually. Right now I am using DHCP. Just for good measure I have added the dhclient output as well.

It's also worth noting that I have seen several other threads today that look like similar issues, one in particular where the user said his nameserver was getting wiped out after a reboot.

Thanks for any help or suggestions.


route -n 

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 vnet0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         169.254.2.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

```

cat /etc/resolv.conf

```

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   7191
#
### END INFO

nameserver 192.168.2.1

```

iptables -L -vnx

```

Chain INPUT (policy ACCEPT 116342 packets, 57271435 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     udp  --  vnet0  *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
       0        0 ACCEPT     tcp  --  vnet0  *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
       0        0 ACCEPT     udp  --  vnet0  *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 ACCEPT     tcp  --  vnet0  *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 

Chain FORWARD (policy ACCEPT 3 packets, 704 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      vnet0   0.0.0.0/0            192.168.122.0/24    state RELATED,ESTABLISHED 
       0        0 ACCEPT     all  --  vnet0  *       192.168.122.0/24     0.0.0.0/0           
       0        0 ACCEPT     all  --  vnet0  vnet0   0.0.0.0/0            0.0.0.0/0           
       0        0 REJECT     all  --  *      vnet0   0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
       0        0 REJECT     all  --  vnet0  *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT 118219 packets, 12984510 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```

iptables -L -vnx --table nat

```

Chain PREROUTING (policy ACCEPT 30 packets, 5106 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 3312 packets, 255702 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      39     6888 MASQUERADE  all  --  *      *       192.168.122.0/24     0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 3350 packets, 262542 bytes)
    pkts      bytes target     prot opt in     out     source               destination        

```


cat /etc/dhcp3/dhclient.conf:

```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
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

---

### Post by mamcgrath on 2008-06-20
> **flyinggreg said:**
> I am a newb that needs some networking help.  I just ran an update on Hardy and now my networking connectivity is gone!  It seems like every time I run a kernel update from the update manager, I lose eth0 connectivity.  In the past I have gotten so frustrated, I would just reinstall Ubuntu.  The reason I switched to Ubuntu is I had so many problems with Windows locking up and needing to reinstall it every few months.  I never had problems with Dapper or Feisty.  It's pretty much started in Gutsy for me.  I have tried Pinging on my network without any luck.  I know something in the configs is changing because I am using a dual-boot system and the Windows boot is working.

Please HELP!!!

Thanks
Greg

Networking is not really my thing but are you using the network-manager applet to manage your connections? If so, I think your /etc/network/interfaces file should be empty except for the first two lines.

auto lo
iface lo inet loopback

---

### Post by cfmunster on 2008-06-20
Hmm, definitely something funny going on. I was just browsing around and I lost connectivity. I had to re-add my nameserver and default gw again. This is becoming a serious hassle.

UPDATE: I switched back to bridged networking and that works, but I just lost my gw and nameserver, again. fyi I am adding them back in on the command line rather than through the network manager app.

---

### Post by flyinggreg on 2008-06-21
The other lines are for connecting to my handheld IPaq.  There never was an issue with those lines before the update.  I am going to check out my /etc/resolv.conf and see if my nameserver changed.

---

### Post by Midwest-Linux on 2008-06-21
I lost wireless after the "helpful" updates and still trying to resolve it. Seems that the mad wi fi.org site is down and cannot reinstall the wireless. No more updates for this laptop. Using Ubuntu 8.04.

---

### Post by SpaceTeddy on 2008-06-21
right-o... here we go (oh, that rhymes)

the most strange thing i notice here is your routing table... something is wrong here. I cannot pin down the source, but it should afaik not look like this.
Kernel IP routing table
> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 vnet0
[COLOR="Red"]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0[/COLOR]
[B]0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         169.254.2.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0[/B]


why do you have two different default gateways, and why is one of them inserted double ? Also, the 169.254 network is usually an autoconfigure network mask for network cards being turned on and NOT having received or set any configuration. this should not really happen.
So, here is what i am suggesting (i have **no idea** if this is going to work) - edit your /etc/network/interfaces and remove any and all entries on there except the loopback device. for me it looks like you have somehow configured an interface that is not supposed to be configured. The thing is, if the avahi daemon kicks in on a non-configured device, i would assume (yes, assume - i do NOT know this) that it would would set the default parameters for the default gateway as well as a broadcast dns server (or none). This would explain your symptoms... but again - i must stress this is a guess. 

besides that, i cannot really see anything wrong with your setup. Just as a sidenote - your iptables configuration is not effective as all the rules don't have a target and the default is on ACCEPT. so if you load them or not, it does not matter. The only rule that applies is the one in the POSTROUTING (which is also the only one that acctually saw some pakets)

now, lets hope my guess is lucky :)

just saw something more... eth0 has, according to your routing table, another subnet attached (check the red line) - where is that one coming from ? I'll do some research on the avahi daemon, as this would be my first guess...

---

### Post by flyinggreg on 2008-06-21
Well, I figured my issue out...I think...All I needed was to switch from Static to DHCP and now I am back connected..

---

### Post by cfmunster on 2008-06-21
> **SpaceTeddy said:**
> - edit your /etc/network/interfaces and remove any and all entries on there except the loopback device.

just saw something more... eth0 has, according to your routing table, another subnet attached (check the red line) - where is that one coming from ? I'll do some research on the avahi daemon, as this would be my first guess...

OK, did this and rebooted. eth0 got an IP address via DHCP, DNS is working. Here is my new routing table:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 vnet0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

The 169.254 route is coming from /etc/network/if-up.d/avahi-autoipd, it looks like. Here is the relevant code:

```

if [ -x /bin/ip ]; then
	# route already present?
	ip route show | grep -q '^169.254.0.0/16[[:space:]]' && exit 0

	/bin/ip route add 169.254.0.0/16 dev $IFACE metric 1000 scope link
elif [ -x /sbin/route ]; then
	# route already present?
	/sbin/route -n | egrep -q "^169.254.0.0[[:space:]]" && exit 0

	/sbin/route add -net 169.254.0.0 netmask 255.255.0.0 dev $IFACE metric 1000
fi

```

One other thing. ifconfig yields this:
```

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:9e:f8:21  
          inet addr:192.168.2.136  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe9e:f821/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21137 (20.6 KB)  TX bytes:27507 (26.8 KB)
          Interrupt:220 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:5 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1572 (1.5 KB)  TX bytes:134 (134.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23824 (23.2 KB)  TX bytes:23824 (23.2 KB)

vnet0     Link encap:Ethernet  HWaddr f2:dc:eb:7c:85:c6  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::f0dc:ebff:fe7c:85c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:10351 (10.1 KB)

```

I'm not sure what eth1 is. There is an entry for "Unknown USB Miscellaneous Interface" in the NetworkManager. Could be my XV6800 cell phone. I just ignore it.

This works fine for now. I'd prefer to have bridged networking and a static IP to work with my Windows VM on software development tasks, though. Any reason why that would not work? I have made fairly extensive edits in some areas of the OS in order to add bluetooth support (this one still doesn't work right), USB audio support, and webcam support. 

Thanks for the help.

---

### Post by rothbert on 2008-06-23
> **flyinggreg said:**
> Well, I figured my issue out...I think...All I needed was to switch from Static to DHCP and now I am back connected..

I have same issue and this may be the fix I need.
I am newb on all of this though, - how do you switch from Static to DHCP?

update:
Worked out how to do this and it hasn't solved the problem. The other ubuntu user in the house is having a look at the problem. We'll maybe start another thread when we've exhausted our resources :-) My hunch is still that it was caused by an update though so if there is a fix issued, would be happy to hear about it.

---

### Post by bwakkie on 2008-07-03
> **mamcgrath said:**
> Networking is not really my thing but are you using the network-manager applet to manage your connections? If so, I think your /etc/network/interfaces file should be empty except for the first two lines.

auto lo
iface lo inet loopback

That was the trick for me... i mixed a bit a while ago...

So open your favorite (g)vim and hit ```
:s%:^:#:g
``` to comment the whole interfaces file and uncomment the 2 lines mentioned in the quote

---

### Post by diafygi on 2008-08-29
> **cfmunster said:**
> I'm not sure what eth1 is. There is an entry for "Unknown USB Miscellaneous Interface" in the NetworkManager. Could be my XV6800 cell phone. I just ignore it.

I noticed when I plugged in my phone (AT&T 8525) to charge, the "Unknown USB Miscellaneous Interface" would appear on the list in Network Manager. Network Manager would then try to connect to the new wired interface and disconnect my wireless connection.

Of course, the USB interface isn't connected to the internet, so I would lose internet connectivity. To fix this, I would just go back and click the wireless network I wanted on the Network Manager list of available networks. Kind of annoying, but not anywhere near as complicated as what's described here.

---

