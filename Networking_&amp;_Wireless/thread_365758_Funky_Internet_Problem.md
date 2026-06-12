---
title: "Funky Internet Problem"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by aquanet1987 on 2007-02-20
Hi, I am rather new to ubuntu and linux and I am having some problems.  I like my new OS enough to want to work through them, so any help would be very appericiated. 

I am connected to the intenet via my ethernet card with connects to my colleges network.  Just surfing around I have no problems, I can open up pages fine.  The minute that any big chunk of information is need to be handled, just a update download or even a pdf file, the connection stops working and will remain useless untill the computer is restarted.

Any Ideas on why this is happening, any possible fixes?  Thanks!

---

### Post by gradedcheese on 2007-02-20
hmm... when this happens (as a test) try opening the shell, Applications->Accessories->Terminal and run running:

```

sudo /etc/init.d/networking restart

```

(if you've never used the shell: you type or paste that in, and press Enter to run it)

Incidentally, what network card are you using?  If you run "lspci" in the shell, it will output all of your PCI hardware.  Post the output here, or just the line that begins with "Ethernet Controller".

---

### Post by aquanet1987 on 2007-02-20
Thanks!  This is what the terminal gives out for data.

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4352 (rev 14)

and this is what the device manager in windows gives off for information

Generic Marvel Yukon Chipset based Gigabit Etheret Controller.

---

### Post by Strider on 2007-02-20
Try using mii-tool (CLI/console) to set the speed of the network card.  I've seen weird issues with gigE network cards when set to AUTO.

To use mii-tool to change speed do the following:

mii-tool -v <interface> # this will list the capabilities of the card

then use:

mii-tool -F <speed settings from above> <interface>

I would set it to 100base-T-FD (full duplex).

You can also use "ethtool" to query settings of the NIC.

See that helps.

-Mike

---

### Post by aquanet1987 on 2007-02-20
Where do I do that?

I take it not the terminal, but where?

---

### Post by gradedcheese on 2007-02-20
the terminal

---

### Post by Strider on 2007-02-20
> **aquanet1987 said:**
> Where do I do that?

I take it not the terminal, but where?

In a terminal window and you'll have to root to do run these commands.

---

### Post by aquanet1987 on 2007-02-22
This is what I am getting

---

### Post by aquanet1987 on 2007-02-22
This is what I am getting,

chris@chris-laptop:~$ sudo mii-tool -v
Password:
eth0: no autonegotiation, 10baseT-HD, link ok
product info: vendor 00:50:43, model 8 rev 3
basic mode: autonegotiation enabled
basic status: autonegotiation complete, link ok
capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
advertising: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
link partner: 10baseT-HD
SIOCGMIIPHY on 'eth1' failed: Operation not supported

What does eth1 failed mean?

I am having trouble finding the right syntax to use the mii-tool command. If this is what I need to be doing, could someone help me out with this?

Thanks!

---

