---
title: "external cd drives  andnot found"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by \george Woodward on 2009-01-01
Just installed Xbuntu 8.04 on Dell L400 laptop Pentium 3 600mhz 256mb ram 8 gig hard disk using compete disk (was w2000). Smooth installation and working OK BUT cannot see external cd drive or USB memory stick. I have set authorizations but no change.I Probably something obvious I am missing?

I could not find a way to uninstall Xbuntu so

Thought I would load Ubuntu to delete Xbuntu so set bios to boot from Ubuntu CD=which is does but ends up back with Xbuntu .Grub file confusion ?

---

### Post by hyper_ch on 2009-01-01
post the output of ```
lsusb
``` and ```
sudo fdisk -l
```

---

### Post by gn2 on 2009-01-01
Have you set desktop shortcuts to be shown or hidden in Desktop properties?

---

### Post by \george Woodward on 2009-01-01
Bus 001 Device 001: ID 0000:0000  
george@dell:~$ 
and
Disk /dev/sda: 10.0 GB, 10056130560 bytes
255 heads, 63 sectors/track, 1222 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfafffaff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1164     9349798+  83  Linux
/dev/sda2            1165        1222      465885    5  Extended
/dev/sda5            1165        1222      465853+  82  Linux swap / Solaris
george@dell:~$ 

Thanks

---

### Post by nemilar on 2009-01-01
Can you unplug the drives, open a terminal, run:

```
 sudo dmesg -c > /dev/null 
```

plug in the devices, then run:

```
 dmesg 
```

and post the output?  Thanks.

---

### Post by \george Woodward on 2009-01-02
Hi
This time I can get no respnse in Terminal (I closed down ovenight and re booted) On my first try the first code asked for my password but would not accept any keyboard imput at that point. The second code produced a result but I decided to try both again after a reboot.
This time neither code produced a reponse, not even a request for a password, I confirm the fist time I replied Terminal worked as one would expect.
george@dell:~$ dmesg
george@dell:~$ dmesg
george@dell:~$ sudo dmesg -c > /dev/null
george@dell:~$  dmesg
george@dell:~$ 

Thanks

---

### Post by \george Woodward on 2009-01-02
Hi
This time I can get no respnse in Terminal (I closed down ovenight and re booted) On my first try the first code asked for my password but would not accept any keyboard imput at that point. The second code produced a result but I decided to try both again after a reboot.
This time neither code produced a reponse, not even a request for a password, I confirm the fist time I replied Terminal worked as one would expect.
george@dell:~$ dmesg
george@dell:~$ dmesg
george@dell:~$ sudo dmesg -c > /dev/null
george@dell:~$  dmesg
george@dell:~$ 

Thanks

---

### Post by \george Woodward on 2009-01-02
Thanks.
I cannot find this option in desktop properties (Xbuntu)

---

