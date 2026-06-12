---
title: "Acer Aspire one wifi issues"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by rm2011 on 2009-02-21
Hello, 
I have just installed ubuntu 8.10 on my aspire one.  I successfully got wifi to work with the guide at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)  however, I did an update and it is no longer working.  It says: Every time there is a kernel update you will need to perform the following steps to make the wireless work. Go to the directory (madwifi-hal-0.10.5.6-r3835-20080801) and run:

make clean
make
sudo make install

however, im not really sure what this means.  Could someone please explain it?

---

### Post by sonicb00m on 2009-02-21
> **rm2011 said:**
> Hello, 
I have just installed ubuntu 8.10 on my aspire one.  I successfully got wifi to work with the guide at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)  however, I did an update and it is no longer working.  It says: Every time there is a kernel update you will need to perform the following steps to make the wireless work. Go to the directory (madwifi-hal-0.10.5.6-r3835-20080801) and run:

make clean
make
sudo make install

however, im not really sure what this means.  Could someone please explain it?

It means you have to recompile and reinstall the driver every time a minor kernel update in Ubuntu is downloaded. It's a real pain in the ***.

I've put PcLinuxOS on mine until Ubuntu sorts this out with a future build. At least my wireless doesn't break down every 4 days.

---

### Post by pparks1 on 2009-02-21
Of course, you could exclude the kernel from updating rather than having to deal with recompiling the drivers so frequently.   If your box is running stable and the kernel is not causing a problem, you may not really need the new kernel.

---

### Post by Panzor on 2009-02-21
> **pparks1 said:**
> Of course, you could exclude the kernel from updating rather than having to deal with recompiling the drivers so frequently.   If your box is running stable and the kernel is not causing a problem, you may not really need the new kernel.

Good advice. That's what I do now that I made my xorg.conf file all funky and strange (dual monitors ftw). Just keep your /boot/grub/menu.lst file clean of the new kernel (should ubuntu decide to already add it) and you should be good. Unless you're worried about the new kernel using up a few MBs...then it'll be more complicated, but doable.

---

### Post by rm2011 on 2009-02-21
ok, but for now how do i reinstall the driver?

---

### Post by sonicb00m on 2009-02-22
> **pparks1 said:**
> Of course, you could exclude the kernel from updating rather than having to deal with recompiling the drivers so frequently.   If your box is running stable and the kernel is not causing a problem, you may not really need the new kernel.

How do you do this so that the update manager doesnt constantly bug you about updates?

---

### Post by nothingspecial on 2009-02-22
If you still have the original madwifi directory you downloaded and extracted from madwifi you need to cd into it before you make clean.

If you deleted it follow the original instructions again but this time don`t delete the madwifi directory.

---

