---
title: "DGE-528T very slow transfer"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by Frunktz on 2008-04-19
Hi!
I've tested the card with WindowsXP, Ubuntu 7.10 and 8.04..

Transfer with samba:

On WindowsXP the transfer rate it's around 25-30 MB
On Ubuntu 7.10 using CIFS => 500 kb/s
On Ubuntu 7.10 using SMBFS => 6000 kb/s

On Ubuntu 8.04 using CIFS => 60 kb/s
On Ubuntu 8.04 using SMBFS => 100 kb/s

They are very very slow. Anyone has resolve that issue?
I use have r8169 module..

Thanks a lot

---

### Post by gerni on 2008-04-22
exactly same problem here... works with windows, but extremely slow with linux :(

---

### Post by blastus on 2008-04-22
This is why I'm going back to NFS. I really like Samba for its security (NFS has no security) stability (unmounting an NFS share that no longer exist causes my Ubuntu client to completely lock up) and configuration (being able to name shares) over NFS but Samba's performance makes it pretty much useless. 

NFS is 4 to 5 times faster on my network than Samba. I have searched the Internet high and low for a solution and no-one really seems to have one that is supposed to work. This is a problem with Samba--no other network application I have has this problem.

---

### Post by Frunktz on 2008-04-26
How much is the transfer rate with NFS?
I think 20-25 MB is very slow with a gigabit..

hdparm -tT /dev/XXX show about 55 Mb/sec...

I can imagine a transfer of about 50 MB/sec obvius with read/write I can have full speed but about 35-40 MB...

---

### Post by djamu on 2008-04-28
same here.
server has dge-530t linux only
desktop has dge-528t dualboot linux / XP

transferring speed 

server > desktop linux 150kBs
server > desktop XP 28MBs
dektop ( any ) > server 28MBS
(desktop has old pata drive )

generating additional traffic speeds up transfer 

ping -i .015 192.168.1.11  (server IP) from linux desktop speeds up transfer > 10MBs
( -i 0.015 forces a ping every 0.015 sec )

downloading 2 files simultaneously normalizes speed ( server > linux desktop )

I've observed this on another occasion ( at a friends house ), but then I was blaming the router ( I should check he has the same nic ) [COLOR="Blue"]EDIT: he's using the same card[/COLOR]

can anybody confirm previous tests ( creating additional traffic )
XP filesharing & samba server uses different ports ( 137-139 )  then 
 samba <> samba ( 445 ) so my guess is that this causes the difference in speed between platforms 

1 dirty workaround would be to force cifs / smbfs on the same ports that XP is using.

I'll try to recompile latest driver & see what that gives ....


:(

---

### Post by axel_oxenstierna on 2008-04-29
Same problem here. I have two 528T cards (8169) connected via a 1 GB switch and only get -8-9 Mbit/S. I think that 20-25 should be OK in real life.

---

### Post by djamu on 2008-04-29
> **axel_oxenstierna said:**
> Same problem here. I have two 528T cards (8169) connected via a 1 GB switch and only get -8-9 Mbit/S. I think that 20-25 should be OK in real life.

do you mean MBs or Mbs  ( Mbyte/s vs Mbit/s  ), if former then depending on the quality of your network / computer it aint that bad. If latter then even 20 - 25 is bad ( Gb = 1000Mbs ) 
Just to say it's a Gb switch not a GB switch > which is in that case a 10Gb one..

I have been fiddling with the interrupt mechanisms ( the extra traffic generates extra interrupts ) but to no avail ... switching APIC LAPIC notimerinterupps noirq's ACPI etc.. ( noapic + acpi=off ) did speed things up ( doubled ) which is not nearly enough ( from 150KBs > 300KBs lol ) if not only to rule out this as a cause...

I did find some weirdness while hex examining the driver... ( driver hacking skills became a little rusty lately ) I'll continue in a couple of days... 

:lolflag:

---

### Post by Frunktz on 2008-04-30
I've changed the card. On windows I have used that 528T on windows that works perfectly..

I've bought another 530T..I think that I can't have speed over 20-25 Mb/s because the PCI bus is the bottleneck...Socket A -> 1600+

Bye

---

### Post by djamu on 2008-04-30
> **Frunktz said:**
> 
I've bought another 530T..I think that I can't have speed over 20-25 Mb/s because the PCI bus is the bottleneck...Socket A -> 1600+
Bye

You mean 20-25MBs > then the pci is the bottleneck ( certainly if it's an old 33Mhz bus ( the newer mobo's have a 66Mhz )

if it's 20-25Mbs like you wrote then it's still way to slow ( B=bytes b=bits)

---

### Post by Frunktz on 2008-05-01
Sorry..
20-25 MB/s :D....I must search some info about my motherboard model...99% bus is 33 Mhz..

With iperf bench I've got about 400-500 Mbit/s => 50 MB/s
99,9% confirm bus PCI bottleneck..

---

### Post by thavinci on 2008-06-09
Anyone know where the problem lies?

I just converted from FreeBSD to ubuntu only to find out nothing worked out for me.

Same slow speeds issue here.

Using DGE-528T

---

