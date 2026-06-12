---
title: "VPN setup to checkpoint safe@office"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by sagyvolkov on 2007-05-21
Hi,

Have anyone successfully connected to a checkpoint safe@office (Which is, i think, a VPN-1 solution)? 
Anyway have any config scripts for openvpn/swan/racoon for connecting to such a checkpoint product?

Thanks.

---

### Post by sagyvolkov on 2007-05-21
Forgot to add, i'm on 7.04.

Anyone? Please....

---

### Post by marianom on 2007-05-23
There are some thread discussing this on the forums. Maybe not the same product but somehow checkpoint related. See [this one]("http://ubuntuforums.org/showthread.php?p=2708130") where you will find links to other discussions.

---

### Post by sagyvolkov on 2007-05-29
no thread is actually holding a solution.
this is really weird that there is no solution....

---

### Post by marianom on 2007-05-29
Oh, I'm really close to a solution using QEMU to virtualize Red Hat 7.3  (not the best solution but hey, at least is something). However, Valhalla comes with a kernel version a little bit different form the one requested by the SecureClient and it tends to panic :eek: when you run the SecureClient.
I'm trying to find the necessary rpm to upgrade the kernel, so far without luck. 

Let's see how it goes in the next days. I keep you guys posted.

---

