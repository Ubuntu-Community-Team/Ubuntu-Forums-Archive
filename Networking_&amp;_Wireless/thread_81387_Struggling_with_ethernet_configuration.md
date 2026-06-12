---
title: "Struggling with ethernet configuration"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by B0rsuk on 2005-10-24
Hey

Please help me, I can't set up my ethernet card for few days and I'm getting paranoid. If you can't help me fix it, at least help me to eliminate as many possible reasons as possible. I never configured a network before.

I have two computers here - my mother's Debian desktop I'm using right now, and my **Kubuntu Breezy Badger 5.10 i386**  machine. I need to connect my machine to the net directly (I mean, to replace mother's machine with my Ubuntu). Unfortunately the admin of the network is unreachable, same goes for brother who set up the Debian. I don't have root access. 
I don't know too much about the network, and I'm no network expert, but it uses ethernet cards and no modems, so I guess it counts as neither broadband nor dialup.
------------------------
Info about this Debian machine, (where internet works).
/sbin/ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:07:95:C5:FB:30
          inet addr:10.112.0.19  Bcast:10.112.0.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8547299 (8.1 MiB)  TX bytes:515592 (503.5 KiB)
          Interrupt:11 Base address:0xd400

eth1      Link encap:Ethernet  HWaddr 00:A0:CC:21:BB:1F
          inet addr:192.168.120.1  Bcast:192.168.120.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11160 (10.8 KiB)  TX bytes:11160 (10.8 KiB)

```

/sbin/route
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.120.0   *               255.255.255.248 U     0      0        0 eth1
10.112.0.0      *               255.255.240.0   U     0      0        0 eth0
default         10.112.0.1      0.0.0.0         UG    0      0        0 eth0

```

In case you wonder, eth1 is meant to used when my brother ocassionaly comes with notebook. I can't afford to connect my Kubuntu to my mother's Debian just to have net - my mother uses computer rarely and a LOT of power would be wasted.
==================================
Now my machine (Kubuntu) where internet needs to work. I remind you that I want to replace Debian machine with Kubuntu one and still have internet access. I tried and failed. First, I installed Kubuntu (and the automatic detection didn't work. I failed to guess the right numbers and set them manually during installation.

Then, I examined configuration files on this machine (Debian) and tried to configure mine (Kubuntu) using this document:
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

And it didn't work. It tries to synchronize clock at startup, and it takes a looot of time and ultimately fails.
I tried to ping my dns (I use 10.112.0.1 and 194.204.152.34). No messages, even "network unreachable".
====================================
Recent Info about machine I'm trying to set up instead of Debian
====================================

Last thing I did was reinstalling Kubuntu to reset all settings and try to configure it manually during installation. I thought I knew all the numbers I needed, because by this time I read a little on the subject. It accepted all numbers,  
(Numbers I used - based on some guesstimates and Debian's config, I'm no network expert. Please compare them to output from debian - above - and tell me if I chose right)
10.112.0.0 net
10.112.0.1 gw
255.255.240.0 netmask
10.112.0.19 ip adress
10.112.0.255 broadcast
10.112.0.1 194.204.152.34 (my dns servers, the way I typed them in installer)

....BUT it took awful lot of time to try apt repositories (I guess it already didn't work at that point). Then, dUring first boot process, it (again) stopped for a long time on "synchronizing clock with ntp.ubuntulinux.org".
At the moment I'm scrathching my head.

lspci (on my Kubuntu) shows that one of my 2 ethernet cards seems to work (I also have old one, and it's also displayed; now I use onboard nvidia nforce2 (ultra, I think) rev a1. (Of course, I chose the onboard one - nvidia - as default during installation. And that's where I plugged the cable).

By the way, once I connect the cable to my ethernet card, it blinks as it should, so most probably hardware is ok. Did I mention I'm getting paranoid ?

/sbin/route          (no floppy/net so I have to retype, sorry. I hope it's still readable)
```

Dest               GW    Genmask            Flags           Metric     Ref      Use   iface
localnet            *          255.255.240.0         U              0             0         0         eth0
default      10.112.0.1     0.0.0.0                 UG          0              0          0          eth0

```

/sbin/ifconfig (this is is going to be nasty)
```

eth0    Link encap: Ethernet HWaddr 00:11:D8:1E:85:08
inet addr: 10.112.0.19 Bcast:10.112.15.255 Mask 255.255.240.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
RX packets:8922 errors:0 dropped:0 overruns:0 frame:0
TX packets: 75 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000

lo       Link encap: Local Loopback
inet addr: 127.0.0.1      Mask:255.0.0.0
UP LOOPBACK RUNNING  MTU:16436 Metric: 1
Rx packets:23 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors: 0 dropped0 overruns: 0 carrier:0
collisions:0 txqueuelen:0
Rx bytes:1319 (1.2KiB) TX bytes:1319 (1.2 KiB)

```

**What should I do now ?**
Please help, I'm not the most experienced of Linux users, but I know a bit and I can answer questions. And provide contents of Debian's and my Ubuntu's config files. Won't you help a badger in distress ?

---

### Post by B0rsuk on 2005-10-24
I got **route** output to look the same on my Kubuntu as on the Debian machine. Except for additional eth1 - I  don't need it. Still nothing, not even "network unreachable". Any ideas ?

---

### Post by byourg on 2005-10-24
Try copying the info from /etc/network/interfaces from the Debian machine and putting it in the Kubuntu machine in the same file /etc/network/interfaces, substituting the eth0 or eth1 device you are using. Make a copy of the Kubuntu file for backup reasons first. Restart the network and see what happens.

---

### Post by B0rsuk on 2005-10-25
[QUOTE=byourg]Try copying the info from /etc/network/interfaces from the Debian machine and putting it in the Kubuntu machine in the same file /etc/network/interfaces, substituting the eth0 or eth1 device you are using. Make a copy of the Kubuntu file for backup reasons first. Restart the network and see what happens.[/QUOTE]

I carefully edited Kubuntu's /etc/network/interfaces as you said.
I presume by "restart the network" you meant /etc/init.d/networking restart. It said "reconfiguring .... ok". Then I tried pinging dns by ip - absolutely no response, not even "network is unreachable". I also tried pinging my gateway by dns, same result. I can't ping anything and no network program works. 
 . But I get this message if I pull the plug out, so I'm sure it's the right ethernet card. Later I tried sudo ifup -a  t o double check   (eth0 is preceded by "auto et0" in /etc/network/interfaces) and it said it's already configured. I'm completely lost now. Kubuntu still takes a lot of time at "Synchronizing clock with ntp.ubuntulinux.org" step.

**EDIT**
Someone from another ethernet topic claims that he was able fix the problem by installing older 2.6.11 kernel. Can anyone confirm that it works ?
If I were to try that way, what EXACTLY do I have to do  ?  I need to know first because copying some data between Debian and Kubuntu means I have to take out hdd **without rack**. So I'm not going to go back and forth many times.  **I'll kill** anyone coming up with suggestion of downloading it via apt.
 Could you help me complete the list ?

- on Kubuntu machine - go to source dir and make menuconfig, then save configuration to a file.
- download EXACTLY which packages do my Debian ? build-essential  ? kernel source ? Is that all ?
- copy them to (Kubuntu) /usr/src/linux
- make menuconfig - load documentation
- standard compilation procedure (make, make modules, make modules_install and also make clean/dep somewhere inbetween)

---

### Post by mips on 2005-10-25
Can you ping the Loopback interface, 127.0.0.1  ???

---

### Post by B0rsuk on 2005-10-25
Yes, I can ping localhost, or 10.112.0.19. 127.0.0.1 - too, if I remember correctly. Sorry for forgetting to mention that.

---

### Post by byourg on 2005-10-25
Are you trying to network the two computers, or just using the internet connection off the Debian machine? If you are trying to network the two computers, what are you using as a router or hub?


Reread the post, sorry. To get rid of the syncronizing clock deal, do "sudo update-rc.d -f ntpdate remove" in a terminal to stop it. If you have one of the live-cd's boot up with that and see if it picks up the internet, then look in the /etc/network/interfaces file and see what's in there.

Get a cross-over ethernet cable to update the Kubuntu machine using the Debian machine as a gateway. There are a lot of KDE updates if you just did a new install. I updated my laptop twice. Had a problem the first time, now everything is fine.

---

### Post by B0rsuk on 2005-10-26
Thanks for tips.

I could try to update my machine using Debian as gateway, but it's a short-term solution. I really need inet on my machine, cvs (university), mail, games, of course; and everything that needs root to be installed...and I cannot afford to have both computers up all the time.
DO you mean that after updating in similar way your internet started working ?

There's slim chance that inet will work after using Livecd, because Install cd can't do that. BUT some people say Hoary was more stable (and better at detecting internet) than Breezy. I may try Hoary. If it worked, it would make my task much easier (perhaps kernel bug in Breezy ? Someone suggested that)

HMM. **I noticed something strange.** I have a dual boot machine, you know, and I can't manage to configure win xp inet, either ! Could that mean there's something about network's configuration I don't know ? (It suggests my problems aren't system dependant, but I already ruled out hardware error - sort of).  I really need to catch the admin !

---

### Post by byourg on 2005-10-26
> DO you mean that after updating in similar way your internet started working ?

Yes, ethernet hookup is better since update.

> eth0    Link encap: Ethernet HWaddr 00:11:D8:1E:85:08
inet addr: 10.112.0.19 Bcast:10.112.**15**.255 Mask 255.255.240.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
RX packets:8922 errors:0 dropped:0 overruns:0 frame:0
TX packets: 75 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000

The 15 in the broadcast address should not be that, it should be 0 to match the Debian machine.

---

### Post by B0rsuk on 2005-11-08
**SOLVED**

The problem was trivial - I had no idea about hardware adresses of ethernet cards. One trip to the admin explained everything. Everything I did to that point was correct (more less), but not enough. My admin had to add the hwaddr to some kind of "allow" list.

I repply just to make sure no one wastes time trying to help me. And so that Ubuntu doesn't take unreserved blame.
It works very nice so far.

---

### Post by mips on 2005-11-08
What happend here? Brief explanation follows, after the fact:

Every single network card has a unique hardware address called a MAC (Media Access Control) address that is generally expressed as a hexadecimal value, ie. 0123.4567.89ab or 01-23-46-89-ab depending on the platform you are working from.

The switch the other end of the LAN cable plugs into has the ability to enable port security if so desired by the administrator. This means that only LAN cards with a valid MAC address as determined by the Admin will be allowed to work on that switch port when plugged in and no other address will work. This is a security/access feature on the switch to prevent any tom, dick & harry siply plugging into the network and gaining access.

---

