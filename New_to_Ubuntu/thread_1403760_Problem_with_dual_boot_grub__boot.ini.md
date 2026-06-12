---
title: "Problem with dual boot grub / boot.ini"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Shocker on 2010-02-10
Hi everybody!

Recently I decided to do a fresh installation of Ubuntu KK
From that day I cannot boot to XP64 (an entry made available from windows bootmanager --> boot.ini file) normally.
Anyway I can boot both Ubuntu (default boot /dev/sdb) and Win7 (dev/sda1) via Grub(2).

What's strange is that XP64 can boot up, but only if I start loading the mbr of /dev/sda through a boot-time bios selection, otherwise I get a NTdetect not found error.

I attach the results of the boot_info_script.sh script.

I hope anyone can give advice.

Bye for now

Shocker

---

### Post by meierfra. on 2010-02-11
Try this

```
gksudo gedit /boot/grub/device.map
```
and change it do:

(hd0) /dev/sd[COLOR="Red"]b[/COLOR]
(hd1) /dev/sd[COLOR="Red"]a[/COLOR]

Save the file. Then

```
sudo update-grub
```

Reboot and see whether you can get into Window 7 and XP.

---

### Post by Shocker on 2010-02-11
meierfra, 

thanks a lot for your reply,

I will try that this evening.

Apart from that, what I don't understand is how can grub affect the map of the booting devices once I have decided to start with the HD with the Win Os (that is: selecting the Win7 entry in the Grub menu)

Another question, changing the devices.map as advised don't I risk to be unable to boot both Ubuntu and Win7? (now I can boot these Os without problems).

In that case, will I be able to fix the file back booting the livecd (dvd)?
  
Thanks in advance for your suggestions

Shocker

---

### Post by meierfra. on 2010-02-11
> I risk to be unable to boot both Ubuntu and Win7?
You still will be able to boot in Ubuntu.  Under  normal circumstance you should also still be able to boot into Win7.

Since /dev/sdb  is your boot  drive, Grub at boot up considers it to be (hd0). So the correct device map is

(hd0) /dev/sdb
(hd1) /dev/sda

You are currently using the wrong device map as one can see from your entries in grub.cfg:
	
> menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set e238ed7938ed4d5b
	chainloader +1
The correct entry  for the  Windows 7 root is "(hd1,1)". Luckily the "search" command overwrites the faulty root statement


I believe that XP does not boot, because  your Windows item is missing  the 

drivemap  -s (hd0) ${root}

line.  (XP assumes that the boot files are on the boot drive. The drivemap line will  virtually turn the Windows  drive into to boot drive)


I was hoping that after  changing the device.map, update-grub  will  insert the drivemap line.
But I now realize that that won't work. update-grub does not insert the drivemap lines since Windows 7 does not need them (and update-grub does not   know that the same boot loader is used for XP) Editing the device.map will not change that.

So we have to switch  Plan B:

Copy the XP boot files from Window 7 partition to the XP partition (this will  have  the additional advantages that you can boot all three OS directly from the Grub Menu):

Just copy the three files "/boot.ini", "/ntldr" and "/NTDETECT.COM" from your Windows 7 partition to the XP partition.   And then follow  direction from my previous post. You should now have an new entry for "XP" an your Grub menu which should let you boot into XP.

---

### Post by Shocker on 2010-02-13
Hi meierfra,

sorry for the delay, but It took me some time to find some spare time to test your solution. 
Your suggestions were right: thanks to you now I can boot to any of the 3 Os from the grub menu.

What I still don't know / understand is why XP64 doesn't boot from the old WinXP bootmanager apart from setting the sda HD as boot device from after the bios POST. (It says "unvalid boot.ini, ... Booting from C:\windows\ .. NTEDECT failed" )

Maybe I will try to rebuild the boot .ni from the XP recovery console.

If anyone else can give a hint, please do.

Bye 

Shocker

---

### Post by meierfra. on 2010-02-13
> What I still don't know / understand is why XP64 doesn't boot from the old WinXP bootmanager apart from setting the sda HD as boot device from after the bios POST. (It says "unvalid boot.ini, ... Booting from C:\windows\ .. NTEDECT failed" )

Maybe I will try to rebuild the boot.ini from the XP recovery console.

The  "boot.ini" on the Win 7 partition uses "rdisk(0)". This means that ntldr on the Win partition  looks on the boot drive for the XP opererating system. If you change that to "rdisk(1)" you will be able to boot XP64 via
   
[CENTER]sdb->Grub->Win7_bootloader->XP64. [/CENTER]

But then

[CENTER]sda->Win7_bootloader->XP64
[/CENTER]

will no longer work


It is possible to configure Grub2 so that all both of these work, but you would either have to edit the Grub2 configuration files or create a Custom entry for Win 7.  Or you  could add a another entry to Win 7 boot loader.


Instead I would suggest to  hide the Win 7 boot menu, so that you boot directly into Win7 when you choose Win7 at the Grub menu:


Boot into Win 7.  Click on "Start". Type "cmd" and press "Ctrl+Shift+Enter". This opens the Win 7 command line with administrative rights. Type

```
bcdedit /set {bootmgr} timeout 0
```


But if your rather be able to boot XP64 via "sda->Win7_bootloader->XP64" let me know and I can show you how to do it.

---

### Post by Shocker on 2010-02-13
Hi meierfra,

thanks again for all your effort and technical exhaustive explanations.

For the time being I prefer to leave it like this as I can boot XP64 through:

sdb--> Grub--> XP64
sda--> Win7 bootloader--> XP64

What will not work is only the

sdb-->Grub --> Win7 bootloader--> XP64

as you have understood.

Have a nice continuation of the weekend!

Bye

Shocker

---

### Post by oldfred on 2010-02-13
This site has a lot of information on windows booting, I think meierfra. was trying to get each windows to boot after you have installed.

If a new install this works:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

