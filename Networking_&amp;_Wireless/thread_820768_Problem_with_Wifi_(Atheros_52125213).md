---
title: "Problem with Wifi (Atheros 5212/5213)"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Cpudan80 on 2008-06-06
** Duplicate of my post in the general forum -- sorry **

Hello all:

My wifi on my Thinkpad T42 (with an Atheros 5212/5213 chipset) suddenly broke on Hardy. The restricted module is enabled but it says "not in use."

I haven't messed around with the system too much lately - so I dont know what's up.

The only thing I can see is that I get an error on bootup:

* Enabling additional executable binary formats binfmt-support
mount: can't open /etc/mtab for writing: No such file or directory
update-binfmts: warning: Couldn't mount the binfmt_misc filesystem on /proc/sys/fs/binfmt_misc

Any ideas about how to fix the wifi? Booting to the ...17 kernel doesn't fix the problem (currently at ...18 )

The wifi works fine off the LiveCD -- so there is no problem with the hardware

Thanks

Dan

---

### Post by SnowTDM on 2008-06-06
Try to disconnect and connect wifi again when you are logged.

If it doesn't solve the problem, could you type "lsusb" and show the output? It will tell you the model of your wireless card and maybe we can help you.

Thanks

---

### Post by Cpudan80 on 2008-06-06
Thanks - I actually fixed the problem - I did an fsck on my HDD and that found some errors, now it works.

Dan

---

