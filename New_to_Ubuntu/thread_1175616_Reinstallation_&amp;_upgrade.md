---
title: "Reinstallation &amp; upgrade"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by wc4r on 2009-06-01
I had a dual boot with v9.04 and Windows Vista.

I built a new PC, saving my old HDs. I lost my dual boot menu.
Can I simply use my Ubuntu DVD and reinstall it? Will it re-create the boot menu again? Will it keep my user files on the Ubuntu drive in tact?

I had the 32-bit Ubuntu version installed, can I easily reinstall with Ubuntu 64-bit instead?

Thanks!
Joe

---

### Post by Elfy on 2009-06-01
I assume that you had to reinstall Vista, doing that would have overwritten the grub bootloader - you can reinstall with the livecd. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

To change to 64bit you would have to install over the top of the existing install or install to a new partition.

---

### Post by techrascal on 2009-06-02
i need to reinstall windows xp...but i have a lot of data etc in my ubuntu.....how can i do this without losing that data........i hope this will not overwrite my uubuntu partition...
i have ubuntu installed in my external usb hard disk.....

---

### Post by Elfy on 2009-06-02
reinstalling grub just does that - it won't be overwriting data

installing 64bit over the top of the 32bit install _will_ overwrite data

if ubuntu is on the external remove it before you reinstall xp and it will not be able to overwrite any data - you will need to reinstall grub then or you won;t be able to boot ubuntu after xp has installed.

---

