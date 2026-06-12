---
title: "usb flash drive not recognised"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by centaur1 on 2011-05-09
hi all - fresh install u10.04 and no usb function. plugged in a thumb drive and ran 'system/administration/hardware drivers' and the drive was detected and readable. removed drive and re-inserted it and no detection/mounting. how do i get the usb port to stay active so that i see it when a drive is plugged in?
thanx

---

### Post by garvinrick4 on 2011-05-09
Open configuration editor and go to apps to nautilus to preferences and make sure
automount is checked:

---

### Post by centaur1 on 2011-05-10
Thanks [garvinrick4]("http://ubuntuforums.org/member.php?u=899097") for the response. I looked after I figured out how to launch the editor and the media automount box is checked. Any other thoughts?

---

### Post by garvinrick4 on 2011-05-11
#Run this with drive plugged in.
```
sudo blkid
``` (second letter lower case L)

Find uuid or label of usb flash drive and write it down.

#run:
```
sudo fdisk -l
``` (lower case L)
find [COLOR=Red]sdx[/COLOR] (x being whichever letter) of  usb drive like sdb or sdc or sdd and so on.

#Then make a directory in media and mount it:
```
sudo mkdir /media/ UUID or Label
``````
sudo mount /dev/[COLOR=Red]sdx[/COLOR] /media/UUID or Label
```[COLOR=Red]sdx[/COLOR] being whatever your flash drive is in fdisk -l.

---

### Post by centaur1 on 2011-05-13
Hi garvinrick4 - I tried your suggestion and with the flash drive in place I received the following after the first terminal entry of sudo blkid

centaur@CNC:~$ sudo blkid
[sudo] password for centaur: 
/dev/sda1: UUID="c6c8519a-a253-4dab-86aa-1697feb3ccf3" TYPE="ext4" 
/dev/sda5: UUID="7db637c8-1e9b-4a8e-af40-67677f99cd41" TYPE="swap" 
centaur@CNC:~$ 

I am (obviously) a novice with Linux but it looks to me that all I see above is the main hard drive partition and the swap file partition. As an aside, I also could not 'see' my floppy after the install and I removed it from the system in the hopes of using the flash. If you still have the patience I wonder what else can be done.Thanks

---

### Post by RJ12 on 2011-05-13
Can you try running this command in the Terminal and then see if your USB drive will work?

```
sudo modprobe usb-storage
```

---

### Post by centaur1 on 2011-05-16
Hi Rj12 - tried this and it works as long as I leave the flash drive connected. When I remove and then re-connect the flash Ubuntu does no see it. Is there any way to arrange things so that Ubuntu sees the flash whenever it is connected?
Thanx
centaur1

---

### Post by jtarin on 2011-05-16
[Try this]("http://http://tips4linux.com/usb-devices-not-mounting-in-lucid-heres-a-fix/")

---

### Post by centaur1 on 2011-05-16
Hi again Rj12 - continuing from my prevoius - I just discovered that after re-connecting the flash and running again the sudo modprobe usb-storage command it did not work! Also when running it the first time the following message showed:
centaur@CNC:~$ sudo modprobe usb-storage
WARNING: All config files need .conf: /etc/modprobe.d/emc2, it will be ignored in a future release.
Might this be s clue as to what is going on?
Thanx

---

### Post by centaur1 on 2011-05-16
Hi Rj12 - one more thing I just discovered - when the flash is plugged in during boot Ubuntu sees it but when I remove and re-insert - again it disappears!

---

### Post by centaur1 on 2011-05-20
SOLVED
Hi Folks - well it looks like we are at a dead end with the USB thing so I tried and old Windoze trick -
re-install the OS. I did this and now the USB works as it should. Thanks for the suggestions which were posted.

---

### Post by RJ12 on 2011-05-21
> **centaur1 said:**
> SOLVED
Hi Folks - well it looks like we are at a dead end with the USB thing so I tried and old Windoze trick -
re-install the OS. I did this and now the USB works as it should. Thanks for the suggestions which were posted.

Glad that you were able to get it working :)

---

