---
title: "Wubi Or Direct Install?"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by noobda on 2011-06-07
One Of Ma Linux Friend Told Me Dat 
Wubi Dont Show Actual Performance.
I Mean It Lags Or Bit Slow Then Actual Installation.
(Installing Direct On Your Drive).
I Like Ubuntu So I Want To See Actual Performance..

:confused::confused::confused:

Thanks In Advance

---

### Post by beew on 2011-06-07
I would go for a real install, if you are nervous about partitioning you can install in an external hard drive, it will give you all the performance because it is a real install. I can give you more details if you are interested in  doing that.

---

### Post by noobda on 2011-06-07
yes sir i do have 2 hard drives so i want to know can i install on other drive
and use windows along ?
without wubi?
will it effect ma windows drive?

without effecting ma old drive....?

---

### Post by beew on 2011-06-07
It is really simple.

1) Download a Ubuntu ISO and make a live CD or a live usb. You can make a Ubuntu live usb in Windows with LILI

You can download the ISO from here.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

This is the homepage of LILI
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)


You may want to check which Ubuntu release you want. 11.04 is the latest, but you can also get 10.10
or 10.04 LTS. You may want to do a bit of research before you decide.

2) Configure your BIOS to boot from usb (if you install with a live usb)

3)Then plug the live usb or CD in the computer and boot.

4) Attach the external hard drive you want to install Ubuntu into. Note its name. In general sda is your internal hard drive, you don't want to touch that. sdb maybe the live usb you install from and sdc would be the targeted drive to install Ubuntu into. If you install with a live CD instead of a live usb it will be sdb.

5) Click install Ubuntu and following the procedure (If you are installing Natty there may be a warning saying that sdb is mounted or something and it offers to unmount it, sdb is the live usb you install from, just click no and proceed) 

6)This is the most important part. At one point you will be presented with a list of options : to erase the hard disk, install side by side with Windows etc. Choose "Some thing Else". 

7) You will then see the partition layout of you drives. Scroll down to sdc (or sdb if you install from a CD) and the choose manually creating partition or something like that. Make sure you choose the correct drive (never sda!) or Ubuntu will wipe out WIndows.

8) You should make 3 partitions. One is your boot partition, the mount point should be  / ; the second one is a home partition to store your data and settings, mount point /home; the third is a swap partition.  The / and /home partition should both be in ext4. The swap partition is just called "swap" and you don't need to format it. The / partition should be about 15G (should be enough) and the /home partition should be as big as you need/

9) In the bottom of the screen there is a box asking you where to install bootloader, choose the same drive you install Ubuntu into (sdc in our example, notice it is not the partition, but the drive, so choose sdc rather than sdc1, say)

10) Then just continue.

It sounds more complicated then it actually is, the process only takes a bout 20 mins. 

Finally, to answer your question, if you follow the steps correctly (espcially 7-9) the drive with Windows will not be touched.

---

### Post by noobda on 2011-06-07
Thanks For Excellent Share ..

---

### Post by dFlyer on 2011-06-07
I would agree to go with a direct install and not wubi. You can setup a stand alone os system or dual boot system fairly easy. I would recommend that you backup your data before doing anything.

---

### Post by wolfen69 on 2011-06-08
Also, if you are worried about wiping your windows drive by accident, just unplug the windows drive temporarily and install ubuntu. Then plug windows back in. When in ubuntu, you can then do:
```
sudo update-grub
```
and then windows will be added to the boot loader screen when the computer starts, and you can then boot into the OS of your choice.

---

### Post by Mark Phelps on 2011-06-08
> **wolfen69 said:**
> Also, if you are worried about wiping your windows drive by accident, just unplug the windows drive temporarily and install ubuntu. Then plug windows back in...

Can't emphasize the importance of this advice enough!

This is the ONLY way to ensure that installing Ubuntu does not touch your Windows setup in any way.  This will save you a whole lot of grief from MBR overwrites and possible Win6 filesystem corruption.

Plus -- when done, you have TWO bootable drives, that's right, each drive can be booted on its own.  That comes in handy when you want to upgrade or repair your Win7 setup and don't want to touch the Ubuntu setup.

---

### Post by Paqman on 2011-06-08
The speed difference between Wubi and a normal install is so small you're highly unlikely to notice it.

---

