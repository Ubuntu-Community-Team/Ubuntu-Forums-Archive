---
title: "No network speed incrase after upgrading to gigabit"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by SogniX on 2006-08-02
Ubuntu Workstation acting as Server, has Gigabit NIC.
iMac Workstation (Core Duo), has Gigabit NIC.
Purchased a 4-port Netgear Gigabit Switch.
Gigabit lights on switch are on on both computer's ports, telling me that the connections should be at full capacity,

Yet xfering files between the two via SAMBA I get around 3 MB/s max xfer speed, which is exactly the same if I plug them both into a 100 Mbit hub... 

I was doing appletalk previously with even slower speeds.

What gives? Is there something in my settings at either computer slowing me down? cables? (I replaced both cables with no results) bad switch? bad NIC?

Any way to troubleshoot? I don't have a 3rd computer so I can't narrow it down further.

Help! :(](*,)

---

### Post by MetalMusicAddict on 2006-08-02
I noticed a difference between the same hardware (I have a SMC setup) using Ubuntu/Windows. Its weird. I dont know if its certain chipsets or what. My new gig stuff is nVidia based and seems faster. Only thing I have to go on is time as I dont know how else to test.

Some people also say Samba is also a factor.

---

### Post by SogniX on 2006-08-02
It finally dawned on me to make a crossover cable and see if there's any spede difference going directly between computers (don't ask me how I got it to finally work tho), anyway I tested it again and it seems I'm at a solid 6MB/s (which is only double over my wireless network of 3MB/s)... which is not all that remarkable at all of a difference...

So now I'm down to it either being:
my iMac (I hope not! it's pretty damned new)
the Ubuntu PC... 

I KNOW the NIC card is a Gigabit NIC, not too old either... 
Device Manager reports it as a RTL-8169 Gigabit Ethernet

Is there something I have to do for Ubuntu/Linux to xfer files at gigabit speeds? 

Does the amount of RAM in the PC affect xfers at all? (256 MBs of DDR RAM).

I can't think of anything else other than buying another NIC (argh!!!).

---

### Post by SogniX on 2006-08-02
> **MetalMusicAddict said:**
> I noticed a difference between the same hardware (I have a SMC setup) using Ubuntu/Windows. Its weird. I dont know if its certain chipsets or what. My new gig stuff is nVidia based and seems faster. Only thing I have to go on is time as I dont know how else to test.

Some people also say Samba is also a factor.

There is an advanced file manager for OS X called Path Finder, when copying files I get an estimated speed in MBs, which is my primary way of measuring... also time but it's more mental than actual time. :p

Still, gigabit should be smoking my wireless xfer speeds by a whole heck of a lot! not, just a little faster than it! :(

---

### Post by MetalMusicAddict on 2006-08-02
I know windows to windows I was gettin 12. I get my new sys tomorrow. Hopefully it will be better than my current 3.

Right now windows to my Ubuntu server I do get 12 but Ubuntu to the Ubuntu server I get 3. My new sys is nVidia based like the server so Im hoping it just boils down to chipsets. Sux cause I bought 3 of those damn SMC cards. :(

---

### Post by halfvolle melk on 2006-08-02
Fot gigabit networking I think you'll need Cat6 though I'm getting up to 6.5MBps over Samba with Cat5, so you may have another problem. What does this tell you?
```
sudo ethtool eth0
```

---

### Post by SogniX on 2006-08-02
> **halfvolle melk said:**
> Fot gigabit networking I think you'll need Cat6 though I'm getting up to 6.5MBps over Samba with Cat5, so you may have another problem. What does this tell you?
```
sudo ethtool eth0
```

Cat5e is rated for gigabit, which is the only reason I bought a box of the stuff. 
That command gives me :
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

---

### Post by halfvolle melk on 2006-08-02
> **SogniX said:**
> Cat5e is rated for gigabit, which is the only reason I bought a box of the stuff.
Yep, I just looked it up on Wikipedia. I'd better do it the otherway around next time :)

> That command gives me :
That looks fine. How about on the Mac side? I wouldn't know how to check that though.

---

### Post by SogniX on 2006-08-02
halfvolle melk,
no idea what the OS X equivilant to that would be either...

But anyway, I gave up for today and put my network back together (computers where using crossover cables, weird IPs, etc.), and just for the heck of it I tried another big file transfer...

AND I FINALLY GOT SOME SPEED!!!

Still not what I was expecting out of gigabit, but I'm now xfering at 18.7 MB/s! YAY! :)

So, what's different now that wasn't before? 
The only thing I can think of is having rebooted earlier, as the GUI also feels snappier than normal. So, RAM is my problem??? 
If that's the case I'll order some ASAP! :)

---

### Post by SogniX on 2006-08-02
Anyone know what speeds in MBs are the following:
10 Mbit
100 Mbit
1000 Mbit

I swear I'm supposed to be getting closer to 100 MB/s or more for Gigabit, but I could be wrong...

---

### Post by kerry_s on 2006-08-02
What about your internet service provider, could they be limiting you? Mine has a cap at 3mb, if we pay a little more we get 6mb...Might want to call and ask, we didn't even know about the cap till we called them up to ask.

---

### Post by SogniX on 2006-08-02
to answer my own question:

10 Mbit   = 1.25 MBs
100 Mbit  = 12.5 MBs
1000 Mbit = 128 MBs

---

### Post by halfvolle melk on 2006-08-02
Just out of interest, how did you reconfigure your network?

You figured it out yourself but a byte is 8 bits so 1mbyte/s is 8mbit/s. Please note that samba has overhead, ftp for instance has less.

150 Mbit is still not near a 1000Mbit. This might be limited to the write speed of your hard disk.

---

### Post by SogniX on 2006-08-02
thing is, I didn't reconfigure my network at all... I put everything back and rebooted the Ubuntu PC - clearing it's RAM.

I didn't figure anything out - Google did. :p

And I'm not expecting to get 128 MBs, I realize that, but I don't think I'm asking for too much wanting somewhere in the middle.

---

### Post by MetalMusicAddict on 2006-08-05
I just wanted to come back to this one. I recently built a new PC. Everything is nVidia on my network (becides wireless laptops) now and things are *LIGHTNING FAST*. Difference is night and day between the SMC stuff I had. Thumbnails for pics/video come up in a flash. Moving through a video is also like its sitting on a local HD. Its sick.

Im thinking it all comes down to the chipset drivers. Im using nForce2&4 chipsets.

---

