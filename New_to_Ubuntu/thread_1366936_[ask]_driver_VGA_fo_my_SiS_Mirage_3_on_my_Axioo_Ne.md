---
title: "[ask] driver VGA fo my SiS Mirage 3 on my Axioo Neon MNC"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by ancruk on 2009-12-29
can someone help me how to get SiS Mirage 3 VGA driver for my laptop Axioo Neon MNC??? I'm using ubuntu 9.10.
thak's before

---

### Post by cariboo on 2009-12-30
Could you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C display
```

and paste the output into your next post. The above command will tell us if the proper drivers is being loaded.

---

### Post by vanillablue on 2010-01-01
Hello,
I also use Axioo Neon MNC with SIS mirage 3 and I have the same problem with resolution.
I already tried to install the driver for SIS, but it doesn't seem to have any effect.
I tried to type the command that you give and here is my result:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff(prefetchable) memory:d8000000-d801ffff ioport:9000(size=128 )

Please help, I'm desperate.
Should I try to create an xorg.conf file?

---

### Post by chickencaesar on 2010-01-01
Try this thread for all of your SiS 771/671 woes:

[http://ubuntuforums.org/showthread.php?t=958967&page=27](http://ubuntuforums.org/showthread.php?t=958967&page=27)

---

