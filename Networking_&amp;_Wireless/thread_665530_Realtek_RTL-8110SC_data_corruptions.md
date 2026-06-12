---
title: "Realtek RTL-8110SC data corruptions?"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by crouchingturbo on 2008-01-12
Just installed Gutsy on a new computer.  The motherboard is an Abit IP35 Pro, with two Realtek RTL-8110SC gigabit ethernet interfaces on-board.

I'm getting occasional data corruptions when I transfer large amounts of data over the interface.  The first sign was the sun-java6-bin package failing to install a couple times, because the hash mismatched.  I'm able to reproduce by doing a large scp from one PC to another, which, at some point (randomly) will bomb out with: "Disconnecting: Corrupted MAC on input."

I've tried both interfaces and the error occurs on both.

Hardware:
Abit IP35 Pro motherboard with two RTL-8110SC interfaces
Intel Q6600

Software:
Ubuntu 7.10 amd64 (text installer used for RAID)
Kernel 2.6.22-14-generic, using r8169 driver for network

Any ideas?

---

### Post by crouchingturbo on 2008-01-12
Another data point, I just installed an old Netgear 10/100 card into the system, and it works perfectly.  So that pretty much rules out things like bad RAM, bad HDD, etc.  It's definitely down to the Realtek hardware itself, or the Linux drivers.

---

### Post by crouchingturbo on 2008-01-13
Ok, things got progressively worse, and now the computer won't boot.  The Ubuntu boot CD goes straight into a kernel stack dump, and it's a different stack dump every time.  I tried to install Windows, for kicks, and it got about 20 minutes into it, then blue screened.

Since the RAM passes memtest86, and I think the CPU is reliable, I'm blaming the motherboard.  Time to RMA.

---

