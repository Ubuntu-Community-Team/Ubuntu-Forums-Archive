---
title: "Unable to connect/Server not found"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by RichardSchollar on 2006-08-05
Hi Everyone

Some background:  UK-based, use a dual boot PC with Windows XP Pro and Ubuntu 6.06 (very recent entrant to the Linux world!).  ISP is AOL (believe it or not, best option where I live), using an ADSL broaband connection.

I recently purchased a ZOOM X5 wired router to connect in the hope that I would be able to connect to the internet via Ubuntu (I stupidly did not check that the router was Ubuntu-compatible first).

Connecting via XP was easy, router works perfectly.

Via Ubunut, however, I am completely unable to connect.  If I go System>Administration>Networking I can see my eth0 is active, but I can't connect (I am opening up Firefox and typing in IP addresses here).

My XP details via ipconfig/all are:

Windows IP Configuration



        Host Name . . . . . . . . . . . . : home

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller

        Physical Address. . . . . . . . . : 00-01-6C-E6-AD-39

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 10.0.0.4

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 10.0.0.2

        DHCP Server . . . . . . . . . . . : 10.0.0.2

        DNS Servers . . . . . . . . . . . : 10.0.0.2

        Lease Obtained. . . . . . . . . . : 05 August 2006 10:30:10

        Lease Expires . . . . . . . . . . : 04 September 2006 10:30:10



PPP adapter {CE5C26D2-486A-4378-91CC-2137DDF58B07}:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface

        Physical Address. . . . . . . . . : 00-53-45-00-00-00

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 172.207.61.163

        Subnet Mask . . . . . . . . . . . : 255.255.255.255

        Default Gateway . . . . . . . . . : 

        DNS Servers . . . . . . . . . . . : 205.188.146.145

        NetBIOS over Tcpip. . . . . . . . : Disabled



I am a complete noob when it comes to Linux (what's a command line, anyhow :-?  ), but I will happily supply any more info that I can if anyone could graciously help me out.

If anyone knows if the router I am using doesn't work with Ubuntu, then please fill me in on that too :( 

Many thanks for your time

Richard

---

### Post by spd106 on 2006-08-05
Just to be clear, are you using usb or ethernet the connect to the router? I strongly suggest that you use ethernet if you don't already. That way there should be no problems with ubuntu instead of windows since you need no controlling software. Instead it will be configured through a web interface usually 192.168.1.1 or 192.168.2.1. It seems strange that windows reports a 10.0.0.0 network. Looking through the router manual [http://www.zoom.com/techsupport/adsl/adsl_5554.shtml](http://www.zoom.com/techsupport/adsl/adsl_5554.shtml), it looks like you have to navigate to 10.0.0.2 to configure it.

Try pinging 10.0.0.2 first to check that you have a connection.

---

### Post by RichardSchollar on 2006-08-05
Hi Spd106

Thanks for the reply: I do indeed use an ethernet cable.  I apologise if this sounds grossly stupid, but when you say "ping 10.0.0.2" what do you actually mean?  I've tried typing in "http://10.0.0.2" into Firefox (this is what I did for XP, which worked) to configure the router, but in Firefox under Ubuntu I get the "Unable to connect" error.

I have wondered if maybe I should reset the router defaults and then try and connect first of all thru Ubuntu (rather than doing the setup under Windows) - do you think this is a sensible sounding option, or not relevant?

Thanks

Richard

---

### Post by spd106 on 2006-08-05
Let's not be too hasty, if the router works with windows then it should be ok. First let's make sure the ethernet connection is up. Open a terminal (Apps -> Accessories -> Terminal) then type ```
$sudo ifconfig
```This should show eth0 and an ip address on the second line, something like this```
 eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80:xxxx:xxxx:xxxx:xxxx:/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12508631 (11.9 MiB)  TX bytes:85665406 (81.6 MiB)


```If so, this is good. Then try ```
$ping -c 5 10.0.0.2
```You should get 5 replies.
If this isn't working could you post the output.

---

### Post by RichardSchollar on 2006-08-06
This is what I get (note I pinged the IP address that came up from the ifconfig command):

richard@RGS:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:01:6C:E6:AD:39
          inet addr:172.206.212.187  Bcast:172.206.255.255  Mask:255.255.255.255          inet6 addr: fe80::201:6cff:fee6:ad39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

richard@RGS:~$ ping -c 5 172.206.212.187
PING 172.206.212.187 (172.206.212.187) 56(84) bytes of data.
64 bytes from 172.206.212.187: icmp_seq=1 ttl=64 time=0.066 ms
64 bytes from 172.206.212.187: icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from 172.206.212.187: icmp_seq=3 ttl=64 time=0.047 ms
64 bytes from 172.206.212.187: icmp_seq=4 ttl=64 time=0.051 ms
64 bytes from 172.206.212.187: icmp_seq=5 ttl=64 time=0.049 ms

--- 172.206.212.187 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.047/0.052/0.066/0.010 ms
richard@RGS:~$

I hope this means something to you!  :) 

Richard

---

### Post by spd106 on 2006-08-06
> net addr:172.206.212.187 Bcast:172.206.255.255 Mask:255.255.255.255I'm going to assume the router is passing on this ip address. The mask given doesn't make any sense to me. You should try setting a static ip address for eth0. 
To do this open the network admin applet and in the properties dialog box change the configuration to static, ip address to 10.0.0.3, subnet mask to 255.255.0.0 and gateway to 10.0.0.2.

Now enable etho and close the applet. You should now be able to ping 10.0.0.2 and access the web interface.

---

### Post by RichardSchollar on 2006-08-06
Spd106

I must apologise: I provided garbage info on that ifconfig data - I am afraid I had been messing around with the Network Admin settings and had changed it to a static IP address (probably why you thought the subnet mask looked like rubbish).  I did try and set the static as per your instructions, but got nothing.  

Hence, returned to DHCP and re-ran the ifconfig:

eth0 Link encap:Ethernet HWaddr 00:01:6C:E6:AD:39
inet6 addr: fe80::201:6cff:fee6:ad39/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:7800 (7.6 b) TX bytes:0 (0.0 b)
Interrupt:209 Base address:0x4000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:272 (272.0 b) TX bytes:272 (272.0 b)



When I run the ping command here I get "No connection" or something along those lines - stupidly haven't written down the exact message.  I am presuming that it can't even see my router??

Thanks for your assistance - I'd be totally at sea without it!

Richard

---

### Post by RichardSchollar on 2006-08-06
Here's some additional info from other shell commands:

richard@RGS:~$ lspci | grep Eth
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
richard@RGS:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
richard@RGS:~$ cat /etc/resolv.conf
richard@RGS:~$ cat /etc/network/interfaces
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


iface dsl-provider inet ppp
provider dsl-provider
richard@RGS:~$ cat /etc/dhcp3/dhclient.conf
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
richard@RGS:~$


I hope it will be of use.

Richard

---

### Post by spd106 on 2006-08-06
Okay, let's try two things.

1) Stick with dhcp and run **$sudo dhclient eth0** and hope it doesn't time out.

2) On Windows your setup uses ip = 10.0.0.4, netmask = 255.255.255.0, gateway = 10.0.0.2, so try entering these as static.

---

### Post by RichardSchollar on 2006-08-06
OK, tried the first command but not sure what it's showing me.  Also, used the set up with 10.0.04 etc and then used ping command (was unable to browse the web).  Got no reply from 10.0.0.2, but did get one from 10.0.0.4 (presumably cos that's just talking to myself?):


richard@RGS:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:01:6c:e6:ad:39
Sending on   LPF/eth0/00:01:6c:e6:ad:39
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
richard@RGS:~$ ping -c 5 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
From 10.0.0.4 icmp_seq=1 Destination Host Unreachable
From 10.0.0.4 icmp_seq=2 Destination Host Unreachable
From 10.0.0.4 icmp_seq=3 Destination Host Unreachable
From 10.0.0.4 icmp_seq=4 Destination Host Unreachable
From 10.0.0.4 icmp_seq=5 Destination Host Unreachable

--- 10.0.0.2 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4000ms
, pipe 3
richard@RGS:~$ ping -c 5 10.0.0.4
PING 10.0.0.4 (10.0.0.4) 56(84) bytes of data.
64 bytes from 10.0.0.4: icmp_seq=1 ttl=64 time=0.054 ms
64 bytes from 10.0.0.4: icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from 10.0.0.4: icmp_seq=3 ttl=64 time=0.049 ms
64 bytes from 10.0.0.4: icmp_seq=4 ttl=64 time=0.050 ms
64 bytes from 10.0.0.4: icmp_seq=5 ttl=64 time=0.050 ms

--- 10.0.0.4 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.049/0.050/0.054/0.008 ms
richard@RGS:~$

---

### Post by spd106 on 2006-08-06
I've had a look around (on google) and it seems that the network chip should be supported by the forcedeth kernel module (lsmod | grep force).
However looking at this thread [http://www.ubuntuforums.org/showthread.php?t=230636](http://www.ubuntuforums.org/showthread.php?t=230636) someone else is also unable to get it working.

Try having a look through this thread for a possible solution [http://www.ubuntuforums.org/showthread.php?t=186848](http://www.ubuntuforums.org/showthread.php?t=186848)

---

### Post by RichardSchollar on 2006-08-07
Thanks - will give it a go when I get back home.  If it looks like a network card problem, and the above doesn't resolve, I'll go and pick one up (I only need a cheap&cheerful one).

Richard

---

### Post by RichardSchollar on 2006-08-07
I am afraid the forcedeth.ko file did not help.  Neither did turning off the modem's power supply for a couple of minutes.

Thank you for your assistance with this though spd106.  I shall consider purchasing another ethernet card if I can determine if my current one really is to blame.

Best regards

Richard

---

### Post by RichardSchollar on 2006-08-13
The problem was with my ethernet adapter (NForce 430 built into my motherboard).  I installed an additional ethernet card (a cheap 3Com - cost about US$17) and was then able to connect without problems.

Richard

---

