---
title: "Gigabit ether running at 20MBs only."
date: 2010-04-17
forum: New to Ubuntu
---

### Post by powel212 on 2010-04-17
I have upgraded the hardware on all my systems to gigabit 1000BaseT but my Ubuntu server only runs at 20MB/s while all the other machines run between 80-85MB/s.

What am I doing wrong?

P.

---

### Post by drascus on 2010-04-18
suggest this question be moved to the Server Platforms Category..

---

### Post by Penguin Guy on 2010-04-18
One gigabit is not the same as one gigabyte.
1 gigabit = 125 megabytes.

Hope this helps.

---

### Post by new_tolinux on 2010-04-18
A chain is as strong as it's weakest link.....
Therefore, datatransfer goes as fast as the slowest link. If there is any switch/cable between your server and "the machine you are taking data from", you'll never get to gigabit speed.

By the way, 20 megabyte ~ 160 megabit. Because that's not a generic network speed, my best guess is that your non-network-hardware does not support higher speeds.

Edit: If I remember well, 20MiB/s _is_ about the maximum transfer rate you'll get with USB-pheripals. So I guess it's either you're using any USB-device to connect to the network, or you're using an USB-harddisk/stick.

---

### Post by powel212 on 2010-04-18
> **new_tolinux said:**
> A chain is as strong as it's weakest link.....
Therefore, datatransfer goes as fast as the slowest link. If there is any switch/cable between your server and "the machine you are taking data from", you'll never get to gigabit speed.

By the way, 20 megabyte ~ 160 megabit. Because that's not a generic network speed, my best guess is that your non-network-hardware does not support higher speeds.

Edit: If I remember well, 20MiB/s _is_ about the maximum transfer rate you'll get with USB-pheripals. So I guess it's either you're using any USB-device to connect to the network, or you're using an USB-harddisk/stick.

I have a new gigabit switch and there are 6 computers on my network with various operating systems. The Ububtu server is the only slow one.

It is different from the other computers in 2 ways other ways. It has an iDE hard drive, and the gigabit network card I bought for it is plugged into regular PCi slot.

Could be the HD slowing me down or perhaps the PCi card. The other computers have SATA disks and the MoBos have built in 1000BasT.

I guess I just wanted to ask if Ubuntu 9.10 needed to be told there was a gigabit system in play or if it needs some other configuration adjustment to run full duplex gigabit.

Thanks for the help

P.

---

### Post by tgalati4 on 2010-04-18
PCI bus normally runs at 33 MHz and the maximum throughput is ~33 MBytes/sec.  So that is one bottleneck.  SATA runs at 150 to 300 MBytes/sec depending on SATA1 or SATA2 and how it's implemented.  IDE is ~133 MB/sec with Western Digital IDE Raptors getting about ~77 MBytes/sec on a good day.

Since the PCI bus is interrupt driven, if it shares any interrupts, that will also slow down throughput.  Examine:

cat /proc/interrupts

So, newer hardware with built-in gigabit ethernet and SATA2 drives will naturally be faster.  Run the live CD on one of your newer machines and measure the performance that way.

---

### Post by powel212 on 2010-04-18
Thanks for the feedback.

I am guessing it is the PCi socket that is slowing me down then. I will test it and see if I can find a PCi-E gigabit card as I have one available PCi-E socket available on that board.

Thanks again.

P.

---

