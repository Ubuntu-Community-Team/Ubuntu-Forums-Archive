---
title: "Suddenly Gutsy wifi stops on T60, but liveCD works!"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by bliffle on 2007-12-02
Gutsy installed like a dream on my Thinkpad T60 and it's been working fine for at least a month, but this morning the wireless stopped working. Haven't changed anything, but it just won't go. Rebooted a couple times, still no go. But when I booted from the Gutsy LiveCD it worked just fine.

When I bootup from the HDD the little wireless antenna icon comes on solid for a second, then spends a few seconds flickering, then comes on solid again for a second. repeats this cycle endlessly. With the LiveCD it stays on solid.

So I'm convinced it's a software problem, not a hardware problem. Meanwhile, the other 3 thinkpads running Gutsy are just fine.

I went through a whole bunch of tutorials and debugging sessions on 'ubuntuforums', but all I really did was accumulate a bunch of data, most of which I have no idea what to do with.

Has anyone seen this before?

Here's a bunch o' data I accumulated:

```

**lspci**
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:18:DE:C7:C2:D8  
          inet6 addr: fe80::218:deff:fec7:c2d8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:91 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17976 (17.5 KB)  TX bytes:27757 (27.1 KB)
          Interrupt:21 Base address:0xe000 Memory:edf00000-edf00fff 

eth0:avah Link encap:Ethernet  HWaddr 00:18:DE:C7:C2:D8  
          inet addr:169.254.11.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xe000 Memory:edf00000-edf00fff 

**iwlist scan**
...
eth0      Scan completed :
          Cell 01 - Address: 00:14:6C:FA:99:76
                    ESSID:"Netgear541JH"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-56 dBm  Noise level=-56 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 372ms ago

**lshw -C network**
...
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:de:c7:c2:d8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated

**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:18:DE:C7:C2:D8  
          inet6 addr: fe80::218:deff:fec7:c2d8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:446 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67410 (65.8 KB)  TX bytes:112128 (109.5 KB)
          Interrupt:21 Base address:0xe000 Memory:edf00000-edf00fff 

eth0:avah Link encap:Ethernet  HWaddr 00:18:DE:C7:C2:D8  
          inet addr:169.254.11.106  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xe000 Memory:edf00000-edf00fff 

[B]sudo dhclient
[/B]Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:de:c7:c2:d8
Sending on   LPF/eth0/00:18:de:c7:c2:d8
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

**uname -r**
2.6.22-14-generic

**cat /etc/resolv.conf**
nameserver 192.168.1.1

**ls -l /var/lib/dhcp3/**
-rw-r--r-- 1 dhcp root 954 2007-12-02 08:42 dhclient.eth0.leases
-rw-r--r-- 1 dhcp root   0 2007-12-02 08:51 dhclient.leases

**ls -l /etc/dhcp3/**
-rw-r--r-- 1 root root 1558 2007-09-07 08:31 dhclient.conf
drwxr-xr-x 2 root root 4096 2007-11-17 13:44 dhclient-enter-hooks.d
drwxr-xr-x 2 root root 4096 2007-10-15 16:28 dhclient-exit-hooks.d

**cat /etc/dhcp3/dhclient.conf**
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

### Post by bliffle on 2007-12-03
I plugged an Airlink101 into the PCMCIA and it started working! But there is no way I can get the builtin working except to boot the LiveCD 7.10.

The builtin also doesn't work with XP, either.

I did an 'iwconfig' :

```

sudo iwconfig eth0 essid Netgear541JH
iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Netgear541JH"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:FA:99:76   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-60 dBm  Noise level=-96 dBm
          Rx invalid nwid:10007  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      unassociated  ESSID:"Netgear541JH" 
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:6C:FA:99:76   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:603   Missed beacon:0


```

---

### Post by bliffle on 2007-12-03
Now I tried an Airlink101 in the PCMCIA slot and it works!

But the builtin doesn't work on XP either.

So the only software that runs the builtin wireless (now) is ubuntu 7.10 liveCD.

---

### Post by bliffle on 2007-12-04
The windows T60 guys say there's a new Intel driver for the 3945abg wireless that installs under Vista, so I'm trying to find that somewhere on the Lenovo site. Does ubuntu subsume the Intel driver somehow? Perhaps thru some version of ndiswrapper? Or does it have a complete homebrew version?

Anyway, that wireless seems not too work under XP anymore, although it was working fine a week ago under both Gutsy and XP. Now it only works under the Gutsy liveCD.

---

### Post by bliffle on 2007-12-05
Problem solved! (slaps forehead with hand)

I just had to set the "Roaming" checkbox in the properties for the wireless connection. Somehow, I don't remember when or why, the actual network AP name was entered.

---

