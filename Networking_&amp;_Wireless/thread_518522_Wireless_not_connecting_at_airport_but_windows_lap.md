---
title: "Wireless not connecting at airport but windows laptops do?"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by Malice007 on 2007-08-06
Hello, 

I am having a problem with a open WIFI hot spot at my work. The WIFI used to be the old B system and we upgraded to G. Well not WE the IT DEPT.  But anyways I can connect to this system my laptop tell me I am connected and have a good signal strength. But I can not surf the net or do anything other than just connect. Windows laptops can surf away. I have the new Dell Inspiron 1420N and I also have another laptop running Ubuntu and neither can connect since they upgraded to G I used to be able to connect to the B. 

I tried running IE under Wine (Nothing)

I tried loading XP under Vmware (still nothing)

I contacted Dell and spoke to people in there Linux dept and they believe the IT dept is blocking Linux machines because they could be hackers. And they suggested that I speak to the IT Dept to see if this is true or not.

Well my problem is I am not supposed to be surfing around while on the clock :) and I can’t ask them this.

I was wondering if anyone knew of away around this problem something I can do in Ubuntu that will trick there system to think I am a Mac or Windows machine? And no I do not want to partition my HD and put windows on it. Its bad enough I used Vmware to put it on..hehe

---

### Post by Malice007 on 2007-08-06
No help on this one? :)

---

### Post by Malice007 on 2007-08-07
Does anyone have any ideas at least?

---

### Post by lgambett on 2007-08-07
Could you please post the output of the ifconfig command ? It is unclear to me if you have a network connection problem or - simpler - a DNS setting problem. 802.11 B or G should not cause any difference.

---

### Post by Malice007 on 2007-08-07
Ok, here it is. But keep in mind I am at home now and it is working. But my home wireless is B.


eth0      Link encap:Ethernet  HWaddr 00:1A:A0:FC:F6:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:71:9C:7E  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe71:9c7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7167 errors:0 dropped:499 overruns:0 frame:0
          TX packets:7052 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:10369268 (9.8 MiB)  TX bytes:1472434 (1.4 MiB)
          Interrupt:17 Memory:fe8ff000-fe8fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:A0:FC:F6:41  
          inet addr:169.254.9.108  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1601 (1.5 KiB)  TX bytes:1601 (1.5 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.186.1  Bcast:172.16.186.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.249.1  Bcast:192.168.249.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Malice007 on 2007-08-07
Also I believe I posted that I can connect to the Wireless at work. Ubuntu shows me that I have a good connection. But if I try to do anything with the connection I can not. If you see anything wrong with my ifconfig that will be great and I hope it fixes the problem. 

Thanks,

---

### Post by Austin_KW on 2007-08-07
Do you get an ip address at work.
Have you set static ip address or static dns config?

---

### Post by Malice007 on 2007-08-08
Yes I get there IP when I am at work. Update also I ran out to the store today and bought a wireless G router and configured it to only allow G connection. And my laptop connects right away to it. So this would make me believe that they (my work) has something flagged that would block me. Like I said before I believe, I can connect to there wireless ifconfig and see there IP, I can even ping it. But to do anything else it will not allow me to go out.

I might be forced to just make a phone call and claim I am a customer using Linux and can not connect (call the IT dept that is)

---

### Post by kevdog on 2007-08-08
At home and at work what does your resolv.conf and dhclient.conf files look like??

---

### Post by Malice007 on 2007-08-08
Ok,

   Here are the files that you requested, this is from home only. I will have the work ones when I get in. 

# generated by NetworkManager, do not edit!



nameserver 192.168.15.1

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

---

### Post by kevdog on 2007-08-08
I want you to take a look at this page, particularly the dhcp3 section.  Try this to see if it suits you.  Im not a big fan of OpenDNS however if this solution works, you can always use different dns servers

[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

---

### Post by Austin_KW on 2007-08-08
Have you set a static dns nameserver in NetworkManager? 
This should be set by dhcp, but here it appears to be set by network manager.

You can easily verify a dns problem by pinging google.com by ip address;
ping -c3 72.14.207.99

---

### Post by Malice007 on 2007-08-09
I found out today for anyone to use the internet you must first open your browser and you are re directed to there site where you must agree to there terms. And then and only them will it let you use the network. For some reason I never get re directed to this site and this would be the reason why I never get to use the wireless. I never get it with IE or Fox. Is there a setting in Ubuntu that will allow there wireless to re direct me to there site right away and not block them when it try to do this to me?

---

### Post by kevdog on 2007-08-09
You are probably have to going find out the redirected URL, and then save this link as a bookmark.

---

