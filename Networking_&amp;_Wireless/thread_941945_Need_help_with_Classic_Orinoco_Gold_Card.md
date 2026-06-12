---
title: "Need help with Classic Orinoco Gold Card"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by caligula08 on 2008-10-08
distro:               Ubuntu 6.06.1 LTS
kernel:               2.6.15-26-386
card chipset:       Hermes1
firmware:           8.72
driver:                0.15rc4 (0.15 will NOT compile)
aircrack-ng:        0.9 (1.0 will NOT compile)

the problem:  airodump-ng stops capturing after about 18 to 20 beacons.... driving me nuts trying to figure out why
have done everything:  removed Network Manager, removed wpasupplicant, ect

if anyone can point me in a direction to the solution, i will be very grateful ...
thx

---

### Post by offensive_jerk on 2008-10-12
I have the same issue with the Orinoco card dieing after running Kismet for a few seconds. 

Kismet will work fine for a couple seconds, then the card will stop.

Does your card do the same in Kismet?

---

### Post by caligula08 on 2008-10-13
yes... i have compiled about 7 different kernels now... from 2.6.11
to 2.6.18 ... and tried every drive, from 0.13e-SN-12 to 0.15 ...
they all fail. 

the closest success i've had is with 0.15rc4 which does put the card
into monitor mode but then both airodump-ng and kismet stop after a few
seconds.  also, iwpriv does NOT show the monitor method.   i believe
that iwpriv MUST show this exposed method in order to get this card to
work properly.

but my problem is i only have 256 Mb until 2 more weeks when i will 
upgrade to 512.  so i can't really test Hardy yet on it.  but there
is definitely a problem with the drivers for this card.  Roskin claims
that PCMCIA changes so frequently that the people who write the drivers
cannot keep up.  and monitor mode/pkt injection is definitely being 
downplayed in the industry.   they act like it is some kind of
secret tool to overthrow the gov't or some crap like that.

am contemplating buying Alfa AWUS036H but i keep reading that it has
problems under Linux.  what the hell is really going on here???

wish i could figure out a new approach ... also the Classic Gold Card
is only 802.11b.  i think that will make it miss 802.11g packets, no?

---

