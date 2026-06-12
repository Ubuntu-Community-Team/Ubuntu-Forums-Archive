---
title: "cannot connect wired connection"
date: 2017-01-26
forum: Networking &amp; Wireless
---

### Post by jgw on 2017-01-26
I was losing my connections randomly and often (again).  I then purged and re-installed the network manager (after installing I was advised that the network manager had been installed).  I was unable to connect.  I ran some reports which can be found at: [http://pastebin.com/t6HcwhdF](http://pastebin.com/t6HcwhdF)

I am also missing my network item in the top bar.  When I tried to get that running (nm-applet) I was told it didn't exist.  I then thought that I had dependencies so I downloaded a pile of .deb files which I have done nothing with (I think I have already done enough without a bit of guidance <G>)  I have also tried dhclient eth1 to no avail.  Oh, I also rebooted after the network manager install.  

Here is what my /etc/network/interfaces looks like:
#interfaces[5] file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

and I added:
#eth1
auto eth1
iface eth1 inet dhcp
(then I rebooted and it changed nothing)

ifup got me:
greg@greg-movies:~$ sudo ifup eth1
[sudo] password for greg: 
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/fc:aa:14:8c:6b:c7
Sending on   LPF/eth1/fc:aa:14:8c:6b:c7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0xaa53ba00)
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0xaa53ba00)
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11 (xid=0xaa53ba00)
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13 (xid=0xaa53ba00)
(etc)

So, basically, I am shut down - thoughts?  I will keep on doing stuff and adding to this until somebody, hopefully, gives me some thoughts)

Thank you...................

---

### Post by chili555 on 2017-01-26
I assume the entries you listed in /etc/network/interfaces are still there. Please refrain from randomly changing things as it is not at all useful to suggest a fix and find out that you, on a whim, removed or revamped a file that we need.> I will keep on doing stuff and adding to this until somebody, hopefully, gives me some thoughtsHere is a thought: stop now.

Your driver, r8169, has some difficulty with autonegotiation. Let's see if we can coax it to life:```
sudo ethtool -s eth1 autoneg off speed 100
sudo ifdown eth1 && sudo eth1 -v up
```Please post the result.

---

### Post by jgw on 2017-01-26
Thank you for the reply!  

I never am sure I will get a reply so I keep on going (and getting myself into a bigger and bigger mess)  Anyway, I am truly grateful for your appearance!! (and will stop))
Below is the result of your suggestion.  I also got the nm-applet back working (moved /etc/xdg/autostart/nm-applet.desktop to ~/.config/autostart and checked the execution box)
in network connections I have two under ethernet; wired connection 1 and eth1 (they are both the same except the wired connection 1 ipv4 setttings method sayhs automatic (dhcp) addresses only whilst the other says automatic (dhcp).  when I do "sudo dhclient eth1" it just hangs.

reg@greg-movies:~$ sudo ethtool -s eth1 autoneg off speed 100
greg@greg-movies:~$ sudo ifdown eth1 && sudo eth1 -v up
RTNETLINK answers: No such process
Killed old client process
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/fc:aa:14:8c:6b:c7
Sending on   LPF/eth1/fc:aa:14:8c:6b:c7
Sending on   Socket/fallback
sudo: eth1: command not found


I should add that I have downloaded the following files (have done nothing with them (except for one)):
/media/greg/8gb-linux/network-manager_1.1.93-0ubuntu4_amd64.deb
/media/greg/8gb-linux/network-manager_1.2.2-0ubuntu0.16.04.3_amd64.deb
/media/greg/8gb-linux/network-manager-dev_1.2.2-0ubuntu0.16.04.3_amd64.deb
/media/greg/8gb-linux/network-manager-gnome_1.1.93-1ubuntu1_amd64.deb
/media/greg/8gb-linux/network-manager-gnome_1.2.0-0ubuntu0.16.04.4_amd64.deb*  (installed this one (forgot))
/media/greg/8gb-linux/network-manager-iodine_0.0.5-1ubuntu1_amd64.deb
/media/greg/8gb-linux/network-manager-iodine-gnome_0.0.5-1ubuntu1_amd64.deb
/media/greg/8gb-linux/network-manager-openconnect_1.2.0-0ubuntu0.16.04.1_amd64.deb
/media/greg/8gb-linux/network-manager-openconnect-gnome_1.2.0-0ubuntu0.16.04.1_amd64.deb
/media/greg/8gb-linux/network-manager-openvpn_1.1.93-1ubuntu1_amd64.deb
/media/greg/8gb-linux/network-manager-openvpn-gnome_1.1.93-1ubuntu1_amd64.deb
/media/greg/8gb-linux/network-manager-pptp_1.1.93-1ubuntu1_amd64.deb
/media/greg/8gb-linux/network-manager-pptp-gnome_1.1.93-1ubuntu1_amd64.deb
/media/greg/8gb-linux/network-manager-ssh_1.2.0-0ubuntu0.16.04.1_amd64.deb
/media/greg/8gb-linux/network-manager-ssh-gnome_1.2.0-0ubuntu0.16.04.1_amd64.deb

The file I used to install the network manager was:
network-manager_1.2.2.-0ubuntu0.16.04.3_amd64.deb

---

### Post by chili555 on 2017-01-26
> sudo: eth1: command not found*Old Chili pauses to wipe a few layers of grime off his glasses*

Sorry for my mis-step. I should have said:```
sudo ifdown eth1 && sudo ifup -v eth1
```My apologies. Please try again and post the hopefully informative result.

---

### Post by jgw on 2017-01-26
curious, how old is "Old Chili?" (just being nosy - I have a few years myself <G>)

actually you did tell me to do that but I did it again and got:
greg@greg-movies:~$ sudo ifdown eth1 && sudo ifup -v eth1
[sudo] password for greg: 
Killed old client process
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/fc:aa:14:8c:6b:c7
Sending on   LPF/eth1/fc:aa:14:8c:6b:c7
Sending on   Socket/fallback
Configuring interface eth1=eth1 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

/sbin/dhclient -1 -v -pf /run/dhclient.eth1.pid -lf /var/lib/dhcp/dhclient.eth1.leases -I -df /var/lib/dhcp/dhclient6.eth1.leases eth1 	
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/fc:aa:14:8c:6b:c7
Sending on   LPF/eth1/fc:aa:14:8c:6b:c7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x273656b)
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0x273656b)
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19 (xid=0x273656b)

A bunch more like this and: no DHCPOFFERS received
no working leases in persistent database - sleeping
/bin/run-parts --exit-on-error  --verbose /etc/network/if-up.d
run parts: executing /etc/network/if-up.d/ (then more lrun parts lines for the following):
000resolvconf
avajo-autopd
avahi-aemon
ethtool
ntpdate
openvpn
upstart

I think I may have left off this the last time around.  When I grabbed it I thought it had finished, it had not (sorry)
the nm-applet tells me that (greyed)
ethernet networks
device not managed

networks tells me that wired is unmanaged

---

### Post by chili555 on 2017-01-26
Old Chili's exact age is a carefully guarded secret. I declined to tell even my great-grandson when he asked. I just told him, "Really old!"

Please verify that the autoneg step took effect:```
sudo ethtool eth1
```Why is this eth1? Please let us see:```
ifconfig -a
```Do you otherwise have internet access if we need to download and install something?

---

### Post by jgw on 2017-01-26
great grand kids!  Good for you (I have a few of them too! <G>)

greg@greg-movies:~$ sudo ethtool eth1
[sudo] password for greg: 
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no
greg@greg-movies:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr fc:aa:14:8c:6b:c7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:337806 (337.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:498918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:133050553 (133.0 MB)  TX bytes:133050553 (133.0 MB)

I have access to the net (another computer)

I decided to put a wifi usb receiver onto this machine to see if I could get wifi.  I am now hooked up wirelessly!  I will make another run at this in a bit.  since I have  a connection I think I will goto synaptic and check stuff.

synaptic told me I had the following network files installed:
libkio5 library
libnm-glib-pbn 1.2.2.
libnm-glib4
libnm-util2
libproxy1-plugin0.4.11
network-manager 1.2.2.Oubuntu
network-manager 1.2.0.Oubuntu

it is also checking dependencies and upgrading all that need it.
I also ran a check on the wireless which I can post on the net if you want.

---

### Post by chili555 on 2017-01-27
> [COLOR="#FF0000"]Auto-negotiation: on[/COLOR]
Supports Wake-on: pumbg
Wake-on: g
Current message level: 0x00000033 (51)
drv probe ifdown ifup
Link detected: noAutoneg didn't set so let's try a bit harder:```
sudo ethtool -s eth1 autoneg off speed 100
sudo ethtool eth1
```Now is it off? If it is, as we hope, try again:```
sudo ifdown eth1 && sudo ifup -v eth1
```Does it connect?

Some of my colleagues swear by the package r8168-dkms, however, it won't build: [https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1487605](https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1487605) Comment #4 says:> Current available work-around: Install .deb package from Xenial or Yakkety. Upstream version 8.041 fixes this issue.However, 8.041 is the subject of its own 'won't build' bug: [https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1635824](https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1635824) Therefor, even though you might read otherwise on ye olde interwebs, this is a dead end.

We either get autoneg: off and connect or we give up and stick with wireless.> great grand kids! Good for you (I have a few of them too! <G>)
I see posts here and elsewhere that play the age card; something like, "I'm old, almost 58 years old, and I'm not able to understand all this as well as I once did." I chuckle and wonder if they'll still be feeling sorry for themselves when they're *really* old like me!

---

### Post by jgw on 2017-01-27
Thanks for the reply....

I have a friend who assured me that you are not in the elder class until you are over 80.  I believe that one as I am close to forgetting my own damned name! <G>  I can remember a time when I could actually put a 2000 solder joint motherboard together (that was for an altair - sold it several years ago for around 500.00 and now they are getting a LOT more for those).  Should have held on (like I do stocks, until they are almost worthless because I am not paying attention <G>)

Anyway, I am currently catching up on my downloads with wifi and then I will return to my wired.  I neglected to say that, for the wired, I am use a tp-link av500 which had been doing great.  I also hook up my laptop to check the connection and it was dandy.  When I start over I think I will replace the existing cable just in case.  I have been finding that, for absolutely no reason I can think of, cables tend to start to fail over time.  I just replaced a couple of hdmi cables and the results told me I did the right thing.  I used to think that cable ends just needed to be disconnected and connected again to fix problems but, I guess, I was at least partially wrong.

I will get back to this in a day or so.  This one is hooked to our main tv so, when I dink with it, my wife tends to pass by with signs of distress, ie. "he is going to screw it up again!" <G>

Later.....

---

### Post by chili555 on 2017-01-27
> cables tend to start to fail over time. Indeed. My wife's ethernet wouldn't do the expected speed until I replaced the cable. Now, it says:```
Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	[COLOR="#FF0000"]Speed: 1000Mb/s[/COLOR]
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
```Woohoo!

---

### Post by jgw on 2017-01-28
Ok, I swapped out the cable and it came right up!  Here is the result of some tests:
greg@greg-movies:~$ sudo lshw -C network
[sudo] password for greg: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 0c
       serial: fc:aa:14:8c:6b:c7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:29 ioport:d000(size=256) memory:fe100000-fe100fff memory:fa100000-fa103fff
greg@greg-movies:~$ sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

I think this comes under the heading of a)bad cable or b)mysterious stuff.  In other words I am back up and running.  Thank you for your help, this is the second time you have bailed me out - I am grateful for your time and help!  I am going to mark this one as solved <g>
One last thought.  I ran both the wired and the wifi - the wifi is faster by about 05% - thought I would throw that in <G>

---

### Post by chili555 on 2017-01-28
Glad it's working by whatever means! Have fun!

---

