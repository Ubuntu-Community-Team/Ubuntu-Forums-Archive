---
title: "Alert! /dev/disk/by-uid xxx not found"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by meat on 2010-12-30
I just installed 10.10 Ubuntu on an Acer 14.10 using a thumb drive and I was greeted with the wonderful text message about not finding my boot drive.  I have looked up other threads and searched for help, but I still don't know how to fix it.  I have typed sudo fdisk -l and here is what it says

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29677   238379008   83  Linux
/dev/sdb2           29678       30402     5817345    5  Extended
/dev/sdb5           29678       30402     5817344   82  Linux swap / Solaris

so I probably have to tell grub to use /dev/sdx instead of using the iid, but how do I do it?  I can't modify the grub.cfg file using sudo gedit /boot/grub/grub.cfg

Thanks

---

### Post by wojox on 2010-12-30
You would modify fstab and tell it where root is.

---

### Post by meat on 2010-12-30
I don't know where root is and I don't understand how to modify the fstab file.  I also don't understand how this happens.  You install the OS and somehow it forgets where the boot file is and you don't even load into the GUI.

I am on the live CD right now.

---

### Post by wojox on 2010-12-30
Can you mount the drive your wanting to use?

/dev/sdb1 tells me your still on your thumb drive.

---

### Post by meat on 2010-12-30
I don't know how to mount the drive and I don't know which drive to mount.

---

### Post by wojox on 2010-12-30
When you click on Places in the top panel can you see your hard drive?

Click on it and open a terminal and run:

```
fdisk -l
```

---

### Post by meat on 2010-12-30
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29677   238379008   83  Linux
/dev/sdb2           29678       30402     5817345    5  Extended
/dev/sdb5           29678       30402     5817344   82  Linux swap / Solaris

I see my hard drive and this is what i get when i do terminal.  I am doing this correctly?

---

### Post by wojox on 2010-12-30
I guess that's it then. Open up fstab 

```
cat /etc/fstab
```

And post that up here.

---

### Post by meat on 2010-12-30
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0

```

---

### Post by meat on 2010-12-30
Thank you Wojox for helping me.  I did another search and found some other threads and I believe I fixed it.  Hopefully others that have this problem will have some luck here.

What I did was go into my bios (f2) and change AHCI to IDE and it worked.

Thanks again

---

