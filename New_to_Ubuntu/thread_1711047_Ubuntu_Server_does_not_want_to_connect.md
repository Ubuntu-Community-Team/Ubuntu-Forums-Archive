---
title: "Ubuntu Server does not want to connect"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by Fearless1057 on 2011-03-20
So recently I decided to go from a Windows based server to a Linux based server and decided to use Ubuntu Server edition. It was working fine and I believed to have accidentally messed with files I was not supposed to be messing with and now it does not want to connect to the internet.
I was getting an error "sudo unable to resolve host" but I managed to fix that but still no internet connection

[QUOTE=hosts file]127.0.0.1	ServerName	localhost.localdomain	localhost
::1	ServerName	localhost6.localdomain6	localhost6
192.168.1.102 ServerName

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/QUOTE]

[QUOTE=Hostname file]ServerName 
[/QUOTE]

[QUOTE= networks file]default		0.0.0.0
loopback	127.0.0.0
link-local	192.168.1.255
localnet	192.168.1.1
[/QUOTE]

---

### Post by taseedorf on 2011-03-21
Cables plugged?
 Check.

try typing this in the command prompt

ifconfig

this will tell you some info about your connections...

that output will let me better help you, and perhaps help yourself... post it here

Are you running a dhcp client? or how are you getting your ip? Statically?  


Try making your hosts file look exactly like this...replacing <host> with your server's name and  NO "< >"

192.168.1.102	<host>	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	<host>	localhost6.localdomain6	localhost6
127.0.1.1	<host>

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts




THEN....try this

sudo ifconfig eth0 down  
(Assuming eth0 is your nic)
then
sudo ifconfig eth0 up

---

### Post by Fearless1057 on 2011-03-21
This is what I got from ifconfig, also I am using a static IP the cable is properly plugged in properly; also I made the file look exactly like you said and nothing.
>  admin94@ServerName:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:4e:3a:d9  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe4e:3ad9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5020 (5.0 KB)  TX bytes:12392 (12.3 KB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131268 (131.2 KB)  TX bytes:131268 (131.2 KB)
Also, thanks for the help.:)
If anything i'll just re install Ubuntu Server

---

