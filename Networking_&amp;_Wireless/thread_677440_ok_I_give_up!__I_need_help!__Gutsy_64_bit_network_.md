---
title: "ok I give up!  I need help!  Gutsy 64 bit network problem 88e8001 gigabit ethernet"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by jpross81 on 2008-01-24
Ok guys I have been reading and reading and cannot get my network connection to work!  
I just did a clean install of gutsy-64bit and I am unable to connect to the internet at ALL.  

I have a p5nsli motherboard with an integrated ethernet gigabit LAN.  When I type lspci it shows my ethernet controller: Marvell Technology Group Ltd. 88e8001 Gigabit Ethernet Controller (rev 13).

In gusty terminal I cannot ping anything and nslookup returns "connection timed out; no servers could be reached"

I am using a WIRED connection and have no wireless adapter.

When I boot the machine into XP everything works fine in XP. ( I have disabled the LAN power management feature of XP)

Oh and I guess I should mention that I had fiesty-32 bit on this same machine and had everything working fine.

Please help me out guys! I miss my ubuntu box!

Any suggestions?

---

### Post by wieman01 on 2008-01-25
Reverting to 32-bit might be a solution if you don't want to go through this. I mean it, 64-bit can be a bit of a headache. Occasionally.

---

### Post by jpross81 on 2008-01-25
Switching back to 32-bit is one option I am thinking about.  The only thing is that I have 4 gigs of memory.  Is there an easy way to get all 4 gigs working?  This box is going to be used as a server for the most part.

---

### Post by jpross81 on 2008-01-29
Well after some more research I ended up installing another network card to at least get my machine connected to the internet.  The new card worked for a little and then would break after a certain amount of usage until I restarted the computer.  Even after I did that the connection sometimes wouldn't work.  Anyways I used this opportunity to try another distro.  With openSuse10.3x64 everything for the most part worked, but as I am typing this it keeps locking up.  I guess my machine just doesn't like to run at 64 bit.

---

### Post by jpross81 on 2008-02-04
After I have tried, opensuse 10.3, fedora 8, centos 5.1, gutsy, and fiesty (all x86_64) and had the same problem with each of them. 

Turns out the problem is that my motherboard (P5NSLI) has some sort of problem supporting 4 gigs of ram while allowing access to the integrated gigabit LAN.  I took out 2 1-gig sticks and when I booted everything started to work fine.

My next step is to buy a new gigabit NIC and replace the four gigs.

If that doesn't work, I guess I am going to go to work on a new motherboard.


My current working setup:
P5NSLI mainboard
P4 2.8 intel CPU
2 gigs ram (have the other 2 to put in)
8600gt nvidia 256mb video
500gig SATA hd
650 watt ps
fedora 8 x86_64

Any suggestions on a specific LAN card?

Any suggestions on a new 775 mainboard with integrated network card? under $300

---

