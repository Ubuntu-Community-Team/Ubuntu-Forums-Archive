---
title: "LAN speed help question"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-02-22
So my questions is how can I make transfer speeds faster wireless from ubuntu to my NAS? The reason i bring this up is because I get 4 different results when i transfer to the NAS. 

I have a Wireless N card in my computer and my NAS is hooked up to my wireless N router via Ethernet.

Right now i am running 10.10 and when i transfer a file to my NAS my speed is around 1.8 MBps.

My second trail was when I had 10.04 installed. When that was installed my speeds were around the 3.5MBps range.

My thrid trail was with the ubuntu 10.10 live cd (USB drive).  When i used it wirelessly I was getting about 5.5MBps

And forth was when I transfer with windows 7. I get around 4.5MBps.

My question is how can I increase my transfer speeds and why does the speed vary by the OS i am using?

Thanks

FYI all of these tests are done on the same computer at the same time of day.

---

### Post by cariboo on 2011-02-22
Check what driver it is using when you boot from your usb device. You haven't told use what your wireless device it, so it's kind of hard to help any further without the correct info.

---

### Post by hunter99507 on 2011-02-22
I have an intel 5100 agn. I am not sure if that helps.  I have been doing some reading and i dont know if this information will help.

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
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x00000000 (0)
    Link detected: yes
```

I read that i should type this command in but it doesnt work.  Any suggestions?
```
watts@watts:~$ sudo ethtool -s eth0 speed 100 duplex full autoneg off
Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg
```

---

### Post by hunter99507 on 2011-02-22
So i have figured out a little more information. I went into my router settings and it says my computer is connected at 10Mbps via ethernet.  How do i change this?  My computer and router have Gigabit ehternet.

---

### Post by grahammechanical on 2011-02-22
I have two onboard ethernet adapters and hence, two ethernet ports, eth1 is PCI Gigabit and eth0 is PCI-E Gigabit (the fastest). Which one is in use depends on which ethernet port I plug the cable in. Those on the back of the computer, I mean.

Regards.

---

### Post by hunter99507 on 2011-02-22
I have 1 gigabit ethernet port that runs at 10Mbps, none duplex.  How do i change that to run at 100Mbps or even 1000Mbps?  Also how do i change the settings on my wifi card as well?

---

