---
title: "Gigabit Ethernet - wtf mate!"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by nystagmust on 2007-01-23
Hey so I have a problem. I am a noob so keep that in mind.

I have two computers that i am trying to connect via a gigabit switch.

The stats from ethtool are provided at the bottom.

I did a transfer from one computer to the other and got a transfer speed of:
[COLOR="Lime"]
nystagmust@core2duoDesktop:~/Photos/2006/11$ scp 11.tar.gz 192.168.1.4:~
11.tar.gz                                     100% 1299MB   7.2MB/s   03:01 

nystagmust@NAS-reaves:~$ scp 11.tar.gz 192.168.1.3:~
11.tar.gz                                   100% 1299MB  18.8MB/s   01:09  [/COLOR]


I recently had to upgrade my driver for my ethernet card on one of my computers it is a 8111b Realtek built into a Asus P5b motherboard. 

The other computer has a linksys gigabit ethernet card.
The switch is a linksys switch.

After I upgraded my version of my driver ( r1000 v1.05 provided from realtek)
for some reason i can no longer vnc into my other machine.

Does this make sense??

Any reason why I am not getting full transfer speeds. ( these computers arent that old and I dont think i am running into any internal bottlenecks in the machines) 

The one that is acting as a server is a dell with a P4 2 Ghz.
Mine is very new Core2Duo and all the rest.

Thanks for any help!



[COLOR="Lime"]Here are the ethtool results:

nystagmust@NAS-reaves:~$ sudo ethtool eth1
Settings for eth1:
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
--------------------------------------------------------------------------------------
The other:

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
        Link detected: yes



[/COLOR]

---

### Post by netztier on 2007-01-23
> **nystagmust said:**
> 
Any reason why I am not getting full transfer speeds. ( these computers arent that old and I dont think i am running into any internal bottlenecks in the machines) 


I think you do run into bottlenecks. IMHO, transfer rates of 18MBytes/s and 22MBytes/s are *blazing fast* when using secure copy; I for myself haven't yet seen rates better than 7MBytes/s with SFTP, and that was with a 3Ghz Pentium and a 2x1.5Ghz UltraSparc III, both on Gigabit Ethernet. Keep in mind that the data stream has to be encrypted and decrypted during transfer.

Try the same thing with NFS, and then, while you're at it, install iperf from the universe repos and have a go at it, running it in client mode on one and server mode on the other machine, then vice-versa. I bet you'll see figures of a different order of magnitude!

best regards

Marc

---

### Post by RandomJoe on 2007-01-23
While you should be able to tune the drivers to get a little more speed, I would also agree you'll soon be hitting some machine limitations.  My setup is quite similar to yours, except for the brand of cards, and I do a fair bit better.

My standard video setup has my movies stored on a 2.4GHz PowerEdge server, and a 3GHz HT P4 hooked to the projector.  When moving large files between them using scp, I get about 20-22MB/s.  I tried using a 1.2GHz P3 machine for the server, and that dropped to 10-12MB/s.  When I went between the 3GHz HT and my new C2D machine, I got nearly 30MB/s.  Between the C2D and the 2.4GHz server it's again about 20-22MB/s.

The encryption overhead is definitely processor dependent.

Also, the quality of the NICs may be an issue.  I can't say for certain on that, but I've always thought Realtek and Linksys were rather on the cheap end of things.  I have Intel cards in all but the C2D system, which has the nVidia nForce chipset.  In the past, Intel and 3Com always seemed to be better in my (limited) experience...

One thought - does your switch support jumbo frames?  I made sure mine (SMC) did, as not all at the time had that.  Although now I think about it, I don't know for sure I'm even using jumbo frames on the NICs at the moment...  That's been a while and several installs ago!

Edit:
Just checked - no, I haven't been using jumbo frames (MTU still at the standard 1500).  Tried some transfers between the server and the C2D system.  With 1500MTU I was getting 24MB/s, when I set both systems to 9000 MTU, the rate went up to 28MB/s.  So a little improvement by using jumbo frames.

---

