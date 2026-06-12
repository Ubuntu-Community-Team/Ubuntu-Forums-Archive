---
title: "couple of issues"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by rock4christ on 2008-06-04
just installed Xubuntu Hardy Heron on a Dell Inspiron 5100 1. I cant use my usb drive. I get :mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

2. I cant get wifi to work. The info (password, Ip, Subnet) is correct. Im not sure of the model of the wireless card( I think it is a Broadcom 440x, but im not sure. how would I check?)

---

### Post by rock4christ on 2008-06-04
it seems to be a BCM4306 (if il looking at the right info in lshw)

---

### Post by chili555 on 2008-06-04
Please try this: [http://ubuntuforums.org/showthread.php?t=767372](http://ubuntuforums.org/showthread.php?t=767372)

---

### Post by rock4christ on 2008-06-04
The problem is synaptic is useless w/o an internet conncection

---

### Post by rock4christ on 2008-06-04
I don't know what to do. I have the fw-cutter downloaded from the windows laptop that has internet, but I cant put it on the other one because it wont recognize usb drives. also, my cd drive is broken.

---

### Post by chili555 on 2008-06-04
Can you walk it over to the router and hook up an ethernet cable and use your wired connection?

---

### Post by rock4christ on 2008-06-04
that'll work

---

### Post by rock4christ on 2008-06-04
didn't work. I still get nothing in Hardware drivers

---

### Post by rock4christ on 2008-06-05
I got the wifi working. I just need to get the usb figured out. here is the result of dmesg | tail:
[ 1337.364661] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1337.367757] sd 2:0:0:0: [sdb] 8027790 512-byte hardware sectors (4110 MB)
[ 1337.368761] sd 2:0:0:0: [sdb] Write Protect is off
[ 1337.368767] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1337.368770] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1337.368778]  sdb: sdb1
[ 1337.370243] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1337.370296] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1338.304921] UDF-fs: No partition found (1)
[ 1338.439427] ISOFS: Unable to identify CD-ROM format.



now what?

---

### Post by chili555 on 2008-06-05
I don't think your *dmesg | tail* tells us anything about your USB. Let's take a look at:```
dmesg | grep -e USB
```Thanks.

---

