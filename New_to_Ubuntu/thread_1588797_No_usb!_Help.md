---
title: "No usb! Help"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by 1Robomaker on 2010-10-05
Just installed ubuntu 10.4 server 64 on my system. Everything seems to have gone fine. I installed the desktop from the command line. Everything has gone perfect thus far I am very excited! However none of my usb ports are working at all. worked fine when I had windows 7 on this box. please help with some direction. I desperatly want to start using this powerful os!
 
Thanks

---

### Post by Clever_Username on 2010-10-05
I was looking around and I found alot of posts indicating an issue with a software package called "Virtualbox". I'm not familiar with this software, but does it ring any bells for you?

[Here]("http://ubuntuforums.org/showthread.php?t=594247") is a link to one of the threads I found.

---

### Post by llawwehttam on 2010-10-05
Why did you use the server edition. Unless you need it to run a server the desktop edition will be fine. The server edition offers a little more benefits than the desktop edition but not for GUI apps.

Virtualbox is not near relevant. Its just an OS virtualiser which is NOT installed as default.

---

### Post by cariboo on 2010-10-05
Are you sure that the problem isn't that your usb devices are not being auto-mounted?

To see if your usb devices is detected, open a terminal and type:

```
dmesg | tail -n10
```

just after you plug the device in. The output should look something like this, if your usb ports are working:

```
dmesg | tail -n10
[ 8317.082611] scsi 4:0:0:0: Direct-Access     Lexar    JD Secure II +   1100 PQ: 0 ANSI: 0 CCS
[ 8317.083280] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 8318.396863] sd 4:0:0:0: [sdc] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[ 8318.397978] sd 4:0:0:0: [sdc] Write Protect is off
[ 8318.397982] sd 4:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 8318.397985] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8318.403354] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8318.403364]  sdc: **sdc1**
[ 8318.407981] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8318.407986] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

As you can see from the output above, my thumb drive is detected and the device label is /dev/sdc1

---

### Post by 1Robomaker on 2010-10-05
Thank you for your quick reply:
Using the code line you suggested this is what was returned

toby@ubuntu:~$ dmesg | tail -n10
[   93.305532] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[   93.305536] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  242.855528] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[  242.855531] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  314.745549] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[  314.745549] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  484.435527] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[  484.435531] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  486.755527] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  486.755530] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
toby@ubuntu:~$ 


Any thoughts???

I only have one 8 gig usb key plugged in and one usb mic
Usb ports worked when under windows, usb devices work on other pc's.
So, it would seem that the hard ware is ok.

I appreciate your input please give me more....

---

### Post by sandyd on 2010-10-05
> **1Robomaker said:**
> Thank you for your quick reply:
Using the code line you suggested this is what was returned

toby@ubuntu:~$ dmesg | tail -n10
[   93.305532] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[   93.305536] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  242.855528] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[  242.855531] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  314.745549] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[  314.745549] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  484.435527] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[  484.435531] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.
[  486.755527] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  486.755530] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
toby@ubuntu:~$ 


Any thoughts???

I only have one 8 gig usb key plugged in and one usb mic
Usb ports worked when under windows, usb devices work on other pc's.
So, it would seem that the hard ware is ok.

I appreciate your input please give me more....
post output of
```

sudo fdisk -l
```

---

### Post by 1Robomaker on 2010-10-05
toby@ubuntu:~$ sudo fdisk -l
[sudo] password for toby: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea6b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       14594   116969473    5  Extended
/dev/sda5              32       14594   116969472   8e  Linux LVM
toby@ubuntu:~$ ^C
toby@ubuntu:~$

---

### Post by 1Robomaker on 2010-10-06
Please don't give up on me folks! Could realy use some insights here.
I needs my usbbbbbbbbb!!

---

