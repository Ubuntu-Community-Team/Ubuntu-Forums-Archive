---
title: "how to install windows xp"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by patchido on 2009-05-06
well, i have vista in my laptop, but i dont use it, its because is my familys laptop and my father tells me that he doesnt want me to mess it up so i use ubuntu from an external drive, i want to put xp on my external to be able to play some games, that i am aware i cant play on vista or ubuntu, so how can i install it without damaging grub or ubunut, the grub isnt on the laptop, it is directly on the EXT

thx


dell inspiron 1420

---

### Post by meindian523 on 2009-05-06
Install XP as normal,but reinstall Grub on the external,and be careful of using the proper names(your external should be sdb)Here's a HOW TO:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by patchido on 2009-05-06
but i first need to partitionate the disk |??? im in a live cd to be able to do it, but i dont wana mess up and im not sure how, can u guide me doin it through gparted?

---

### Post by meindian523 on 2009-05-06
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

The guide uses the GParted Live CD,you can use Partition Editor in System>>Administration on the Ubuntu Live CD.

---

### Post by powel212 on 2009-05-06
I run xp in a virtualBox in Ubuntu. This can be done on a flash drive install but the flash drive is going to need enough free disc space to allow for the xp install. You can also try wine for running windows programs. But I have never tried it with games. You might also be able to make a windows live cd and run your games off that. I have never done such a thing and don't know how to do it but you could try searching the forums.

Powel

---

### Post by linuxe on 2009-05-06
check it out
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by patchido on 2009-05-06
> **linuxe said:**
> check it out
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

plz read post, ur link actually has (xp installed first) my case is completly the oposite

---

### Post by lovinglinux on 2009-05-06
Reinstalling the Grub is not that complicated. I was afraid to do it until yesterday, when I decided to test Windows 7. Since then I have already reinstalled the grub twice, without problems.

Basically you will boot from Ubuntu Live CD, then run GParted (System >> Administration >> Partition Editor) and shrink the Ubuntu partition to make room for Windows. Then you will create a new partition using the unallocated space and format it as NTFS.  Follow the [tutorial provided by meindian523](http://ubuntuforums.org/showpost.php?p=7223390&postcount=4).

After that, reboot using Windows installation CD and install it on the new partition. When you finish Windows installation, grub will be gone and you will be able to boot only from XP.

Now it's time to restore grub. Follow the tutorial provided by [meindian523](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) or [this one](http://ubuntuforums.org/showthread.php?t=224351) (which I used). After completing this step, you will be able to boot from Ubuntu, but not from Windows XP. You need to [modify the menu.lst file to include the XP option](http://ubuntuforums.org/showpost.php?p=5739984&postcount=8).

That's it.

---

### Post by patchido on 2009-05-06
[QUOTE=
After that, reboot using Windows installation CD and install it on the new partition. When you finish Windows installation, grub will be gone and you will be able to boot only from XP.

Now it's time to restore grub. Follow the tutorial provided by [meindian523](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) or [this one](http://ubuntuforums.org/showthread.php?t=224351) (which I used). After completing this step, you will be able to boot from Ubuntu, but not from Windows XP. You need to [modify the menu.lst file to include the XP option](http://ubuntuforums.org/showpost.php?p=5739984&postcount=8).

That's it.[/QUOTE]

the problem is that this never happened :S my xp never booted, and i can boot ubuntu so my grub went untouched and that is really weird :S

---

### Post by caljohnsmith on 2009-05-06
> **patchido said:**
> the problem is that this never happened :S my xp never booted, and i can boot ubuntu so my grub went untouched and that is really weird :S
Actually that may not be so weird, because what may have happened is that XP put its boot file in some primary NTFS/FAT partition on your internal drive, and that would most likely be your Vista partition. If that is the case, XP would have also rewritten the MBR of your internal drive with a Windows MBR (which it all ready has), but XP would have left Grub on your external drive untouched. Also, XP would have rewritten your Vista partition boot sector with XP boot sector code, meaning that it will boot "ntldr" rather than "bootmgr". Maybe you have it all sorted out all ready and can boot XP from Grub, but if you don't and you would like some help, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup so we can get an idea what happened since your XP install.

John

---

### Post by patchido on 2009-05-06
well, i managed to return vistas mbr, and i installed windows into the external, but i made it my internal,( i disconnected my original internal drive and inserted my external,) and now windows was installed, but it wont work, the mbr is correct, it starts "loading" but after a sec i get a milisecond blue screen and the computer reboots, then i get windows error of start windows normally, blah , blah


:S im stuck in here

the installation cd might be wrong?

---

### Post by lovinglinux on 2009-05-06
Just to clarify some things, correct me if I'm wrong:

1 - Windows Vista is installed on the internal hard drive and you can boot it. It loads and works, but you have temporarily removed the disk.
2 - You managed to install Windows XP into the external drive making it temporarily internal
3 - Grub loads and you can choose between Ubuntu and Windows XP. Ubuntu loads and works, but Windows XP gives you a blue screen

---

### Post by patchido on 2009-05-06
things changed,now i reinstalled xp, but grub is gone as it should, how do i get it back?

---

### Post by patchido on 2009-05-07
well, i tried this tutorial[http://ubuntuforums.org/showthread.php?t=1148724&highlight=restore+grub]("http://ubuntuforums.org/showthread.php?t=1148724&highlight=restore+grub"), but i couldnt get it working, windows still poped up like if grub wasnt there, does anyone know why is this happening?

---

### Post by servicetech on 2009-05-07
I'd look into picking up another external drive for XP. You were already looking for an excuse to upgrade anyways right? ;)

---

### Post by albinootje on 2009-05-07
> **patchido said:**
> things changed,now i reinstalled xp, but grub is gone as it should, how do i get it back?

To recover Grub :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You can use "SuperGrub", and choose "manual" and then choose the MBR of the external for Grub to use.

---

### Post by patchido on 2009-05-07
thx now i got it, maybe i shouldnt tell you this cause it will sound so noob, but it was because i never did quit

xD

---

### Post by patchido on 2009-05-07
ok, windows installed correctly and i returned grub and im in ubuntu but when i click in grub to windows i get starting up and it will stay there forever, any ideas why?

this is my fdisk:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed260086

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5080    40805068+  83  Linux
/dev/sda2   *        5081        6992    15358140    7  HPFS/NTFS
/dev/sda3            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris
patricio@patricio-laptop:~$ 


```
but this is right now that i placed my external into my laptop as internal, it shouldnt be like this, but i dont think that matters, does it? and this is my menu.lst

```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c209b65b-ace7-430f-bda0-e9ee0ac2c2ef ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c209b65b-ace7-430f-bda0-e9ee0ac2c2ef ro  single
initrd		/boot/initrd.img-2.6.27-11-generic


title		Ubuntu 8.10, memtest86+
uuid		c209b65b-ace7-430f-bda0-e9ee0ac2c2ef
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Guindows Xp
root		(hd0,2)
savedefault
chainloader	+1
```

---

### Post by patchido on 2009-05-07
now im as it is suposed to be xD

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65cc02ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317       14267   104023036    7  HPFS/NTFS
/dev/sda4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed260086

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5080    40805068+  83  Linux
/dev/sdb2   *        5081        6992    15358140    7  HPFS/NTFS
/dev/sdb3            6993        7296     2441880    5  Extended
/dev/sdb5            6993        7296     2441848+  82  Linux swap / Solaris
patricio@patricio-laptop:~$ 

```

---

### Post by albinootje on 2009-05-08
> **patchido said:**
> 
```

title		Guindows Xp
root		(hd0,2)
savedefault
chainloader	+1
```

See here :
[http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10)
Add this to that section :
```

map (hd0) (hd1)
map (hd1) (hd0)

```

---

### Post by patchido on 2009-05-08
what does that make?

---

### Post by blazemore on 2009-05-08
Good guide here: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by patchido on 2009-05-08
do i need this or the map thing is enough ??

[http://www.ngine.de/index.jsp?pageid=4176]("http://www.ngine.de/index.jsp?pageid=4176")

---

### Post by patchido on 2009-05-08
i did it 2 ways, first by editting the menu.lst, and it woudlnt work, it woudnt boot, and then i erased it and did it from terminal as the link sayas and it was as if i didnt change grub i got windows "loading" and crashing am i doing it wrong?

---

### Post by ACupOfCoffee on 2009-05-08
Your ultimate goal is to boot a non-hacked copy of Windows XP from an external drive, right? Well that's impossible. It can only be done with hacked copies and the legality of those things is murky at best.

---

### Post by Jon Monreal on 2009-05-08
Remember to make sure that XP drivers are available before installing as well. This is especially important for laptops.

Edit: I'm going to be offline for a while, but you can PM me if you need further help (the link is in my signature).

---

### Post by patchido on 2009-05-09
what do you mean before installing? before installing what thing? at first i had no drivers but i already installed all of them to the windows partition by putting it as an internal drive

---

### Post by patchido on 2009-05-09
ill close this thread, went out topic, ill make a new one about botting winodws from external devices

---

### Post by Jon Monreal on 2009-05-09
Just for clarification: I was not being off-topic, just simply saying that you should make sure that drivers are available before you do anything, so you don't waste any time trying to do this while the drivers aren't available anyways.

The problem is installing XP on an external drive. You probably won't get too much help here, and not because we don't want to help you.


Perhaps you should check out Virtualbox as suggested above. That would allow you to run XP on top of the Ubuntu installation if the laptop is powerful enough.

---

