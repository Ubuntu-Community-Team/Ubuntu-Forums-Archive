---
title: "[SOLVED] I changed the grub.lst and broke my wired connection O_o"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Dr.Pepper on 2008-11-10
Long story short, I noticed after installing Ubuntu that kacpid was using 80% of my CPU. My *only* option was to disable ACPI. Ubuntu booted and ran five times faster, but the internet stopped working in Ubuntu, although it was still fine in XP and Vista. I'm getting an IP and can ping the router, but Firefox, Synaptic, Open Arena, you name it, can't access the net.

After doing more searches, I tried everything to change Ubuntu's wired network settings with no success. I did add more parameters to the grub.lst(thinking they'd help) than I did in my recent PCLinuxOS install, which can access the net just fine, so I'm guessing maybe one of those could be the fault? I'm not quite sure though, still being a total newbie at Linux, I practically grew up on Windows. :P

Here's the part of the grub.lst that I changed, no need to post the whole thing if everything else is still the same.
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=6460371C6036F500 loop=/ubuntu/disks/root.disk ro acpi=off pic=noacpi apm=off quiet splash

So do I need to take away or add more parameters to make this work? If this is just fine, what setting do I need to change in Ubuntu to work around it? I'm all out of ideas after spending almost a week of sifting this MB for help. My problem seems pretty unique since the net stopped working only *after* I changed the lst file, but I don't know if the problem is more than skin-deep. I would like to stay booted in Ubuntu regularly and can't do that without an internet connection. I'm only asking for help because I've exhausted all that I know to do.

---

### Post by cariboo on 2008-11-10
What is the output of:

```
sudo lshw -C network
```

and

```
ifconfig
```

Got you paste the output in your next post.

Jim

---

### Post by Dr.Pepper on 2008-11-10
Oops, sorry I didn't think of putting that info in my first post.
I'm using Hardy Heron, hope this is useful:
```
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:04:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:5c:2e:fe
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
```

```
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:19:d1:5c:2e:fe  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe5c:2efe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1838 (1.7 KB)  TX bytes:5704 (5.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:135200 (132.0 KB)  TX bytes:135200 (132.0 KB)
```

---

### Post by Dr.Pepper on 2008-11-30
Sorry for the big bump (and for not posting in a while), but I finally figured out what my problem was!
I was randomly browser for a solution and found this thread today.
[http://ubuntuforums.org/showthread.php?t=476489](http://ubuntuforums.org/showthread.php?t=476489)
[QUOTE="chefele"]Additionally, the following two sets of parameters worked,
but I had no Ethernet / Internet access (adding irqpoll fixed this):

acpi=off
noapic acpi=off[/QUOTE]
After adding irqpoll to my kernel line, it got rid of all my internet problems. Now not only is my native install of Ubuntu running at full speed, but the internet is now functional too! I breathed a sigh of relief when Google came up in Firefox, I want to thank chefele for posting what's in the above quote. It's also nice that I'm able to keep IPv6 without having to blacklist it on everything as well. I'm typing this from Ubuntu right now without issue. :)
It's surprising how some things with less obvious answers have such simple solutions, now I can finally enjoy this awesome OS to it's fullest.

---

