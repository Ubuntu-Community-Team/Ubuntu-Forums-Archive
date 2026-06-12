---
title: "Dual Boot Help - Error 21"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by pappasaa on 2008-12-20
Hello all,

I need some help if anyone can. I am going to try to give you as much info as I know to give and a quick install history.

OK her it is:

1) I have two drives so i installed ubuntu on one drive

2) removed it and put in another drive a setup windows ( its required for my school or i would not even use it )

3) then i put both of them in and tried to setup a dual boot but I read a good idea and wanted to change everything.

The idea was to put both OS on one drive and store all my files on the extra drive in case something goes wrong with one of the OS so....

4) I took the drive with windows on it and installed ubuntu  and everything is working great. I got my dual boot setup and now I want to clean off the other hard drive and use it for storeage.


So that is where I am at right now. I did a test to see what would happen if i took the extra drive out and i got an error 21 from grub ans I an not sure how to edit the other drive out of the startup

i want to be able to boot the ubuntu/win drive without the other drive installed on my computer


5) I used KGRUBEditor to take out the option to boot Ubunto from the extra drive but I think there is somthing I missed.

here is /boot/grub/menu.lst

```
default 0
timeout 99
color white/brown white/black

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2d56e390-01b2-4d91-afb0-92450db14019 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2d56e390-01b2-4d91-afb0-92450db14019

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=2d56e390-01b2-4d91-afb0-92450db14019 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=2d56e390-01b2-4d91-afb0-92450db14019 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive


```

here is /boot/grub/device.map

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```


i want to be able to boot the ubuntu/win drive without the other drive installed on my computer

---

### Post by pappasaa on 2008-12-20
i buped this so I wont get lost...

---

### Post by bumanie on 2008-12-20
Grub is looking for a ext3 filesystem on the drive you originally had as ubuntu. On the drive with windows and ubuntu, can you boot both OSes or only windows? - I suspect only windows will boot, can you confirm whether ubuntu boots as well.

---

### Post by logos34 on 2008-12-20
sounds like you were actually booting to grub on the other drive.

With the other drive removed, reinstall grub to the MBR of the ubuntu/windows dual boot drive. (see link in my signature)

---

### Post by pappasaa on 2008-12-20
i can boot both. I only get the error when I unpug or change the jumper setting on the second drive. Thanks for getting back to me

---

### Post by bumanie on 2008-12-20
Post the output of > sudo fdisk -lu

---

### Post by pappasaa on 2008-12-20
> **bumanie said:**
> Post the output of


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d2d2d2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf188f188

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   114125759    57062848+  83  Linux
/dev/sdb2       114125760   234484739    60179490    5  Extended
/dev/sdb5       231480648   234484739     1502046   82  Linux swap / Solaris
/dev/sdb6       114125886   228460364    57167239+  83  Linux
/dev/sdb7       228460428   231480584     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by logos34 on 2008-12-20
> **pappasaa said:**
> i can boot both. I only get the error when I unpug or change the jumper setting on the second drive. Thanks for getting back to me

right, that's consistent with what I said.  Grub is either not on the MBR of the ubuntu/windows drive or is not pointing to the / at the correct location (i.e. hd**0**,?)

so try reinstalling grub

---

### Post by logos34 on 2008-12-20
if sdb1 is ubuntu /, then 

sudo grub

grub> find /boot/grub/stage1

(if it returns 'root (hd1,0)', then do:

grub> root (hd1,0)
grub> setup (hd1) --> you want it on the same drive MBR 

or if it returns '(hd0,0)', do:

grub> setup (hd0)

---

### Post by bumanie on 2008-12-20
fdisk -lu shows that you have got windows on one drive and two installations of ubuntu on the other drive - the output indicates something quite different to what you have explained (or atlleast how I understood what you were saying). sda indicates the first drive and sdb is the second drive.

---

### Post by pappasaa on 2008-12-20
> **logos34 said:**
> if sdb1 is ubuntu /, then 

sudo grub

grub> find /boot/grub/stage1

(if it returns 'root (hd1,0)', then do:

grub> root (hd1,0)
grub> setup (hd1) --> you want it on the same drive MBR 

or if it returns '(hd0,0)', do:

grub> setup (hd0)


I got this back
```
 (hd1,0)
 (hd1,5)
```

after doing 
```
grub> find /boot/grub/stage1
```

so i stopped there....I am a newb

---

### Post by bumanie on 2008-12-20
If this is a new istallation and you want the setup how you described, setting up grub to boot from the second hard drive won't achieve what you want, also it would be best not to have two ubuntu installations of the same version on the one hard drive - it's really just wasting space. It would be easy to setup your computer as is as a dual boot, but I would delete one of your ubuntu installations first. If you want windows and ubuntu on the one drive you will have to reinstall ubuntu to the first hard drive and format the second hard drive to get rid of ubuntu from it.

---

### Post by pappasaa on 2008-12-20
> **bumanie said:**
> If this is a new istallation and you want the setup how you described, setting up grub to boot from the second hard drive won't achieve what you want, also it would be best not to have two ubuntu installations of the same version on the one hard drive - it's really just wasting space. It would be easy to setup your computer as is as a dual boot, but I would delete one of your ubuntu installations first. If you want windows and ubuntu on the one drive you will have to reinstall ubuntu to the first hard drive and format the second hard drive to get rid of ubuntu from it.


I this what i am trying to do....I want to uninstall ubuntu from the second drive....


I had ubuntu on one drive and windows on another....I then took the disk with windows on it and installed ubuntu on it whitch then gave me the double boot I wanted. At the same time it added the second drive with ubuntu on it to the boot list before I even tried to uninstall ubuntu from the other disk.

I now have 2 copies of ubuntu on two different disks. I am going to uninstall ubuntu from the second disk to use it for storeage...but...my problem is that grub still sees it in the startup so I have not made any changes to the disk yet for fear that i will need to just start with two blank disks and reinstall everything all over.

---

### Post by bumanie on 2008-12-20
You actually have windows on its own, on one hard drive and two ubuntu installations on the other hard drive - I know what you want to have, but if you look at fdisk -lu you will see that windows is on sda and 2 ubuntu's are on sdb - you have not got one ubuntu on sda with windows. sda is one separate hard drive, sdb is another separate hard drive.

---

### Post by pappasaa on 2008-12-20
> **bumanie said:**
> You actually have windows on its own, on one hard drive and two ubuntu installations on the other hard drive - I know what you want to have, but if you look at fdisk -lu you will see that windows is on sda and 2 ubuntu's are on sdb - you have not got one ubuntu on sda with windows. sda is one separate hard drive, sdb is another separate hard drive.

ok...this makes the partisions i made make sence to me now. I did not understand why i set 50% of the partision to ubuntu and the other 50% was to ubuntu...never installed a dual OS system before. I think i am just going to start fresh so I am going it right the first time...


Thanks for helping me out.

---

### Post by bumanie on 2008-12-20
If you need help with the istallation, post again and someone will help you out. To get rid of grub and ubuntu off sdb, it would be best to format that drive, just make sure you don't format your windows installation.

---

### Post by logos34 on 2008-12-20
The way I see it, it makes as much sense to shrink windows and clone ubuntu / to the 80 gb drive as it does to reinstall, which involves redownloading all the programs and updates (unless you backup your /var/cache/apt/archives first).  

anyway, good luck

---

