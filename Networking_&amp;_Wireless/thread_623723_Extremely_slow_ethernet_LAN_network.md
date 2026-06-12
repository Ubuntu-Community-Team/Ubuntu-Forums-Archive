---
title: "Extremely slow ethernet LAN network"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by BuffaloX on 2007-11-26
Hi
I have a small ethernet 100 mbit LAN.
When I try to copy files from my server (Samba share), it is extremely slow.
Copying 4 Gbyte takes more than an hour in Ubuntu (both feisty and gutsy), but is possible in less than 10 minutes in windows.
Internet works fine. :confused:

The problem is with my main system using an Asus board with Nvidia Chipset with built in Marvel ethernet.

How do I:
1: disable auton egotiation, and make it fixed at 100 mbit full duplex
2: check/adjust buffers.
3: configure my network, beyond the very limited options in administration/network menu.

---

### Post by pete.dawgg on 2007-11-26
hi,
i think the best tool to do all that is the program **ethtool**.  just install and use it; the options might differ a little bit depending on the capabilitiess of the driver.

i've got a similar problem on two boxes and i haven't solved it to this day, but i think it has got sth. to do with the marvell-chipsets. network-copying with samba is the slowest, but with other protocols it's still much slower than the theoretical maximum. (and that's with all kernel-versions since about 2.6.4, internal and external drivers etc etc  etc)
I've kind of given up on it (the boxes are mainly used for other things, so i just don't copy dvd-isos or large backups over the network between thos two anymore :(  )

---

### Post by BuffaloX on 2007-11-27
Thanx

Maybe I get lucky. :)
If I do, I'll come back.

---

