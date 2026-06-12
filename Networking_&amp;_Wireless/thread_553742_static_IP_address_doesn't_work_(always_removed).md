---
title: "static IP address doesn't work (always removed)"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by zhangweiwu on 2007-09-18
Dear all.

I used ubuntu for several years always with DHCP. Now I am taking the iBook for trip and I must work in a place where there is no DHCP. I have followed instructions on the Internet which suggested me changed my /etc/network/interfaces to the following:
```

zhangweiwu@esmeralda:~/code$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.23.19
netmask 255.255.255.0
gateway 192.168.23.254

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

The result is, every time after I run ```
sudo /etc/init.d/networking restart
```, I got the IP address I specified (192.168.23.254), like the following:
```

zhangweiwu@esmeralda:~/code$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:95:EA:46:82  
          inet addr:192.168.23.19  Bcast:192.168.23.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:95ff:feea:4682/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162861979 (155.3 MiB)  TX bytes:6212636 (5.9 MiB)
          Interrupt:41 
```

but after several minutes, all connection broken and I got:
```

zhangweiwu@esmeralda:~/code$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:95:EA:46:82  
          inet6 addr: fe80::20a:95ff:feea:4682/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:414960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162598156 (155.0 MiB)  TX bytes:6211532 (5.9 MiB)
          Interrupt:41 

eth0:avah Link encap:Ethernet  HWaddr 00:0A:95:EA:46:82  
          inet addr:169.254.145.237  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:41 


```

This is frustrating, I have to maintain a stable connection and I am already very frustrated as I have been doing ```
sudo /etc/init.d/networking restart
``` every a few minutes.

How can I set the box to really, really, use static IP address and stop trying eth0:avah ?

(P.S. I am command line freak, to help me it's okay to to straight to the point. Used more than a dozen Linux distros without such problem before moved to Ubuntu last year. thanks very much for your help!)

---

### Post by wieman01 on 2007-09-18
I'd replace the Ethernet cord first of all. This is odd and I have no explanation for it at this moment. 

What does "dmesg" say right after the connection has dropped.

---

### Post by bapoumba on 2007-09-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/138895](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/138895) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have *exactly* the same problem with a laptop, DHCP at home, static IP at work.

I fixed it removing network-manager and some of the dependencies. I never used network-manager, which is not happy with static IPs, and overwrite the config files depending on which location I connect.

To be noted: it started to happen after i begun to use my ethernet (eth0) network card both at home (DHCP) and at work (static IP). Previously, I used the wireless card at home, and eth0 at work, and there was no issue for several years.

Switching from static config --> DHCP config works fine restarting the networking service. Going from DHCP --> static needs a reboot.

This is where I am for now. I'm looking into some other packages that can automatically pick up the proper configuration depending on where I connect (guessnet et ifplugd), but I have not tested yet.

---

### Post by wieman01 on 2007-09-18
**@Bapoumba:**

Will Gutsy improve networking at all? I head that the use of static leases will be fixed. Waiting for a month and then upgrading to Gutsy might resolve the issue.

---

### Post by bapoumba on 2007-09-18
@ wieman01: I am already running gutsy (since Tribe2). I have not changed my profile infos because I do not consider myself a "beta tester".
```
:~ $ aptitude show network-manager
Package: network-manager
New: yes
State: not installed
Version: 0.6.5-0ubuntu11
```
This is the package I removed (along with the other ones stated in the bug report, ie network-manager-gnome, dhcdbd, libnl1-pre6, libnm-util0).

---

### Post by wieman01 on 2007-09-18
Oh no... I was hoping they would fix it with the advent of Gutsy. Hope they will do so before the final version comes out. I find it a bit frustrating that they cannot get a grip on such a simple feature. Even WICD can handle static IPs with way less programming effort and man power.

---

### Post by zhangweiwu on 2007-09-19
I think I have "solved" this problem by using a reboot after configured network. network-manager package is not removed by me.

This isn't good because Linux used to have no requirement of reboot unless kernel is replaced.

---

### Post by richg74 on 2007-11-24
I've had the same problem with trying to set, and keep, a static IP on my Feisty box.  I found a trick that seems to work in the FAQ at avahi.org
[http://avahi.org/wiki/Avah4users]("http://avahi.org/wiki/Avah4users#FAQ").    You can get avahi to ignore a specific interface by turning the multicast flag off, like so:
 
[FONT="Courier New"]ifconfig ethN -multicast[/FONT]

So far it seems to work OK, although obviously it's a non-starter if you need multicast for something else.

---

### Post by hodad on 2007-11-24
I have been having the same problems listed in this thread and have wasted a lot of time trying to figure out what's going on. The System-Admin-Network and Network Tools drop downs are pretty much useless.

 Hearing the back and forth here have been helpful  - BUT -
Does anyone know of a good discussion/explanation of ethernet port commands and networking issues within the Ubuntu community?  I'd like to be able to fix the problems on the command line, but the "Documentation" on the Ubuntu website is oversimplified, and frankly, doesn't explain what to do when things go wrong when using the GUI apps.

Thanks!

---

### Post by wieman01 on 2007-11-24
> **hodad said:**
> I have been having the same problems listed in this thread and have wasted a lot of time trying to figure out what's going on. The System-Admin-Network and Network Tools drop downs are pretty much useless.

 Hearing the back and forth here have been helpful  - BUT -
Does anyone know of a good discussion/explanation of ethernet port commands and networking issues within the Ubuntu community?  I'd like to be able to fix the problems on the command line, but the "Documentation" on the Ubuntu website is oversimplified, and frankly, doesn't explain what to do when things go wrong when using the GUI apps.

Thanks!
These two:
[http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")
[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

---

### Post by hodad on 2007-11-24
Thanks for your reply!

The postings are excellent, and I will delve into them.

In the meantime, I found a post by dataw0lf that is also excellent:

[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

---

### Post by bapoumba on 2007-11-24
I have not tested the solution richg74 suggested.
In the meantime, I got one workaround (but sorry, I cannot find again from where I got it..) to have the static IP  settings remain on eth0 after switching from DHCP :

```
sudo pkill dhclient
```

---

