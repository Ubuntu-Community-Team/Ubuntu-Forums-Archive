---
title: "internet connection thru windows ?"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by kiiz on 2008-01-03
it seem impossible to get my cdma phone to work on ubuntu:(.my new problem is how to make ubuntu use the internet connection on a windows system. previous attempt where unfriutful.the two systems couldnt 'see' each other.do i need smb for internet sharing.please help

---

### Post by Predator[23rd] on 2008-01-03
Hi!

No, you don't need SMB for ICS.

Activate ICS in Windows and give your ethernet card with a static IP.

Basically Windows will give your "internal" NIC a static IP (probably 192.168.0.1, can't remember at the moment ...). Give your Ubuntu box an IP in the same subnet (e.g. 192.168.0.2) and it should work. As gateway you have to use the Windows machine's "internal" IP (i.e. 192.168.0.1) ...

---

