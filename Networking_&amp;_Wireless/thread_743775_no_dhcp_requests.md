---
title: "no dhcp requests"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by ZMpike on 2008-04-02
I can't get any connection on my onboard ethernet connection. ifconfig shows the device with its correct MAC and I can ping the loopback but nothing else because I have no ip. When I do a networking restart I get the mesg no DHCPOFFER received. I have tried removing ipv6 but it didnt help.

below is a cat of ipconfig eth0, resolv.conf, dhclient.conf

```
eth0      Link encap:Ethernet  HWaddr 00:50:70:56:11:B0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:115 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:15635 (15.2 KB)
          Interrupt:5 Base address:0xc000 

resolv.conf:

search home
nameserver 192.168.1.1


dhclient.conf:

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

### Post by ZMpike on 2008-04-03
bumping since it was late last night when i posted

---

### Post by superprash2003 on 2008-04-03
it could be a roaming mode problem .. check this [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html)

---

### Post by ZMpike on 2008-04-05
I already set my interface to DHCP. I still get this output from sudo dhclient eth0:
discover requests...
No DHCPOFFERS received
No working lease in persistant database

This whole issue started when I upgraded to gutsy. I was running feisty before and the kernel option pcmcia=off combined with turning off ipv6 allowed me to access the internet with no problems. But my usb didn't work so I thought I would try the upgrade. I could of course just reinstall feisty, however, I also have these exact same problems with fedora8, suse10, rhel5 so I am trying to resolve the issue rather than work around. There are other issues also basically with all onboard devices not working - AC'97, usb, ethernet. All devices are recognized correctly, as far as I can tell, but just don't work. Everything except the usb were working on feisty, but no other linux versions. I also have to run the acpi=off kernel parameter or udev fails.

My system:
Athlon64 3000  - but running i386 versions
NVIDIA 6600GT
chaintech mobo - no support unfortunately
with the nforce4 chipset

---

### Post by superprash2003 on 2008-04-05
have you tried by manually entering the ip in network settings?

---

### Post by ZMpike on 2008-04-06
Have tried both dhcp and static. tried the sudo dhclient eth0 cmd. also tried hooking up wake on lan because I saw someone using debian used that to fix a similar issue.  With static IP it can't find the default gateway.  I can ping my loopback but nothing outside my local host.

---

### Post by ZMpike on 2008-04-08
ok I switched back to 7.04 and my network works great.  
I saved my dmesg,host.conf, dhclient.conf, resolv.conf, and interfaces files from 7.10.  I compared the files to 7.04 and there are no differences. 
Does anyone have any ideas as to why my network works in feisty but not in gutsy?

---

### Post by mlekodukye on 2008-07-07
the same problem with 8.04 here, i used to have instant internet right from the liveCD on 7.04 but now i don't. switched back and forth the roaming mode, tried entering ip manually - no result!!

the ethernet adapter is attansic L1, mobo is asus p5k, ubuntu 8.04 64-bit desktop

---

