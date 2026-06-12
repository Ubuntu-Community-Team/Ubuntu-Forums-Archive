---
title: "Dual Boot XP &amp; Ubuntu on DIfferent Disks"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by chandru4895 on 2008-12-13
Hello All,
I have XP on an internal HDD(SATA) preloaded by IBM when I purchased the system. I have recently purchased a 250 GB external HDD(SATA) USB mounted, on which I wish to put UBUNTU 8.04 Hardy Heron. How do I setup Grub to be able to boot either XP or Ubuntu.
I believe I could go ahead & install Ubuntu on the Primary partition of the ext Drive,including GRUB, disconnect the drive and boot as usual from internal drive for windows XP _OR_[COLOR="Red"][/COLOR] ensure BIOS is set to ext drive as boot device before internal drive; and then Boot with the external Drive connected, for UBUNTU. Is this assumption correct?
Have seen one POST with replies on a similar issue -one SATA & one IDE - but no final answers.
Be great to have some views on this business please - Thanks

---

### Post by nakama85 on 2008-12-13
> **chandru4895 said:**
> Hello All,
I have XP on an internal HDD(SATA) preloaded by IBM when I purchased the system. I have recently purchased a 250 GB external HDD(SATA) USB mounted, on which I wish to put UBUNTU 8.04 Hardy Heron. How do I setup Grub to be able to boot either XP or Ubuntu.
I believe I could go ahead & install Ubuntu on the Primary partition of the ext Drive,including GRUB, disconnect the drive and boot as usual from internal drive for windows XP _OR_[COLOR="Red"][/COLOR] ensure BIOS is set to ext drive as boot device before internal drive; and then Boot with the external Drive connected, for UBUNTU. Is this assumption correct?
Have seen one POST with replies on a similar issue -one SATA & one IDE - but no final answers.
Be great to have some views on this business please - Thanks

The only thing you have to do is set bios to boot on whatever drive you have grub on and then point grub to windows hd you can do this by adding somthing similar below to your grub menu list
```

#title		Windows xp(vista
#root		**(hd1,0)**

```

of course you would change **(hd1,0)** to whatever you have your windows on

---

### Post by tomtom1982 on 2008-12-13
Install Ubuntu with the alternate-CD. Here you can choose where GRUB will be installed.

If you want to install GRUB on your external drive, you can also take the desktop-CD an make a normal installation, but before you have to take your internal HDD up from the mainboard (or the power supply).

If you install GRUB on your internal HDD it will show you the alternatives to boot Windows or Ubuntu. But this will only be if your external HDD is on.

---

### Post by louieb on 2008-12-13
Do be careful. Let Ubuntu do the default Grub install and the machine will have to have the external drive plugged in order to boot.

By default GRUB stage1 will be installed in the MBR of the 1st internal hard drive.

The two most common ways around this are:

If your PC allows booting from an external USB device. Install GRUB stage1 on the MBR of the external drive.  Just before the install begins there is a summary page with a button labeled **advanced**. The option to change the stage1 location is there. 

The other option is to create a dedicated GRUB partition on the internal drive. [IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")   Do this and you'll learn a lot about GRUB and whole booting process. Good Luck.

---

### Post by chandru4895 on 2008-12-13
Hello nakama85,
Thanks for that reply. Will give it a try and come back.

---

### Post by chandru4895 on 2008-12-13
Thanks loads - tomtom1982 & loueb.
Will study all three replies I have so far, try out suggestions and give you folks a response shortly.
Thanks a lot so far.

---

### Post by chandru4895 on 2008-12-13
Thanks loads - tomtom1982 & louieb.
Will study all three replies I have so far, try out suggestions and give you folks a response shortly.
Thanks a lot so far.

---

