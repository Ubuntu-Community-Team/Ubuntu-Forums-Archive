---
title: "Lenovo 710S with Intel-kabyLake-Chipset"
date: 2017-01-24
forum: Networking &amp; Wireless
---

### Post by krabelle on 2017-01-24
Hello, thank you for this idea with the hew-edge.
I bought a new Lenovo 710S with Intel-kabyLake-CPU  and made the partitions manually over graphic-installer.
I used a 16.04.1-desktop-image from January 2017.

All seems working with 16.04-Kernel 4.4.0.62/-59 but the standby is not possible. I lose and wireless wired-network (over USB-adapter) after every wake up completely.
So I decided to try hew-edge kernel. before I red 2 days in forum and search by google...

The  3 steps above worked fine. 
But only with the new hew-edge the Notebook stops after grub starting with "loading initial ramdisk". and I waited 5 minutes...tried STRG ALT F1 F2 .... 
with kernel 4.4.0-62 or -59 this don't happens.
BTW it also happens with kernel 4.9.5 from Ubuntu mainline.

ther are a lot of discussions and mystery bug-history about this.

for example like this:
kann es dass hier sein? [http://askubuntu.com/questions/829914/stuck-on-boot-on-loading-initial-ramdisk-or-dropped-to-busybox](http://askubuntu.com/questions/829914/stuck-on-boot-on-loading-initial-ramdisk-or-dropped-to-busybox)
bug: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1359689](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1359689)

I also tried this:
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX_DEFAULT=""

It brings me to an text boot then I can type the phasphrase for encrypted-partion. but it works only for the standard kernel.

Maybe it has something to do with efi-board and bios-config...

actually it seems that on February 2 some users will run into this problem with official hew stack?

Do you have an idea where I can address this problem? oh maybe my question should moved to another forums area.

---

### Post by howefield on 2017-01-25
Post moved to its own thread.

---

### Post by krabelle on 2017-01-26
ok thanks for moving but I think it shall be moved to "Installation & Upgrades".
in the meanwhile I finally found a similar bug. With AMD-CPU from 2013 but similar! I joined this ticket: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1659340](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1659340)


and the network-topic (standby/resume) sems to be an different problem than the kernel-boot-problem: (I will search similar issues in bugtracker.)


All seems working with 16.04-Kernel 4.4.0.62/-59 but the standby is not  possible. I lose and wireless wired-network (over USB-adapter) after  every wake up completely.
So I decided to try hew-edge kernel. before I red 2 days in forum and search by google...

---

