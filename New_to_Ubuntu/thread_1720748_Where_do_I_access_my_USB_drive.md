---
title: "Where do I access my USB drive?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by ChTTay on 2011-04-03
Hi All,

I am brand new to Linux/Ubuntu (10.10) and just jumped in at the deep end with my ASUS EeePC R101 netbook. I've plugged in my USB drive/stick and checked 'automount' is ON but where do I access the drive? I am looking in 'File Manager' and I cannot see anything; The USB drive does not appear to show up as an icon. 

I have tried searching Google and this forum. This seems so simple but I just can't see it! I did get this log information and I presumed it is okay to post;

Apr  3 20:02:26 c-1001PX kernel: [13901.042639] Initializing USB Mass Storage driver...
Apr  3 20:02:26 c-1001PX kernel: [13901.042975] scsi4 : usb-storage 1-1:1.0
Apr  3 20:02:26 c-1001PX kernel: [13901.043765] usbcore: registered new interface driver usb-storage
Apr  3 20:02:26 c-1001PX kernel: [13901.043773] USB Mass Storage support registered.
Apr  3 20:02:27 c-1001PX kernel: [13902.071418] scsi 4:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Apr  3 20:02:27 c-1001PX kernel: [13902.074760] sd 4:0:0:0: Attached scsi generic sg1 type 0
Apr  3 20:02:29 c-1001PX kernel: [13903.951070] sd 4:0:0:0: [sdb] 31277056 512-byte logical blocks: (16.0 GB/14.9 GiB)
Apr  3 20:02:29 c-1001PX kernel: [13903.952921] sd 4:0:0:0: [sdb] Write Protect is off
Apr  3 20:02:29 c-1001PX kernel: [13903.961196]  sdb: sdb1
Apr  3 20:02:29 c-1001PX kernel: [13903.987250] sd 4:0:0:0: [sdb] Attached SCSI removable disk

Thanks for your help
C.T

---

### Post by Dutch70 on 2011-04-03
What do you mean "access it"? When you plug it in, an icon should show up on the desktop if you're running Ubuntu.

Do you by any chance have usb 3.0 ports? You may want to try plugging it in to different ports.

---

### Post by frenchn00b on 2011-04-03
> **ChTTay said:**
> Hi All,

I am brand new to Linux/Ubuntu (10.10) and just jumped in at the deep end with my ASUS EeePC R101 netbook. I've plugged in my USB drive/stick and checked 'automount' is ON but where do I access the drive? I am looking in 'File Manager' and I cannot see anything; The USB drive does not appear to show up as an icon. 

I have tried searching Google and this forum. This seems so simple but I just can't see it! I did get this log information and I presumed it is okay to post;

Apr  3 20:02:26 c-1001PX kernel: [13901.042639] Initializing USB Mass Storage driver...
Apr  3 20:02:26 c-1001PX kernel: [13901.042975] scsi4 : usb-storage 1-1:1.0
Apr  3 20:02:26 c-1001PX kernel: [13901.043765] usbcore: registered new interface driver usb-storage
Apr  3 20:02:26 c-1001PX kernel: [13901.043773] USB Mass Storage support registered.
Apr  3 20:02:27 c-1001PX kernel: [13902.071418] scsi 4:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Apr  3 20:02:27 c-1001PX kernel: [13902.074760] sd 4:0:0:0: Attached scsi generic sg1 type 0
Apr  3 20:02:29 c-1001PX kernel: [13903.951070] sd 4:0:0:0: [sdb] 31277056 512-byte logical blocks: (16.0 GB/14.9 GiB)
Apr  3 20:02:29 c-1001PX kernel: [13903.952921] sd 4:0:0:0: [sdb] Write Protect is off
Apr  3 20:02:29 c-1001PX kernel: [13903.961196]  sdb: sdb1
Apr  3 20:02:29 c-1001PX kernel: [13903.987250] sd 4:0:0:0: [sdb] Attached SCSI removable disk

Thanks for your help
C.T

You can try my OS window manager, it is made to be easy for all: 

[http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v50.1%5D?content=127893](http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v50.1%5D?content=127893)

in gdm or kde, use the fvwm, and untar my files into $HOME/.fvwm
so that $HOME/.fvwm/.fvwm2rc...

so to reply:

the pendrive is seen when you un/plug the pendrive, and type : dmesg

then you see to where it will be affected, then you can update your /etc/fstab 

here mine, part for the /media/pendrive:

```



#UUID="DEB0-0001"       /media/pendrive         vfat    users,rw,noauto,umask=0000,uid=1000,gid=1000 0 0
/dev/sdf1       /media/pendrive         vfat    users,rw,noauto 0 0
#/dev/sdf1: SEC_TYPE="msdos" LABEL="Debian Inst" UUID="DEB0-0001" TYPE="vfat" 




```

---

### Post by 3177 on 2011-04-03
> **ChTTay said:**
> 
Apr  3 20:02:26 c-1001PX kernel: [13901.042639] Initializing USB Mass Storage driver...
Apr  3 20:02:26 c-1001PX kernel: [13901.042975] scsi4 : usb-storage 1-1:1.0
Apr  3 20:02:26 c-1001PX kernel: [13901.043765] usbcore: registered new interface driver usb-storage
Apr  3 20:02:26 c-1001PX kernel: [13901.043773] USB Mass Storage support registered.
Apr  3 20:02:27 c-1001PX kernel: [13902.071418] scsi 4:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Apr  3 20:02:27 c-1001PX kernel: [13902.074760] sd 4:0:0:0: Attached scsi generic sg1 type 0
Apr  3 20:02:29 c-1001PX kernel: [13903.951070] sd 4:0:0:0: [sdb] 31277056 512-byte logical blocks: (16.0 GB/14.9 GiB)
Apr  3 20:02:29 c-1001PX kernel: [13903.952921] sd 4:0:0:0: [sdb] Write Protect is off
Apr  3 20:02:29 c-1001PX kernel: [13903.961196]  sdb: sdb1
Apr  3 20:02:29 c-1001PX kernel: [13903.987250] sd 4:0:0:0: [sdb] Attached SCSI removable disk



its there.

---

### Post by garvinrick4 on 2011-04-03
Any Nautilus window in left side panel.
```
nautilus /home
```

---

### Post by 3177 on 2011-04-03
to see if its REALLY there try this.
go to the terminal.
type ```
cd /media
```
then ```
ls
```
you should see your flash drive listed when entering the second code.

---

### Post by dwhite on 2011-04-03
hi,

if it is not showing up on desktop...go to the main menu-->places and see if  the usb is listed there (just under "computer")

i've attached a screenshot showing what it looks like on my computer (my usb is "lake placid")

---

### Post by ChTTay on 2011-04-05
3177 - I tried the command suggested in the terminal. Nothing seemed to happen;

c@c-1001PX:~$ cd /media
c@c-1001PX:/media$ ls
c@c-1001PX:/media$ 

dwhite - It doesn't look like I have a 'main menu' on this nor 'places'. I've attached a screen shot below of my desktop and of file manager.

[IMG]https://lh4.googleusercontent.com/_9Oe4bdCPafQ/TZsAh-3tXPI/AAAAAAAAASI/2OyDHPxo-bw/s144/Screenshot-1.png[/IMG]

[IMG]https://lh3.googleusercontent.com/_9Oe4bdCPafQ/TZr_QhG6b5I/AAAAAAAAAR4/mLM3uEnN8Fo/s144/Screenshot.png[/IMG]

This is so frustrating - I really appreciate your help!

---

### Post by 3177 on 2011-04-05
weird. this means its really not picking it up. I'll look around and see if anyone else has had this problem.

---

