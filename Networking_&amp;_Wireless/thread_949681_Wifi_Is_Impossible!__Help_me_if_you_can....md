---
title: "Wifi Is Impossible!  Help me if you can..."
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by benf101 on 2008-10-16
First and foremost, I've been searching the forums for days.  There are about 6 or 8 different answers for my problem, none of which work.  (So please don't do that thing where you tell me to google it because it's already been solved.)

I have a new laptop (horray for me) and I cannot get it do find a wifi signal... and by the way, wifi is all around me right now, for the record.

After running the command lspci -v | less, I find out that my wireless card is one of these:
> 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
        Subsystem: Acer Incorporated [ALI] Unknown device 013f
        Flags: bus master, fast devsel, latency 0, IRQ 217
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
        Subsystem: Foxconn International, Inc. Unknown device e006
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f8600000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>


I think it's the second one.  I've read that the Atheros card drivers come with the madwifi package (or whatever you'd call it) so I downloaded it.  I also searched synaptic for atheros and downloaded the driver for it, but maybe the wrong one???? I'm not sure...

So when I say "it doesn't work", basically, it just doesn't detect any networks and so I'm stuck from the get-go.  Like I said, there is wifi all around me right now, so the issue is PROBABLY with getting a driver for my card.

If someone could tell me what to look for and how to resolve this I would be extremely relieved.  Feel free to talk to me like I'm an idiot because my problem with understanding a lot of the forum talk is when the brilliant answer is all encoded so that noobies can never learn from it.

A step by step response would be appreciated.  Thanks to the linux genius who helps.

---

### Post by benf101 on 2008-10-18
Is there anything wrong with bumping my own message?

---

### Post by chorltonian on 2008-10-18
Hi 

Have a look at [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/) to see if the chipset is supported on Linux, some are not.

Might be one of these: [http://ubuntuforums.org/archive/index.php/t-894177.html](http://ubuntuforums.org/archive/index.php/t-894177.html)

What do you get with 

lshw -C Network

?

Good luck!

---

### Post by benf101 on 2009-02-07
benjamin@GENIUS:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:d0:15:1c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.100 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by danni-la on 2009-02-07
If you haven't already tried this...

sudo aptitude install linux-backports-modules-intrepid-generic

give it a go it worked for me.

Cheers Danni

---

### Post by benf101 on 2009-04-23
It's 6 months later and I have resolved the issue.  I may never understand why it didn't work before, but I fixed it by trashing my previous install (which was 7.10 upgraded to 8.10) and installed a fresh version of Ubuntu 8.10.

Everything worked.... out of the box.

I love my new OS!  Thanks to whoever put that distribution together.  It's a great package.

---

