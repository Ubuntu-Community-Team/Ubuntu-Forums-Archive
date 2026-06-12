---
title: "I think I probably screwed up here... [Win/Ubuntu dual boot]"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by Gustavson on 2011-02-26
Okay, so recently I built my own computer and decided to dual boot Windows 7 and Ubuntu. I was able to build it relatively quickly and decided to install Ubuntu due to the fact that the windows 7 Disk had not arrived yet. Now I am completely lost, I am new to Ubuntu and don't really know how it works, which leads to this post.

I am having trouble finding a way to create a partition on the hard drive through Ubuntu to install windows on, and have no Idea how I would create said partition. (you can see I obviously didn't think this through). So now comes my question, is there a way to create a partition to install windows on. Or would I have to wipe my hard drive and Install windows then Ubuntu? (and if that's the case how would I be able to do that?) Or is there some other way to do this that I have not heard of yet. 

Any help is greatly appreciated.

---

### Post by Frogs Hair on 2011-02-26
Here are a couple of resources .

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by howefield on 2011-02-26
It is easier to install Windows first then Ubuntu, but by no means the only way. Windows will wipe out your grub meaning you won't be able to boot into Ubuntu until you reinstall grub.

Booting up with the Ubuntu Live CD and going to System > Administration > GParted Partition Editor will allow you to partition up your disk.

---

### Post by sikander3786 on 2011-02-26
Welcome to Ubuntu and the forums :-)

First of all, Windows needs a primary partition to boot from and secondly, after installation of Windows, you'll need to re-install Grub (Ubuntu bootloader) for dual-booting as Windows over-writes the MBR.

You can install GParted and use it for partitioning purposes. Go to Applications > Software Center and search for GParted or go to Applications > Accessories > Terminal and paste the following command.

```
sudo apt-get update && sudo apt-get install gparted
```

When you type your password, you won't see any asterisks on the screen, just type blindly and hit <Enter>.

GParted will appear under System > Administration > GParted.

In order to let us advise more efficiently on your partitioning, it would be better to post the output of this command before you actually partition your disk and have a look at our advice.

```
sudo fdisk -l
```

For an overview of restoring Grub after Windows installation, see here.

[http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html](http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html)

However, we can give you exact commands to follow (just 2 of them) after you finish Windows installation. We need to go step by step.

Feel free to ask any further queries :-)

---

### Post by IWantFroyo on 2011-02-26
You should probably just install Windows first, then Ubuntu. Windows just overwrites any Ubuntu installation, so you I doubt you'll have to wipe the drive. Then you can burn a GParted cd or usb and boot off that, and find a guide on dual boot partitioning. Or you can just put in a Ubuntu cd/usb while booted into Windows, and run it to get Wubi (if you can't run the cd/usb, go into the Ubuntu folder on it and open wubi.exe). Then, Wubi can guide you to install Ubuntu alongside Windows without partitioning. You can just uninstall Ubuntu like any other Windows application that way (by searching for a Windows folder and running uninstallubuntu.exe.
Good luck!

---

### Post by Gustavson on 2011-02-27
Thanks guys everything is working great now, Dual Booting Windows 7 and Ubuntu now. So far its working without a problem.

---

