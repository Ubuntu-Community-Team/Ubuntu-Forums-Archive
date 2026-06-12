---
title: "Bluetooth Weirdness"
date: 2020-12-29
forum: Networking &amp; Wireless
---

### Post by el_bizarro on 2020-12-29
Hi Everyone..

So I upgraded my Kernel to allow my HyperX Cloud Alpha S Wired 7.1 Surround Sound Gaming Headset to work and I think I made a Minor Mistake..

Works fine on Lubuntu 18.04 (I Hate the Newer Desktops on the 20.xx Versions)

However when I try to use Bluetooth and Connect my Laptop to my Phone I get the Following.

"paired successfully but this device has no services which can be used with raspberry pi"

I'm assuming that the Kernel is geared more to the Pi than my 64Bit Laptop or is there a Little more Weird issues going on..

The Kernel I have is 5.7.0-050700-lowlatency

CPU is Intel(R) Celeron(R) CPU  N2830  @ 2.16GHz

Intel Corporation Wireless 7260 (rev 73)

Guess I need a replacement Kernel ?..

Thanks

Rob..

---

### Post by #&amp;thj^% on 2020-12-29
To be clear, are you now using 20.04 or 18.04. This needs an answer first.
I would first check and play with "pavucontrol,"
Dose it show there?
```
apt policy pavucontrol
```
This bug is now fixed in Ubuntu 20.04, because we are able to install hwe-edge kernel, which should be 5.8.0-28

---

### Post by el_bizarro on 2020-12-29
Hi and Yes I am still using 18.04

pavucontrol:
  Installed: 3.0-4
  Candidate: 3.0-4
  Version table:
 *** 3.0-4 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

Rob..

---

### Post by #&amp;thj^% on 2020-12-29
please re-read my previous post.

---

### Post by el_bizarro on 2020-12-29
Ahh so you added a bit. a Bug

well its not a huge issue.

Thanks..

Rob.

---

