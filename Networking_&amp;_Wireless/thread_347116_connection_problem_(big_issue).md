---
title: "connection problem (big issue)"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by checho on 2007-01-26
Hi everyone! I got an Fast Ethernet PCI CNet PRO 200 and Ubuntu 6.06 (not a good mix). I´ve been trying for 2 days to establish the connection via Cable/modem. I know that this and other cards with Davicom internet adapters give trouble because of a conflict between two modules in linux (and is a problem in many other distributions). In a forum I read that all you got to do is quit the module tulip (modprobe --remove tulip) and mount the module dmfe (modprobe dmfe). I did it, then restart the interface with "ifdown eth0" and "ifup eth0" but Igot this error:

parse_option_buffer: option host-name (15) larger than buffer.

I tried everything: restarting the computer, looking in the /etc/networking and /etc/devices scripts but I´ve no clue, even in the internet i haven´t found anything similar to this. I hope someone knows what to do! You are my only hope, otherwise there won´t be any other option for me than to go defeated to the store an buy a new card :confused:

---

### Post by chili555 on 2007-01-26
When you ifup eth0, does it try to reload tulip? Is your problem a conflict between tulip and dmfe?

You can check to see if tulip got loaded by doing sudo lsmod | grep tulip. You may get some lines of output including the word tulip, indicating ifup eth0 reloaded it, or you may get a command prompt, indicating it is not.

If it is reloaded, you might need to blacklist tulip. Add the following to your /etc/modprobe.d/blacklist file:

blacklist tulip

Let us know. Other dmfe fans will want to see what happens.

Good luck.

Also, could you please let us see the output of cat /etc/network/interfaces?

---

### Post by checho on 2007-01-26
Hi body, thanks for your time!  Well, first I forgot to mentioned but in all I've been doing I already blacklisted tulip and added dmfe to /etc/modules wich is a list of modules that you want to run at start up "kind of the opposite of blacklist i guess".
Ok, then this is the file you requested: 

root@sergio-desktop:/home/sergio# cat /etc/network/interfaces
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

now I include what shows ifconfig, i don't know maybe it can help you figure it out

root@sergio-desktop:/home/sergio# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:A1:46:DB:3C
          inet6 addr: fe80::208:a1ff:fe46:db3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:40445 (39.4 KiB)  TX bytes:29196 (28.5 KiB)
          Interrupt:185 Base address:0xac00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10752 (10.5 KiB)  TX bytes:10752 (10.5 KiB)

---

### Post by chili555 on 2007-01-26
I wonder if this > option host-name (15) larger than buffer is caused by the hyphen in your hostname: root@sergio-desktop? Dunno for sure, but I suggest Googling up changing your hostname to sergiodesktop.

Also, this > UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 implies that your eth0 is running OK, but just hasn't gotten an IP address yet. What do you get when you do sudo dhclient eth0?

---

### Post by koenn on 2007-01-27
>   ...  then restart the interface with "ifdown eth0" and "ifup eth0" but Igot this error:

parse_option_buffer: option host-name (15) larger than buffer.

when you run "ifdown eth0" and "ifup eth0, that will in turn run dhclient (to get ip address by dhcp), and "option host-name" is a keyword from dhclient config, so it's possible there's something crooked in the /etc/dhcp3/dhclient.conf, probably at or near the "option host-name"  statement in it. Have a look, or post the file for others to look at it.

---

### Post by checho on 2007-01-27
Hi, I'm taking the weekend off, so i got no access to my computer but monday I'm gonna check it out and post it, thanks again both for your time and for everyone that had read my issue

---

### Post by checho on 2007-01-29
ok here is what i get:

sergio@sergio-desktop:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:a1:46:db:3c
Sending on   LPF/eth0/00:08:a1:46:db:3c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.13 -- renewal in 1380 seconds.
sergio@sergio-desktop:~$ cat /etc/dhcp3/dhclient.conf
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

### Post by koenn on 2007-01-29
Strange. You got an IP address just fine. run
```
ifconfig eth0
``` again, it should now show that IP address - 192.168.1.13

are you still experiencing trouble then ? what kind ?

All what follows is guesswork so proceed with caution 

the only thing "host-name" related I can see in your dhclient config is that the computer requests to be given a hostname by the dhcp server. 

```
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, **host-name,**
netbios-name-servers, netbios-scope;
```) 

you might try removeing that request (remove what's bold in the code snippet) - make a copy of the file first in case things go bad. 

"option host-name" can also be set at the dhcp server, so if all of the above doesn't work, see if your dhcp server (could be located on your router / ...)  is configured to send out a hostname, along with other options such as dns-servers, netbios parameters and so on.

---

### Post by checho on 2007-01-29
I restarted the system to do what you told me but just before doing it I tried once more and there is, magically I got connected. The strange thing is that in the morning I did ifdown and ifup after trying what told me two days ago. It seems that a lesson of this is that if up and ifdown doesn't restart the whole connection (for example get a new ip adress in a dhcp network) just the ethernet card.
 Well thanks again for your help, I really apreciate it! I know that I never could figure it out by myself

---

