---
title: "Perplexed: Networking problem (no connectivity via Ethernet)"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by DigitDuke on 2006-10-28
Now's the time to earn karma points.  I installed Ubuntu Edgy yesterday only to be thrilled by Ubuntu for the first time.  What a great user interface with a wonderful collection of useful applications.

Unfortunately, it was too good to be true.  I've twice attempted to install Ubuntu on this particular computer, but those were Dapper server editions.

When I had first installed the system I went on the Internet and everything seemed slow.  I looked around on the boards and I found a much-appreciated thread on how to turn off IPv6.  After that, the Internet was great (this was last night).

I shut down the computer and went to sleep thinking how wonderful Ubuntu was, thinking that life was wonderful.

When I turned the computer on this morning, the Internet didn't work.  I began playing with the settings, disabling this and that, and at this point I believe I tried most possible configurations that seem obvious to solve this problem.

However embarassing it may seem, I am now posting about what seems to be one of Ubuntu's most repetitious problem.  At this point I'm unsure whether to blame my network card, the router or Ubuntu, but I'm sure as hell that something isn't working right.  But basically, there's no connection at all - no responses to local pings and seemingly no assigned network address.

So I reinstalled Ubuntu.  The only change I've made since I set up the system (besides the screen resolution) is I added my router address as DNS.  I find it interesting though, that yesterday it automatically entered the router IP (192.168.1.254) into the DNS, but now I had to add it manually.  It's as if yesterday it had some connectivity it didn't have before.

So nothing is changed apart from that in the original installation, and nothing is working.

Here's the output of various command on my Ubuntu system:

Command: **lshw** (network part only)
> 
        *-network
             description: Ethernet interface
             product: 3c905C-TX/TX-M [Tornado]
             vendor: 3Com Corporation
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: 74
             serial: 00:50:da:2d:ee:e4
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=3c59x multicast=yes
             resources: ioport:1000-107f iomemory:41200000-4120007f irq:10


Command: **lspci**
> 
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 22)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
00:0a.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 13)
00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:14.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)


Command: **cat /etc/network/interfaces**
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



Command: **sudo /etc/init.d/networking restart**
> 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4032
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:da:2d:ee:e4
Sending on   LPF/eth0/00:50:da:2d:ee:e4
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:da:2d:ee:e4
Sending on   LPF/eth0/00:50:da:2d:ee:e4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]



Command: **ifconfig**
> 
eth0      Link encap:Ethernet  HWaddr 00:50:DA:2D:EE:E4  
          inet6 addr: fe80::250:daff:fe2d:eee4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:857 errors:0 dropped:0 overruns:1 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70379 (68.7 KiB)  TX bytes:9144 (8.9 KiB)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)




I decided to do a little comparison, and I plugged the Ethernet cable into my Mac (Macs run partially on FreeBSD, so I'm able to do a comparison).  For the record, I've checked to see that this is not a cable problem (obviously, since it works with my Mac).

Here's what I get from **ifconfig** (irrelevant parts removed):

> 
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        inet 192.168.2.1 netmask 0xffffff00 broadcast 192.168.2.255
        inet6 fe80::216:cbff:fe8a:23b7%en0 prefixlen 64 scopeid 0x4 
        inet 192.168.1.7 netmask 0xffffff00 broadcast 192.168.1.255
        ether 00:16:cb:8a:23:b7 
        media: autoselect (100baseTX <full-duplex>) status: active
        supported media: autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 10baseT/UTP <full-duplex,flow-control> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback> 100baseTX <full-duplex,flow-control> 1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 1000baseT <full-duplex,flow-control> none


I feel like I have exhausted all options that are known to me, so I resort to making one more of threads begging for help so I can reach a conclusion in this matter.  It's noteworthy that I have full faith in that whoever helps me solve this will be rewarded with the greatest amount of karma and unlimited amounts of non-sexual love.

I will provide you with whatever information possible as fast as possible (and I won't abandon it in the middle saying, "it worked!11 bye!").

Whoever takes the time to help me on this (hopefully to help some desperate solution-seeker in the future too), I will be ever so grateful for them sharing their time.

Regards,
Friðrik Már

---

### Post by lloyd_b on 2006-10-28
There is a problem with DHCP.  DHCP is a protocol that automatically obtains IP addresses, nameserver addresses, and other related info.  With DCHP broken, you ethernet card is not being given an address (and the nameserver is not being set in "resolv.conf".  

Now for the $64 question: why isn't it working.  It's *trying*:

> DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.

These indicate that a messages are being sent out of your ethernet card, asking for somebody to PLEASE give it an IP address.  Unfortunately, nobody is answering...

Was the ethernet cable connected when you ran this test?  Most likely your router is also your DHCP server, and if the cable isn't connected then you'd see results like this.

Also, some further information that might help sort things out would be the contents of "/etc/dhcp3/dhclient.conf".  This is the configuration file that's used by the DHCP programs.

Lloyd B.

---

### Post by DigitDuke on 2006-10-28
Because I made some changes to the system that I couldn't revert, I decided to reformat.  I'll check the **/etc/dhcp3/dhclient.conf** after the jump.

The ethernet cable, however, is definitely connected because I tried two cabled and tested the other with my Mac, so it definitely works.  Also, there's a glowing green light below the number "100".

---

### Post by lloyd_b on 2006-10-28
I strongly suspect this problem is strictly software-related, so if you're doing a reinstall it'll probably take care of things.

Lloyd B.

---

### Post by DigitDuke on 2006-10-28
Reinstalling the blessed OS didn't solve my problem.  Resorting to a static address, however, did.  What I did was apply the following configuration.  For people that have this problem in the future, the /etc/network/interfaces file should be changed to the following:

```
auto eth0
iface eth0 inet static
address 192.168.1.13
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.254
```

**address:** The IP address you would like to assign your computer on the local network.  This must be within your router's range of allowed IP addresses (usually configurable via the administrative interface).  Also make sure that this address isn't already in use by another computer on your network.
**netmask:** This seems to me to be 255.255.255.0 by default.
**broadcast** and **network:** From some good help I got from two fellows in [#ubuntu on FreeNode](irc://irc.freenode.net/ubuntu), apparently the *broadcast* address is the same as the *address* field, but with the last octet replaced with 255, and *network* is the same except replaced with 0.
**gateway:** In the case of having a router, gateway is seemingly the IP address of the router.

I want to thank you, Lloyd, to take the time to help me with this.  In case you have curious, or if you think you have a different suggestion that may solve this problem, here is the output of [FONT="Courier New"]/etc/dhcp3/dhclient.conf[/FONT]:

> 
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


---

