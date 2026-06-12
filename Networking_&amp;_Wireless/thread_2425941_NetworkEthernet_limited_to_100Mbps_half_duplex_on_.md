---
title: "Network/Ethernet limited to 100Mbps half duplex on startup."
date: 2019-09-02
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2019-09-02
When I boot and run this command I get the following:

```

$ ethtool eth0

[FONT=monospace][COLOR=#000000]       Supported ports: [ TP ][/COLOR]
        Supported link modes:   10baseT/Half 10baseT/Full  
                                100baseT/Half 100baseT/Full  
                                1000baseT/Full  
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Advertised FEC modes: Not reported
        **Speed: 100Mb/s**
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: off
        MDI-X: off (auto)
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes
[/FONT]

```

And if I run a speed test, I get capped around 30 Mbps.  My internet speed from my ISP is 100Mbps.  

I dual boot, and in windows I immediately get 100Mbps.

If I run the following command

```
$ sudo ethtool -s eth0 speed 1000 duplex full
```

then I get my full 100mps download.

However, this command does not survive reboot.

This all started with a new router (Netgear R7800).  On my old router, I never had these issues.  I always got 100Mbps down on boot.

So a few questions.

1) Why would a new router change my computers default ethernet speed?
2) Is 'full duplex' what I want?  It defaults now to half duplex, but that is legacy, right?
3) After running the above command, it now turns 'auto-negotiation' to 'on'.  Is that better?

And most importantly

4) How do I fix this?  Is the command above the correct thing to do?  How do I make it survive reboot?


Info:
Kubuntu 18.04.2
Kernel 4.15.0-58-generic
ethernet connection (2) I219-v

---

### Post by SeijiSensei on 2019-09-02
Never seen this problem myself, but you can try

```
sudo echo 'ethtool -s eth0 speed 1000 duplex full' >> /etc/rc.local
```

Now reboot and see if that makes the fix permanent.

---

### Post by NertSkull on 2019-09-02
Yeah, I thought about doing something akin to that.  It just seems really 'hacky' to me.

But if that's my only/best option I can do that.  It just makes no sense to me that I changed literally nothing on my computer.  I just installed a new router and things are now different.  Same cables and everything.  

I feel there has to be something more going on that has a 'real' fix.

---

### Post by SeijiSensei on 2019-09-02
Well, sure, but do you want to futz with your computer, or do you want to use it?

---

### Post by NertSkull on 2019-09-02
Seems to be my eternal debate while using ubuntu/linux.

I mean yeah I want to use it.  But I always feel that when things aren't working 'the way they should' that I'm missing something else that is wrong and that I would like fixed. Especially if it could in anyway affect security.

For now I'll probably us rc.local.  But I'd still like to figure out what is going on if anyone has any bright ideas.

---

### Post by him610 on 2019-09-02
NertSkull,
Your post got me to wondering about my own connection using ethtool which is shown below with differences highlighted -
```

	Speed: 1000Mb/s
	[COLOR="#FF0000"]Duplex: Full[/COLOR]
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	[COLOR="#FF0000"]Auto-negotiation: on
	MDI-X: on (auto)[/COLOR]

```
These get set during installation. Don't know how to effect a change in them. It may have something to do with the quality of your Cat5/Cat5e cable to your router.

---

