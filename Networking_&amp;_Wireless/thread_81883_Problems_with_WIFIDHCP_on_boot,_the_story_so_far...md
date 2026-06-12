---
title: "Problems with WIFI/DHCP on boot, the story so far..."
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by Dardie on 2005-10-25
I've been having strange problems with Ubuntu 5.10 final that I didn't have with Colony 3. The first problem is that Ubuntu doesn't boot up with network connectivity using DHCP. Following are my efforts to explore the problem to submit a really useful bug report or even a patch. Maybe some clever person has some suggestions?

On installation, ubuntu asks for ESSID & WEP password, connects, installs over the net. On first boot-up after install, it connects to the network, no problem. However from the second boot and subsequently, my wifi card (acx100 based) comes up WITHOUT an IP address and WITHOUT a default route. 

This is what my card looks like after bootup:

$ iwconfig wlan0
wlan0     IEEE 802.11b+  ESSID:"bearnet"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:04:E2:A8:97:2E   
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=90/100  Signal level=87/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:40:05:C5:E9:50  
          inet6 addr: fe80::240:5ff:fec5:e950/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1682 (1.6 KiB)  TX bytes:168 (168.0 b)
          Interrupt:16 Base address:0xa000 

$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

Trying to disable the card in network-admin causes network-admin to hang. Trying to run ifup or ifdown hangs those programs. I CAN use ifconfig and route add to set up an IP address and default route and then it works. If I set up a static address and gw rather than using DHCP, it will boot up OK with a working network.

I re-installed Breezy Badger 5.10 final again, with the same problem. I had no problems with with Colony 3, so I am guessing the problem was introduced between Colony 3 & final.

Looking more closely...

$ ps -ef | grep lan
root      6889     1  0 18:10 ?        00:00:00 /bin/sh /etc/hotplug/net.ifup wlan0=hotplug
root      6979  6889  0 18:10 ?        00:00:00 ifup wlan0=hotplug
dhcp      6987  6979  0 18:10 ?        00:00:00 dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/run/dhclient.wlan0.leases wlan0

So, it seems ifup never terminates. If I kill ifup (which also kills the calling script /etc/hotplug/net.ifup), then I can use ifup and ifdown. If I kill it and then run '/bin/sh /etc/hotplug/net.ifup wlan0=hotplug' manually, it works like a charm. So something about the boot environment, or maybe a race condition is causing ifup to hang.

$ /etc/hotplug/net.ifup wlan0=hotplug
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:40:05:c5:e9:50
Sending on   LPF/wlan0/00:40:05:c5:e9:50
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.0.0.2
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.4 -- renewal in 265481 seconds.
$

Then, I edited '/etc/hotplug/net.ifup' so that instead of calling
/sbin/ifup "$1" 2> /var/log/ifup.log
directly, it now does an 'ltrace -S' and logs the output:
ltrace -S /sbin/ifup "$1" 2> /var/log/ifup.log

Here is the (long) output from ltrace. I haven't got the source, so this is as far as I've gotten so far. Any suggestions are welcome...

---------

SYS_uname(0xbfd4e99c)                            = 0
SYS_brk(NULL)                                    = 0x804f000
SYS_mmap(0xbfd4e71c, 589, 0xb7f51838, 0xb7f51fc8, 4096) = 0xb7f3b000
SYS_access(0xb7f4ff3b, 0, 0xb7f51838, 0xb7f3b020, 0x804ebe4) = -2
SYS_mmap(0xbfd4e72c, 6200, 0xb7f51838, 0xb7f3b320, 8192) = 0xb7f39000
SYS_access(0xb7f4d5ad, 4, 0xb7f51838, -32, 0xb7f4d5ad) = -2
SYS_open("/etc/ld.so.cache", 0, 00)              = 3
SYS_fstat64(3, 0xbfd4e23c, 0xb7f51838, 0xb7f51fa8, 0) = 0
SYS_mmap(0xbfd4e21c, 0xbfd4e23c, 0xb7f51838, 3, 0xb7f51f30) = 0xb7f30000
SYS_close(3)                                     = 0
SYS_access(0xb7f4ff3b, 0, 0xb7f51838, 0xb7f51df3, 3) = -2
SYS_open("/lib/tls/i686/cmov/libc.so.6", 0, 00)  = 3
SYS_read(3, "\177ELF\001\001\001", 512)          = 512
SYS_fstat64(3, 0xbfd4e2b4, 0xb7f51838, 0xb7f51fa8, 0) = 0
SYS_mmap(0xbfd4e128, 3, 0xb7f51838, 0xbfd4e190, 0xbfd4e160) = 0xb7e02000
SYS_mmap(0xbfd4e128, 2, 0xb7f51838, 3, 0xbfd4e178) = 0xb7f2a000
SYS_mmap(0xbfd4e128, 0, 0xb7f51838, 0xb7f2e000, 0xbfd4e178) = 0xb7f2e000
SYS_close(3)                                     = 0
SYS_mmap(0xbfd4e764, 520, 0xb7f51838, 0xb7f3afe8, 4096) = 0xb7e01000
SYS_set_thread_area(0xbfd4e928, 0xb7e01000, 64, 0xb7f51838, 0xb7f51a20) = 0
SYS_munmap(0xb7f30000, 36568)                    = 0
__libc_start_main(0x8048fe0, 2, 0xbfd4ebe4, 0x804c554, 0x804c5a5 <unfinished ...>
memcpy(0xbfd4e9f0, "6\307\004\b", 176)           = 0xbfd4e9f0
fcntl(0, 1, 176, 0x756e694c, 120 <unfinished ...>
SYS_fcntl64(0, 1, 176, 176, 0xb7f2c0dc)          = 0
<... fcntl resumed> )                            = 0
fcntl(1, 1, 176, 0x756e694c, 120 <unfinished ...>
SYS_fcntl64(1, 1, 176, 176, 0xb7f2c0dc)          = 0
<... fcntl resumed> )                            = 0
fcntl(2, 1, 176, 0x756e694c, 120 <unfinished ...>
SYS_fcntl64(2, 1, 176, 176, 0xb7f2c0dc)          = 0
<... fcntl resumed> )                            = 0
strrchr("/sbin/ifup", '/')                       = "/ifup"
getopt_long(2, 0xbfd4ebe4, "e:s:i:hVvna", 0xbfd4e9f0, NULL) = -1
malloc(12 <unfinished ...>
SYS_brk(NULL)                                    = 0x804f000
SYS_brk(0x8070000)                               = 0x8070000
<... malloc resumed> )                           = 0x804f008
fopen("/etc/network/interfaces", "r" <unfinished ...>
SYS_open("/etc/network/interfaces", 0, 0666)     = 3
<... fopen resumed> )                            = 0x804f018
realloc(NULL, 80)                                = 0x804f180
fgets( <unfinished ...>
SYS_fstat64(3, 0xbfd4e6ac, 0xb7f2c0dc, 0x804f018, 8192) = 0
SYS_mmap2(0, 4096, 3, 34, -1)                    = 0xb7f38000
SYS_read(3, "# This file describes the networ"..., 4096) = 588
<... fgets resumed> "# This file describes the networ"..., 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 70, 0x8048668, 0x804f018) = 0x804f180
fgets("# and how to activate them. For "..., 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 69, 0x8048668, 0x804f018) = 0x804f180
fgets("\n", 80, 0x804f018)                       = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 1, 0x8048668, 0x804f018) = 0x804f180
fgets("# The loopback network interface"..., 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 33, 0x8048668, 0x804f018) = 0x804f180
fgets("auto lo\n", 80, 0x804f018)                = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 8, 0x8048668, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
malloc(20)                                       = 0x804f1d8
__strdup(0x804c769, 80, 0xb7e018c4, 7, 0x804f008) = 0x804f1f0
__ctype_b_loc()                                  = 0xb7e018c4
realloc(NULL, 4)                                 = 0x804f200
__strdup(0xbfd4e92c, 4, 0xbfd4e7f8, 0x804ae01, 0x804c769) = 0x804f210
fgets("iface lo inet loopback\n", 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 23, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
malloc(36)                                       = 0x804f220
__ctype_b_loc()                                  = 0xb7e018c4
__ctype_b_loc()                                  = 0xb7e018c4
__ctype_b_loc()                                  = 0xb7e018c4
__strdup(0xbfd4e8dc, 0x804f180, 23, 0xbfd4e92c, 0x804f018) = 0x804f248
strcmp("inet", "inet")                           = 0
strcmp("wvdial", "loopback")                     = 1
strcmp("manual", "loopback")                     = 1
strcmp("ppp", "loopback")                        = 1
strcmp("static", "loopback")                     = 1
strcmp("bootp", "loopback")                      = -1
strcmp("dhcp", "loopback")                       = -1
strcmp("loopback", "loopback")                   = 0
fgets("\n", 80, 0x804f018)                       = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 1, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("# This is a list of hotpluggable"..., 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 53, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("# They will be activated automat"..., 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 65, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("mapping hotplug\n", 80, 0x804f018)        = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 16, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
malloc(32)                                       = 0x804f258
__ctype_b_loc()                                  = 0xb7e018c4
realloc(NULL, 4)                                 = 0x804f280
__strdup(0xbfd4e92c, 4, 16, 0xbfd4e92c, 0x804f018) = 0x804f290
fgets("\tscript grep\n", 80, 0x804f018)          = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f181, 12, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
__strdup(0x804f187, 0x804f181, 12, 0xbfd4e92c, 0x804f018) = 0x804f2a0
fgets("\tmap wlan0\n", 80, 0x804f018)            = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f181, 10, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
realloc(NULL, 4)                                 = 0x804f2b0
__strdup(0x804f184, 4, 10, 0xbfd4e92c, 0x804f018) = 0x804f2c0
fgets("\n", 80, 0x804f018)                       = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 1, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("# The primary network interface\n", 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 32, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("iface wlan0 inet dhcp\n", 80, 0x804f018)  = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 22, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
malloc(36)                                       = 0x804f2d0
__ctype_b_loc()                                  = 0xb7e018c4
__ctype_b_loc()                                  = 0xb7e018c4
__ctype_b_loc()                                  = 0xb7e018c4
__strdup(0xbfd4e8dc, 0x804f180, 22, 0xbfd4e92c, 0x804f018) = 0x804f2f8
strcmp("inet", "inet")                           = 0
strcmp("wvdial", "dhcp")                         = 1
strcmp("manual", "dhcp")                         = 1
strcmp("ppp", "dhcp")                            = 1
strcmp("static", "dhcp")                         = 1
strcmp("bootp", "dhcp")                          = -1
strcmp("dhcp", "dhcp")                           = 0
strcmp("lo", "wlan0")                            = -1
fgets("\t# wireless-* options are implem"..., 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f181, 67, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("\twireless-mode managed\n", 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f181, 22, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
realloc(NULL, 80)                                = 0x804f308
__strdup(0xbfd4e92c, 80, 22, 0xbfd4e92c, 0x804f018) = 0x804f360
__strdup(0x804f18e, 80, 22, 0xbfd4e92c, 0x804f018) = 0x804f378
fgets("\twireless-essid bearnet\n", 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f181, 23, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
strcmp("wireless-mode", "wireless-essid")        = 1
__strdup(0xbfd4e92c, 0xbfd4e92c, 23, 0xbfd4e92c, 0x804f018) = 0x804f388
__strdup(0x804f18f, 0xbfd4e92c, 23, 0xbfd4e92c, 0x804f018) = 0x804f3a0
fgets("\twireless-key1 s:XXXXX\n", 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f181, 25, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
strcmp("wireless-mode", "wireless-key1")         = 1
strcmp("wireless-essid", "wireless-key1")        = -1
__strdup(0xbfd4e92c, 0xbfd4e92c, 25, 0xbfd4e92c, 0x804f018) = 0x804f3b0
__strdup(0x804f18e, 0xbfd4e92c, 25, 0xbfd4e92c, 0x804f018) = 0x804f3c8
fgets("\twireless-key s:XXXXX\n", 80, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f181, 24, 0xbfd4e92c, 0x804f018) = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
strcmp("wireless-mode", "wireless-key")          = 1
strcmp("wireless-essid", "wireless-key")         = -1
strcmp("wireless-key1", "wireless-key")          = 1
__strdup(0xbfd4e92c, 0xbfd4e92c, 24, 0xbfd4e92c, 0x804f018) = 0x804f3d8
__strdup(0x804f18d, 0xbfd4e92c, 24, 0xbfd4e92c, 0x804f018) = 0x804f3f0
fgets("\n", 80, 0x804f018)                       = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 1, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("\n", 80, 0x804f018)                       = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 1, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("\n", 80, 0x804f018)                       = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 1, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets("\n", 80, 0x804f018)                       = 0x804f180
__ctype_b_loc()                                  = 0xb7e018c4
memmove(0x804f180, 0x804f180, 1, 0xbfd4e92c, 0x804f018) = 0x804f180
fgets( <unfinished ...>
SYS_read(3, "", 4096)                            = 0
<... fgets resumed> "", 80, 0x804f018)           = NULL
ferror(0x804f018)                                = 0
ferror(0x804f018)                                = 0
fclose(0x804f018 <unfinished ...>
SYS_close(3)                                     = 0
SYS_munmap(0xb7f38000, 4096)                     = 0
<... fclose resumed> )                           = 0
fopen("/etc/network/run/ifstate", "a+" <unfinished ...>
SYS_open("/etc/network/run/ifstate", 1090, 0666) = 3
<... fopen resumed> )                            = 0x804f018
fileno(0x804f018)                                = 3
fcntl(3, 1, 0x804c70f, 0xbfd4e9f0, 0 <unfinished ...>
SYS_fcntl64(3, 1, 0x804c70f, 0x804c70f, 0xb7f2c0dc) = 0
<... fcntl resumed> )                            = 0
fileno(0x804f018)                                = 3
fcntl(3, 2, 1, 0xbfd4e9f0, 0 <unfinished ...>
SYS_fcntl64(3, 2, 1, 1, 0xb7f2c0dc)              = 0
<... fcntl resumed> )                            = 0
fileno(0x804f018)                                = 3
fcntl(3, 7, 0xbfd4eaa0, 0xbfd4e9f0, 0 <unfinished ...>
SYS_fcntl64(3, 7, 0xbfd4eaa0, 0xbfd4eaa0, 0xb7f2c0dc

---

### Post by Dardie on 2005-10-30
Thanks to comments in [another thread]("http://untuforums.org/showthread.php?t=77380") my problem is now fixed... the solution was simply to add EITHER of the lines 'auto wlan0' OR 'allow-hotplug wlan0' into my /etc/network/interfaces.

Based on about 5 bootups each, my system boots successfully with DHCP 100% of the time with either of these, and maybe 5% - 20% of the time (ie. DHCP does not get IP address or default route) without.

I also placed a similar comment in [the other thread]("http://untuforums.org/showthread.php?t=77380") for completeness...

Happy happy joy joy! (and thanks Tor)

---

### Post by Dardie on 2005-10-30
Just checked another computer still running hoary, and it had the line 'auto eth1' in /etc/network/interfaces.

I'm considering filing this as a bug, but it would be nice to get some feedback to know if this was affecting anybody else...it  seems as though lots of people are having (somewhat poorly defined) problems with wifi under breezy.

---

