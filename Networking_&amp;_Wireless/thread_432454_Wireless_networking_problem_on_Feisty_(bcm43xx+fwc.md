---
title: "Wireless networking problem on Feisty (bcm43xx+fwcutter method)"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by renaudb on 2007-05-04
Hi,

I've look for messages on this forum and a lot of varied other places but I haven't found a solution yet. My problem is that Network-Manager sees WiFi networks as well as the signal strenght but I cannot connect to them (no error, it just doesn't connect).

After a fresh install of Ubuntu, my wireless card was detected but I could not see any networks. After I install bcm43xx-fwcutter and the default driver that is automatically downloaded by the package, and then typing "sudo modprobe bcm43xx", I see the networks in my surrounding.

I also commented out all the interfaces in /etc/networks/interfaces except LO, and then did  "sudo /etc/init.d/networks restart", which doesn't seem to change anything. 

ubuntu@ubuntu:~$ sudo uname -r
2.6.20-15-generic

ubuntu@ubuntu:~$ sudo lspci -v
08:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: AMBIT Microsystem Corp. TravelMate 2410
        Flags: bus master, fast devsel, latency 64, IRQ 21
        Memory at b0200000 (32-bit, non-prefetchable) [size=8K]

ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"drmckee1"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:3F:18:52:61   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ sudo ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:16:CF:9C:58:37  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:1120 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2712 (2.6 KiB)  TX bytes:16511 (16.1 KiB)
          Interrupt:11 Base address:0xc000 

The last results of the "dmesg" command is a bunch of:

[ 5124.260000] bcm43xx: IRQ_READY timeout
[ 5222.404000] bcm43xx: IRQ_READY timeout
[ 5249.064000] bcm43xx: IRQ_READY timeout
...

The network I am trying to connect to is secured by WPA, which is something I cannot change. I'm quite out of idea of what to try.

Now I am on a wired connection. I just tryed this command:

ubuntu@ubuntu:~$ sudo ifdown eth1 && sudo ifup eth1 && sudo dhclient
ifdown: interface eth1 not configured
Ignoring unknown interface eth1=eth1.
There is already a pid file /var/run/dhclient.pid with pid 11824
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Listening on LPF/eth1/00:16:cf:9c:58:37
Sending on   LPF/eth1/00:16:cf:9c:58:37
Listening on LPF/eth0/00:16:36:9c:2d:b0
Sending on   LPF/eth0/00:16:36:9c:2d:b0
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPREQUEST on eth0 to 255.255.255.255 port 67
receive_packet failed on eth1: Network is down
DHCPACK from 192.168.0.1
bound to 192.168.0.102 -- renewal in 239004 seconds.

Any body has any inspiration on how I could solve this problem? 
Thanks a lot!

---

### Post by Kobalt on 2007-05-04
I've never had any satisfying results, in terms of reliability and speed of connection, with the bcm43xx drivers. I advise you to use the ndiswrapper method : [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

