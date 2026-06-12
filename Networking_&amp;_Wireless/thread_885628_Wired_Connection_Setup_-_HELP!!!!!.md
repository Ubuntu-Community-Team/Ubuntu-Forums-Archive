---
title: "Wired Connection Setup - HELP!!!!!"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by DualJazz on 2008-08-10
Hello, i am still having a problem with my wired connection. Its a wired broadband connection my internet and im using a lan hub which connects to the internet.
I am on tiscali and i have tried the techniques like changing the ip to auto config and setting DNS but still no luck, i also tried the ipv6 thingy and that didnt work. I cannot download updates or view any websites (except google, it searches but then dosnt load the page i want to load). I am dual booting XP and Ubuntu 8.04 - Installed on LiveCD and motherboard with lan is **Sis191 Gigabyte**

---

### Post by chili555 on 2008-08-10
Please open a terminal and do:```
ifconfig
```If you see an entry for eth0, please do:```
sudo dhclient eth0
```If you do not connect or do not see an entry for eth0, please do:```
sudo lshw -C network
```and post the result. Thanks.

---

### Post by DualJazz on 2008-08-10
Thank you for reply

These are my results! Thnx for codes! :)

computer@computer-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:97:e1:8e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe97:e18e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:30 dropped:0 overruns:0 frame:30
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8762 (8.5 KB)  TX bytes:16228 (15.8 KB)
          Interrupt:20 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75000 (73.2 KB)  TX bytes:75000 (73.2 KB)

computer@computer-desktop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 5805
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:8d:97:e1:8e
Sending on   LPF/eth0/00:50:8d:97:e1:8e
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 1729 seconds.
computer@computer-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 190 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 01
       serial: 00:50:8d:97:e1:8e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.3 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s

---

### Post by DualJazz on 2008-08-10
bump!

---

### Post by DualJazz on 2008-08-10
bump again! POSTED results above ^^^^^^^^^

---

### Post by DualJazz on 2008-08-10
bump again! Need help - what did i need todo this for? what now?

---

### Post by chili555 on 2008-08-10
> DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 1729 seconds.Looks like you are connected perfectly well.

Please let me see:```
ping -c3 www.google.com
ping -c3 209.85.165.103
cat /etc/resolv.conf
```Thanks.

---

### Post by DualJazz on 2008-08-10
Hello again, this is what i got from your code! I changed back the wired connection to roaming mode just incase, but its exactly the same as auto so i did that just incase! :)


computer@computer-desktop:~$ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.102.9.147) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (66.102.9.147): icmp_seq=1 ttl=235 time=111 ms
64 bytes from [www.google.com](www.google.com) (66.102.9.147): icmp_seq=2 ttl=235 time=112 ms
64 bytes from [www.google.com](www.google.com) (66.102.9.147): icmp_seq=3 ttl=235 time=112 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 111.670/112.272/112.754/0.594 ms
computer@computer-desktop:~$ ping -c3 209.85.165.103
PING 209.85.165.103 (209.85.165.103) 56(84) bytes of data.
64 bytes from 209.85.165.103: icmp_seq=1 ttl=241 time=144 ms
64 bytes from 209.85.165.103: icmp_seq=2 ttl=241 time=143 ms
64 bytes from 209.85.165.103: icmp_seq=3 ttl=241 time=142 ms

--- 209.85.165.103 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 142.034/143.216/144.267/0.967 ms
computer@computer-desktop:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4887
#
### END INFO



nameserver 192.168.1.1

---

### Post by fwre01 on 2008-08-10
...whats the problem exacltly? it seems asthough you can resolve and ping hosts on the net fine. so is there still a problem?

---

### Post by DualJazz on 2008-08-10
> **fwre01 said:**
> ...whats the problem exacltly? it seems asthough you can resolve and ping hosts on the net fine. so is there still a problem?

I just cant access the internet fully! I can load up google and search for anything, but when i want to click one of the results it just dosnt load up the page or acts as if it does.

And also i cant update ubuntu or search for new programs on Synaptic Package Manager.

---

### Post by fwre01 on 2008-08-10
strange, you may be able to search google because of a dns cache. trying changing you /etc/resolv.conf. take out the 192.168.1.1 and use tiscali's name servers which are
Primary DNS Server 212.74.112.66
Secondary DNS Server 212.74.112.67

so it looks like this instead...

nameserver 212.74.112.66
nameserver 212.74.112.67

---

### Post by DualJazz on 2008-08-10
> **fwre01 said:**
> strange, you may be able to search google because of a dns cache. trying changing you /etc/resolv.conf. take out the 192.168.1.1 and use tiscali's name servers which are
Primary DNS Server 212.74.112.66
Secondary DNS Server 212.74.112.67

so it looks like this instead...

nameserver 212.74.112.66
nameserver 212.74.112.67

I think i remeber doing this but still gathered the same problem, ill try again and see what happens

---

### Post by DualJazz on 2008-08-10
Well the DNS's are defined but gathering the same problem, tried chaning the ip proxy to auto on firefox and auto ip on network manager but still no luck.

Do i need to install a linux driver for the motherboard? Because I found the driver on my motherboards website but had problems installing it, because you had to copy a file over to the linux distro's header folder but I didnt have permission or something like that to copy it and I am the only user.

Or has it got nothing todo with that? Does ndiswrapper help at all, if so ill try that and how?

EDIT : Driver as in Sis191 driver

---

### Post by fwre01 on 2008-08-10
both of those sound possible (maybe), but unlikely. so, as a test, can you open a terminal and ping these three sites.
facebook.com
ubuntuforums.org
sourceforge.net
im assuming you can resolve and ping those addresses, but cant view them in the firefox? is that right?

---

### Post by DualJazz on 2008-08-10
> **fwre01 said:**
> both of those sound possible (maybe), but unlikely. so, as a test, can you open a terminal and ping these three sites.
facebook.com
ubuntuforums.org
sourceforge.net
im assuming you can resolve and ping those addresses, but cant view them in the firefox? is that right?

But before i do this, if firefox is the problem, why is this affecting the updates?

---

### Post by villiansv on 2008-08-10
Just to add - I tried Ubuntu a couple of days ago, and I had the exact same problem. This is on an Asus laptop, with the ethernet reported (in Vista) as SiS191. DHCP worked fine, however no sites were accessible, and the automatic update did not work. I could ping, but nothing more than that.
Since I did not have a 2nd computer handy, I didn't feel like rebooting into Windows 10 times to post on the forums and get it working (lazy, I know :-)). Hopefully the issue will be resolved and I can try out Ubuntu again.

---

### Post by fwre01 on 2008-08-10
thats why my initial thought was a DNS problem...

i was trying to get a clearer picture of what is and isnt happening

---

### Post by DualJazz on 2008-08-10
Well, here it is the pings I have done. Also I have pasted my results of updating ubuntu aswell. I have split the results, one part is pinging and the other is the update APT source errors.

computer@computer-desktop:~$ ping -c3 [www.facebook.com](www.facebook.com)
PING [www.facebook.com](www.facebook.com) (69.63.184.15) 56(84) bytes of data.
64 bytes from [www.facebook.com](www.facebook.com) (69.63.184.15): icmp_seq=1 ttl=246 time=110 ms
64 bytes from [www.facebook.com](www.facebook.com) (69.63.184.15): icmp_seq=2 ttl=246 time=110 ms
64 bytes from [www.facebook.com](www.facebook.com) (69.63.184.15): icmp_seq=3 ttl=246 time=107 ms

--- [www.facebook.com](www.facebook.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 107.602/109.678/110.912/1.501 ms
computer@computer-desktop:~$ ping -c3 [www.ubuntuforums.org](www.ubuntuforums.org)
PING [www.ubuntuforums.org](www.ubuntuforums.org) (91.189.94.12) 56(84) bytes of data.
64 bytes from [www.ubuntuforums.org](www.ubuntuforums.org) (91.189.94.12): icmp_seq=1 ttl=53 time=19.5 ms
64 bytes from [www.ubuntuforums.org](www.ubuntuforums.org) (91.189.94.12): icmp_seq=2 ttl=53 time=21.3 ms
64 bytes from [www.ubuntuforums.org](www.ubuntuforums.org) (91.189.94.12): icmp_seq=3 ttl=53 time=20.7 ms

--- [www.ubuntuforums.org](www.ubuntuforums.org) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 19.542/20.518/21.314/0.753 ms
computer@computer-desktop:~$ ping -c3 [www.sourceforge.net](www.sourceforge.net)
PING sourceforge.net (216.34.181.60) 56(84) bytes of data.
64 bytes from [www.sourceforge.net](www.sourceforge.net) (216.34.181.60): icmp_seq=1 ttl=245 time=121 ms
64 bytes from [www.sourceforge.net](www.sourceforge.net) (216.34.181.60): icmp_seq=2 ttl=245 time=122 ms
64 bytes from [www.sourceforge.net](www.sourceforge.net) (216.34.181.60): icmp_seq=3 ttl=245 time=123 ms

--- sourceforge.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 121.603/122.505/123.023/0.640 ms

------------------------------------------------------------------

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release](http://archive.canonical.com/ubuntu/dists/hardy/Release)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)

---

### Post by DualJazz on 2008-08-10
Also, ive been looking around the forums and posts have said that you can change the overall internet speed or something to what your internet speed is actually supposed to be rather then Ubuntu giving you a really high speed. Is that a problem, and do i need to try the ipv6 problem again? (just a notice)

---

### Post by DualJazz on 2008-08-11
bump

---

### Post by chili555 on 2008-08-11
I just noticed this in your *ifconfig*:> Interrupt:20 Base address:[COLOR="Red"]0xdead[/COLOR]I have been Googling for this and the results, as far as I can see, share two common themes: they are all involving the Sis 190 chipset and none seem to have a solution. I am beginning to suspect there is a flaw in the driver *sis190*. As I see it, there are three alternatives:

#Keep Googling and hope we see a solution.
#Try ndiswrapper. 
#Buy a new $15 ethernet card and wait for the *sis190* driver to get updated.

I wish I had a silver bullet solution.

---

### Post by fenderjaguar on 2008-11-06
Got an abit SG-95 too. Tried Ubuntu and got the whole "Google working, but nothing else" thing. I groaned when reading I would have to stick a network card in my PC. Mainly because I don't have one to hand, it's an inconvenience and it would have to go right underneath the video card (I wanted the radeon x800 to get some fresh air).

However, my router (a BT home hub) has USB ports on it. So I just did that. To my amazement it works perfectly. You'll have to forgive me, I know nothing of linux really, but I remember my mate once telling me to steer well clear of any non-ethernet connection with linux. But nay, Internet and Bittorrent both seem to work fine right off the bat.

---

### Post by kapetus on 2008-11-07
just adding then same problem...

i have a laptop running ubuntu 8.10 intrepid ibex (64bit)version
and it recongnises the sis191 network card, but nothing works, ping or internet browsers, but with the 32bit version all works fine.
but with a 64bit machine its a petty dont use all the pottencial...
it wod be good to solve this BUG...

---

### Post by fenderjaguar on 2008-11-14
LOL, mine works with the LAN, now! I haven't even done anything.

---

