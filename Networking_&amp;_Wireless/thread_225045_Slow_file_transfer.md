---
title: "Slow file transfer"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by adrenaline_nz on 2006-07-28
Hello all,

I have a Realtek 8169 1000mb network card installed and working under Unbuntu Dapper, network file transfers are extremely slow.

I have compared the speeds compared to my Windows partition on the same PC the results are below:

Nvidia 100Mb Onboard NIC:
Windows XP: 41sec File size 350.0MB
Ubuntu: 51sec File size 350.0MB

Realtek 8169 1000Mb NIC
Windows XP: 18sec File size 349.4MB
Ubuntu: Stopped counting when it went over 4mins 349.4MB

I have the files sitting on a Windows 2003 server the folder the files are in are mounted in Fstab with the following:
```
//blackbox/Video	/media/Video	cifs	username=nathan,passwords=Avbhci1	0	0
```

sudo ethtool eth0 gives me the following:
```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000033 (51)
        Link detected: yes
```

Is anyone able to help me with this?

---

### Post by dtfinch on 2006-07-29
I've had that problem a few times before, seemingly not limited to any OS or hardware, with gigabit being the only common factor. I'd get full speed one way, and 20kb/s the other, with severe packet loss.

I've had luck with a number of workarounds:
1) Try a different gigabit card.
2) Switch to 100mbit.
3) Try another distro :-( (Downgrading from Fedora Core 3 to CentOS 3 (2.4 kernel) solved it once)

I've also had two different gigabit switches that weren't entirely compatible, resulting in this same problem. Fast one way, modem speeds the other. I suspect that slightly increasing the inter-frame delay could solve the problem, but I lack the motivation to find out how to do such a thing, or if it can be done with most drivers.

---

### Post by adrenaline_nz on 2006-07-29
Thanks for the reply, I'll get another NIC and see what happens then. BEfore I do that though I'll see what happens when I change my GB switch for a 100mb one.

---

### Post by adrenaline_nz on 2006-08-01
I've installed a new NIC, a D-Link DGE530T, after some struggling with getting the drivers installed it's working, although I'm still getting the slow transfers!

I have plugged a 10/100 switch into the 10/100/1000 Router I'm using and plugged the PC into that and tranfers where just fine, albeit at 100mb.

So the problem seems to lie with my D-Link DGL4300 Router and Ubuntu.

Has anyone got any ideas on where to go from here, is there some diagnostic tools that I can run?

---

### Post by dtfinch on 2006-08-01
Longshot as root:
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
echo 0 > /proc/sys/net/ipv4/tcp_sack
If it works, see which one did it and add the setting to /etc/sysctl.conf.

You can try bypassing the switch with a crossover cable, to see if the switch might have problems. But if the same card in the same computer works when you run windows, it's probably a combination of the default configuration and the switch.

I saw a thread where someone solved the problem by rebuilding their kernel with netfilter disabled, but that was with an old 2.6.0 testing kernel.

---

