---
title: "[SOLVED] SLOW transfer using NFS - 1 hour to do 10 gigs?"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by bluepowder7 on 2008-02-25
i managed to get NFS set up on my server and laptop (client), and i'm now moving files to the server.  however, i'm noticing that the transfer is incredibly slow.  using the regular System Monitor, it looks like i'm sending files from my laptop at no more than 3MB/s.  shouldn't it be flying across from the laptop to the server MUCH faster than that?

here's how i set up the storage drive that's inside the server (this is the line in my /etc/exports file):
```

/sata_nas 192.168.1.53(rw,sync,no_root_squash)

```

where /sata_nas is the LVM'd storage drive on the server, and the IP address is of my laptop


and this is in my server's fstab file:

```

/dev/sata_volume_group/sata_nas     /sata_nas    ext3    defauts   0    0

```




and here's how i mounted it from the client laptop (so far, from the command line only, not yet set up in the fstab)

```

sudo mount server1:/sata_nas /mnt/sata_nas

```

where server1 is the hostname of my server box



are there settings that i should change on either of those?



.

---

### Post by Sam Lars on 2008-02-25
Looks pretty basic to me...
Do you get faster transfer with anything else?  Can you look at the machines to see if ether one is peaking CPU or I/O?

---

### Post by bluepowder7 on 2008-02-25
this is the only approach i've tried, and being a noob it took me quite a while to get set up this far!  :P

i have the system monitor on the laptop up all the time, and the dual CPUs are not taxed at all.  no more than 20% each.  dunno how i can check stats on the server, though, since all i have is a terminal window open on the laptop and connecting via ssh to the server.

i'm just thinking - if the network interfaces are basic 100Mb/s (10/100Base-T), then i should be able to hit 10MB/s (megabyte), but it's loafing along at less than a third of that.

oooh - are WiFi interfaces on modern laptops slower than 100Mb/s?  my gateway lappie has the broadcom / dell 1390 wifi guts.  maybe i can try hooking up the laptop using the ethernet cable - going wired?

---

### Post by bluepowder7 on 2008-02-25
son of a ......

it WAS the WiFi that was limiting it.  i didn't know that 802.11g was around 30Mbit/sec.  i thought it was faster.  i went wired, and now my transfers are in the 8MByte/sec to 10MByte/sec range.  that's about 3 times faster, and sort of what i would expect with 100Base-T.

hmm...  how can i check if my laptop, server, and router are capable of gigabit rates?  or rather, which is the limiting piece?

---

### Post by Sam Lars on 2008-02-25
Yeah, 3MB/s is about the max my wireless gets.  It's technically 54 Mb/s, but you have to have a really strong signal...
The limiting factor is the weakest link.  For Gigabit, you need Gigabit adapters, Gigabit cables, and a Gigabit-supported router...
If you look in ifconfig it should tell you link rates, and you can research your hardware to find out what it can operate at.

---

### Post by bluepowder7 on 2008-02-26
hmm, the router (linksys wrt54g) is only spec'd for 10/100, so that would need an upgrade.  ditto the laptop.  and the desktop.  hmm, server mobo has gigabit lan, so that's cool, but useless since nothing else has it.  bugger.  i guess at this point, the cables being different is moot.  :p

---

### Post by kaginken on 2008-02-26
NFS is the combination of the two slowest things on a computer - disk drives and network.

Especially if you're wireless...you can't expect much more speed than that.

If you're REALLY feeling saucy - try copying the same 10Gigs with a wired connection - see what happens.

God Speed, John Glenn.

:popcorn:

---

