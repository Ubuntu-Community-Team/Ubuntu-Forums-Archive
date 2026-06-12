---
title: "Can't figure out how to re-install grub"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-06-17
I have Kubuntu installed and decided to give the Windows 7 RC a try, so I installed it, knowing full well that I would need to replace grub. Unfortunately, I can't figure out how to use grub-install. Could someone give me the command that I should use?

Partition map:

/dev/sda1 Windows (some kind of /boot I think, 100MB)
/dev/sda2 Windows 20GB
/dev/sda3 Logical
  /dev/sda5 Kubuntu (This is the partition that I need grub to be able to boot from)
  /dev/sda6 empty
  /dev/sda7 (Mandriva /boot, not important)
  /dev/sda8 (Mandriva /, not important)
/dev/sda4 encrypted partition

I know how to add entries for the other OSes in /boot/grub/menu.lst; I just need to figure out how to install it.

Thanks

---

### Post by pastalavista on 2009-06-17
searching is easier than asking. I've searched this one many times

[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

:)good luck..

---

### Post by Technoviking on 2009-06-17
It is easy to fix this, and all you need is an Ubuntu install CD or LiveCD.  Once the Ubuntu Live session finishes booting you should see a Ubuntu basic desktop. Open a terminal window ***Applications -> Accessories -> Terminal*** and type the following in the terminal window:
```
sudo grub
```
This will open grub command line interface. At the ***grub*** prompt, enter the following commands. 

```
find /boot/grub/stage1
```
This will tell you what hard drive and partition  grub is on. For this example we will use (hd0,0), which means first partition on the first hard drive. That is a very common setup. Now we want to repair the grub ```
bootloader.
root (hd0,0)
setup (hd0)
exit
```
The root command point to the proper area of the harddrive and the setup command install grub to the MBR (Master Boot Record). Close down your Ubuntu LiveCD session, remove the CD, and reboot your computer normally. Your Ubuntu boot menu should be back.

T-V

---

### Post by LewRockwell on 2009-06-17
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

