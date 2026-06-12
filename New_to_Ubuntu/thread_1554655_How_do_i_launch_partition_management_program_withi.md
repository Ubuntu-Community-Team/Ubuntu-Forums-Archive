---
title: "How do i launch partition management program within ubuntu ?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by AfrikaDietmar on 2010-08-17
Hi,

i guess this is a novice question so i decided to post it here instead under installations.
I'm not talking about the disc management tool that comes pre installed with ubuntu but that program that launches when you install ubuntu with which you set the partitions.
Is it possible to reaccess it when ubuntu is already installed to make changes to the partitions ? I've read somewhere that it could be "Gpart" ? but when i install it from the software centre, i then simply have no idea where it is located (i did search a lot).
This peace of information will be really helpful for future systems management as i tend to work with a lot of lets say quite old used machines where i might need to make changes within ubuntu and not from booting from the cd to relaunch the partition program.

---

### Post by miserly-martyred on 2010-08-17
I'm trying to memorize the menu's as best i can, given that my Ubuntu is temp. fried - just go to the top left of the screen, follow from apps, to the right thru places and on to system, then from system go to administration, gParted should be in there, i believe.

---

### Post by cantormath on 2010-08-17
You can boot to the live cd and run Gparted, that is the partition  management program i use if I need a GUI.  You can install it on your  system using synaptic or apt, but you cannot make changes to a disk that  is currently mounted.  If you are using a single drive with your Linux  installation, you will need to use the live cd to make any changes to  the drive's partitions.  You will need to boot to the live cd and select  the "try ubuntu without any changes" option.  That will boot you into a  desktop environment from which you can run gparted (from terminal).  If  you want to make changes to a drive that is not the primary drive, you  can do so without the live cd.

---

### Post by cantormath on 2010-08-17
double post

---

### Post by Elfy on 2010-08-17
> If you want to make changes to a drive that is not the primary drive, you can do so without the live cd.You can do whatever you want to any of your drives so long as they are not mounted.

---

### Post by AfrikaDietmar on 2010-08-17
Yes, that makes sense, and thats the workaround i would use, my dilemma is, my sony vaio laptop has a dying cd/dvd rom drive that unfortunately doesn't read anymore burnt .iso cds, so i cannot boot from CD. The only way i kind of managed to boot into linux was to have a boot record and grub written for ubuntu from winXP - and then with a bootable usb stick i managed to do as above. But it also doesn't boot so well from the usb drive, only after i select ubuntu from grub (before i had ubuntu installed) i could run a test version. I haven't tried if it would now. So i guess i will not be able to use GPART within ubuntu then as my primary drive is mounted...

By the way in winXP i can launch Paragon Drives manager, and make changes to the mounted drive, it doesn't apply changes yet, but once i reboot i applies them to the primary drive - is there no way we can do this in ubuntu as well ? well maybe there are some reasons thats not possible in ubuntu which makes sense, but i'm just no yet aware about.

---

### Post by Elfy on 2010-08-17
You can add iso's to the grub menu - so you could maybe get the iso to boot from there 

I have this in my 40_custom file to boot partedmagic

```
menuentry "Test Parted Magic ISO @ /iso/pmagic-4.10.iso" {
set root=(hd0,2)
loopback loop (hd0,2)/iso/pmagic-4.10.iso
linux (loop)/pmagic/bzImage iso_filename=/iso/pmagic-4.10.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
initrd (loop)/pmagic/initramfs
}

```

---

### Post by AfrikaDietmar on 2010-08-17
Thats a good tipp, only that my CD/DVD drive is not reading any copied cds anymore, its dying, it will only read original cds, and even if i insert an .iso cd of ubuntu, it will not know that its there.

Is this workaround possible in ubuntu?...
> By the way in winXP i can launch Paragon Drives manager, and make  changes to the mounted drive, it doesn't apply changes yet, but once i  reboot i applies them to the primary drive - is there no way we can do  this in ubuntu as well ? well maybe there are some reasons thats not  possible in ubuntu which makes sense, but i'm just no yet aware about. 	

---

### Post by Elfy on 2010-08-17
If it works with the buntu iso then you don't need the cd. I have edited the post.

No idea about paragon drive manager I'm afraid - but to do any work to partitions which include in some way the linux install it needs to be unmounted.

---

