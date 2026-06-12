---
title: "Wired connection on Hardy"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by JohnnyTricksta on 2008-06-27
I just installed the newest release of Ubuntu on my HP dv6000. Whenever I plug in my wired internet it tries to connect but fails. It says my wired connection is secured, however as far as I know it is not. I know the wireless is secure with WEP. I've tried typing my WEP key in as the password, but it still didn't work. How do I find out all information it asks for (PEAP, identity, etc...) I need this up and running so I can install my BCM wireless driver.

Thanks!
Jt

---

### Post by superprash2003 on 2008-06-27
go to your terminal and type ifconfig and post output here.. before that go to system-admin-network and go to your ethernet properties and set it to DHCP mode

---

### Post by JohnnyTricksta on 2008-06-27
> **superprash2003 said:**
> go to your terminal and type ifconfig and post output here.. before that go to system-admin-network and go to your ethernet properties and set it to DHCP mode

I went in and changed my wired connection to DHCP. However, when I went to the terminal and typed ipconfig it said command not found. I'm not sure if it will help or not, but I ran ipconfig in windows. I've attached a SS below:

---

### Post by JohnnyTricksta on 2008-06-27
Bump

---

### Post by superprash2003 on 2008-06-27
isnt this a ubuntu pc mate?? how come you are trying all this in a windows machine..

---

### Post by elbrute on 2008-06-28
@ JohnnyTricksta

The command in Linux is i[COLOR="Red"]f[/COLOR]config, not i[COLOR="red"]p[/COLOR]config.

Dave

---

### Post by JohnnyTricksta on 2008-06-28
Sorry about that. Being a Windows user for so long I just glanced over that and thought it said ipconfig. Here is my ifconfig output:

jordan@jordan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:6e:37:04  
          inet6 addr: fe80::216:36ff:fe6e:3704/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1992 (1.9 KB)
          Interrupt:10 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:36:6e:37:04  
          inet addr:169.254.2.189  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11892 (11.6 KB)  TX bytes:11892 (11.6 KB)

---

### Post by stringkarma on 2008-06-28
you shouldn't need the device eht0:avahi. I am running the same laptop (dv6000) and sometimes I get an extra wireless card with :avahi added. try

sudo ifconfig eth0:avahi down

(you may need to restart networking at this point "sudo /etc/init.d/networking restart", but try it first as this may also restart the :avahi device) and see if this works.

If it does you may want to go to System -> Administration -> Services and turn off Multicast DNS discovery. This will prevent the eth0:avahi device from reappearing.

---

### Post by JohnnyTricksta on 2008-06-29
Nope, still no success :(

jordan@jordan-laptop:~$ sudo ifconfig eth0:avahi down
[sudo] password for jordan: 
jordan@jordan-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5751
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:6e:37:04
Sending on   LPF/eth0/00:16:36:6e:37:04
Sending on   Socket/fallback
grep: /etc/resolv.conf: No such file or directory
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:6e:37:04
Sending on   LPF/eth0/00:16:36:6e:37:04
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]

---

### Post by stringkarma on 2008-06-30
Well maybe thats not the problem then, I do wonder about the output of your restart though. I have seen, one time, that ipv6 was working but not ipv4. In your ifconfig I see ipv6 info only. If I recall correctly the problem was in the hosts file that time. Can you post the output of "cat /etc/hosts" ?

---

### Post by superprash2003 on 2008-06-30
is that ifconfig output after you enabled DHCP? if so try manually entering ip address.. what is your router ip?

---

### Post by JohnnyTricksta on 2008-06-30
Ok, I think I found out my problem. It seems my wired connection is protected. Here's what I found out. When I plug it into my X-box or XP machine it automatically detects my 802.1x wired protection and uses a default certificate or smart card to gain access. Since my 360 and XP machine did this in the back ground I thought the connection was not protected since it worked out of box (I pluged my CAT6 cable in and I had instant internet). However, on my vista and Ubuntu machine it doesn't want to connect.

Does anyone know how to disable this? I've gone to my router [http://192.168.1.1](http://192.168.1.1) but I don't see any option to disable this. Or, is there a way to figure out how to configure Ubuntu to work in conjunction with this?

Many Thanks!

PS: Here is my hosts file:

jordan@jordan-laptop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	jordan-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by JohnnyTricksta on 2008-06-30
> **superprash2003 said:**
> is that ifconfig output after you enabled DHCP? if so try manually entering ip address.. what is your router ip?
If you use a wired connection, won't your IP be dynamic and change on each restart? If not, how do I know which IP address to use?

---

### Post by stringkarma on 2008-06-30
> **JohnnyTricksta said:**
> Ok, I think I found out my problem. It seems my wired connection is protected. Here's what I found out. When I plug it into my X-box or XP machine it automatically detects my 802.1x wired protection and uses a default certificate or smart card to gain access. Since my 360 and XP machine did this in the back ground I thought the connection was not protected since it worked out of box (I pluged my CAT6 cable in and I had instant internet). However, on my vista and Ubuntu machine it doesn't want to connect.

Does anyone know how to disable this? I've gone to my router [http://192.168.1.1](http://192.168.1.1) but I don't see any option to disable this. Or, is there a way to figure out how to configure Ubuntu to work in conjunction with this?


You are jumping a little out of my field of knowledge. It is interesting that your vista box is having problems with it too though. This is at your house correct? I am a little surprised that a home wired connection would be protected by a certificate. Check again to see if there isn't some security setting turned on in the router. While you are in there make sure that DHCP is turned on for assigning IPs to connections (in the router). I hope this works as I am running out of ideas for you, without being able to sit down and tinker with it myself.

---

### Post by superprash2003 on 2008-06-30
it need not change everytime.. atleast it doesnt for me!!!

---

