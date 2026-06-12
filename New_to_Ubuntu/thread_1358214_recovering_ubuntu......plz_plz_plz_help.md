---
title: "recovering ubuntu......plz plz plz help"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by ckdutta1 on 2009-12-18
hey all...

i am a very very newbie here so plz forgive me in advance for my any mistakes....

now to the problem...
i got installed ubuntu at my 40 gb hard disk and i devoted all my disk space to ubuntu...i got my windows on some other hard disk.

bootlodar of ubuntu is grub and it is on 40 gb hard disk.so when i have to log in in ubuntu i must boot from 40 gb hard disk and when i have to log in in windows i have to boot from other hard disk(booth boot loader is separeted).

now when i am trying to boot from ubuntu it shows nothing.....i downloaded new ubuntu so that i can recover iff possible but after trying for whole day i gave up...and now i need help.....

here it shows that 40 gb hard disk is not in good shape and some bad sectore in it....but ubunto it self(from live cd i just downloaded) fail to recgnoize the 40 gb hard disk.it says free space of 40 gb.


now i m stuck here and really noidea wat to do.....as i have really imp.stuffs in there ...

kindly help me out please

i will appriciate if any online user can have a chat with me and guide me through this


witing for ur suggestion......

---

### Post by cholericfun on 2009-12-18
just to clarify: it has worked before for a while then?

when you mean you have separate bootloaders you mean what?
when you install ubuntu you'll normally get a sceen from grub on boot-up to let you pick your install but sounds to me that you manually plugin your different drives?

ps: when you boot from liveCD go straight to GPARTET *before* you do anything else with it like mount it and tell it to "check" that drive (right click on the drive an so on)
(System--->Admin--->partition editor)

---

### Post by ckdutta1 on 2009-12-18
thanks for ur reply.... i m on it....
separete boot loader means there is different boot loader for windows.....and ubuntu....

means grub never shows to choose from 2 different o.s.....

---

### Post by cholericfun on 2009-12-18
> thanks for ur reply.... i m on it....
separete boot loader means there is different boot loader for windows.....and ubuntu....

means grub never shows to choose from 2 different o.s.

ok so how do you switch between them, via BIOS?

any luck on the gparted side?

---

### Post by ckdutta1 on 2009-12-18
thanks a lot .......

but no luck with gparted......it dosnt shows my 40 gb hard disk with ubuntu in it....

an i was choosing my o.s. from "F10".......it gives me option from which media i want to boot........

---

### Post by ckdutta1 on 2009-12-18
hey cholericfun.......thanks a lot....

but as regarding my problem i think file system is corrupted....it happend earlier with windows but i  managed it to repair with its cd.....
but i dont know how to repair this in ubuntu........

i know it was my fault becouse one of my friend told me there is "Earthing" problem that corrupted my windows........so i think that is the problem with ubuntu too.......

waitinn for suggestions...

---

### Post by cholericfun on 2009-12-18
F10 - nice one.


Ok, well: 
i once had a problem with fixing my partition. turns out that if i *didn't* touch that drive at all (e.g. list it ,find it,mount it...) then Gparted would show me something and it was able to repair it. maybe that applies here as well. (BTW you need to select the right drive on the right of the Icon Bar)

show us this:

```
sudo fdisk -l
```

---

### Post by guvnr on 2009-12-18
@ckdutta1, that sounds a pain, hope not too much lost.

1 ting to try .. boot off live CD (Try Ubuntu option) and from there, mount the disk with Ubuntu and try to recover anything important (like maybe your entire /home and perhaps a few key config files in /etc)

.. then buy a nice shiny 1TB drive for about 50p!

you could also try recovering files from your Windows partition.  can be done, so i've read .. can't remember the software you need but there is some Wins app that recognises ext3/ext4 filesystems, then you can try to save data.

---

### Post by ckdutta1 on 2009-12-18
> **cholericfun said:**
> F10 - nice one.


Ok, well: 
i once had a problem with fixing my partition. turns out that if i *didn't* touch that drive at all (e.g. list it ,find it,mount it...) then Gparted would show me something and it was able to repair it. maybe that applies here as well. (BTW you need to select the right drive on the right of the Icon Bar)

show us this:

```
sudo fdisk -l
```


here is this........i dont understand it a lot but think you people wil......





ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4dce4dcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19456   135797445    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   b  W95 FAT32
/dev/sda6            5101       10199    40957686    7  HPFS/NTFS
/dev/sda7           10200       15298    40957686    7  HPFS/NTFS
/dev/sda8           15299       19456    33399103+   b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by cholericfun on 2009-12-18
hm, not great.
it only sees the 160GB Windows HD. not the other one.

i'll try a reboot into the LiveCD and try Parted again.

other than that i'm afraid i'm not sure. Could be something stupid as well though - maybe try the drive out in a different computer.

---

### Post by ckdutta1 on 2009-12-18
thanks you people for your support.....

but i am not giving up this ****.......will do google for more.....

thanks again...

but for once any one plz tell me "how to repair file system?"

and if i can go to command prompt with root privilage...with the help of live cd???


thanks a lot....

---

### Post by cholericfun on 2009-12-18
gparted "check" checks and repairs a filesystem. there sure are commandline tools that prob do the same. Problem is your System doesnt seem to be able to access the HD at all.

---

