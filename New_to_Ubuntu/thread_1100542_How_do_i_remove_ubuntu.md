---
title: "How do i remove ubuntu"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by pja944 on 2009-03-19
I have a clean install on my laptop with no other operating system on it. I want to remove this as I have now got the original drivers and setup for this laptop. I have checked out some threads but they all refer to dual boot or programs i dont have.

could someone please help I can boot into safe mode but there I get stuck.

Thanks

---

### Post by taurus on 2009-03-19
Boot from Ubuntu LiveCD.  Then open gparted (System -> Administration -> Partition Editor).  Highlight the swap partition and click the right button of your mount and run swapoff to unmount it.  Then, delete all the partitions.  Now, create a new one that takes up all the space of your harddrive and format it as ntfs.

Now, reinstall whatever OS you want.

---

### Post by BDNiner on 2009-03-19
You can put in the windows CD and select format the whole drive and install windows. That will completely remove any data on your computer before installing windows.

---

### Post by mcla0203 on 2009-03-19
Find the key to enable you to choose a boot device.  It's usually F12 or something.  Maybe different on some machines so google it.  Then select to boot from a cd, make sure you have a bootable cd in, like vista or xp, whatever you want to install.  Then when you install it just use the full hard drive so it overwrites the ubuntu stuff.

---

### Post by pja944 on 2009-03-19
I have attempted all the suggestions but have a problem. Ubuntu does not recognise any cd's in the drive and i cannot get past a password on my bios setup. Arrrrggggghhhh! 

Any ideas from here coz so far I have spent 8 hours on this and i'm tired, lol.

---

### Post by overdrank on 2009-03-19
> **pja944 said:**
> I have attempted all the suggestions but have a problem. Ubuntu does not recognise any cd's in the drive and i cannot get past a password on my bios setup. Arrrrggggghhhh! 

Any ideas from here coz so far I have spent 8 hours on this and i'm tired, lol.

Some laptops will let you select the boot device withe keys F11, or F12. You should find the info in the specs of the system from the manufacture.

---

### Post by pja944 on 2009-03-19
Done that but it asks for a password which i do not have. I tried no password, Admin and all of my own but it will not let me in.

---

### Post by overdrank on 2009-03-19
> **pja944 said:**
> Done that but it asks for a password which i do not have. I tried no password, Admin and all of my own but it will not let me in.

Hi and I have not seen a password that stop from selecting the boot options but if you can not get the bios password then you may remove the cmos battery and then reset the cmos. Password gone. :)

---

### Post by pja944 on 2009-03-19
Well taken my Sony apart to find this CMOS battery and its not there and now i have detached the wireless cables on the motherboard and it is now in pieces. so that was a great help.

---

### Post by Helios1276 on 2009-03-19
> **pja944 said:**
> Well taken my Sony apart to find this CMOS battery and its not there and now i have detached the wireless cables on the motherboard and it is now in pieces. so that was a great help.


Won't go back together for ya?

[http://www.computerhope.com/issues/ch000239.htm](http://www.computerhope.com/issues/ch000239.htm)

---

### Post by benerivo on 2009-03-19
If you can't boot from cd, how did you install ubuntu? If you did it from a usb stick, and you can't remove the cmos battery, then i think you are stuck. Try googling for your machine's default bios password.

---

