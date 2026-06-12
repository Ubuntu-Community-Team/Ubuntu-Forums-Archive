---
title: "Multiple Questions. (Answer as you can :P )"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by adeee on 2011-05-19
Guys i have some questions.

1- i have dual boot system. and so when i try to install windows.  grub boor loader not shown and ubuntu disappears. and then i install ubuntu again. :( so is there any way if i install windows xp and then i can get back ubuntu again. no need to install ubuntu.

2- what is the best screen capture video software? i need these features.

[LIST=1]
[*]i can zoom while i record specific area?
[*]mouse pointer have colour.
[*]voice quality not broken?
[*]and export any format i want. (avi, flv, mp4, ogg) :
[/LIST]
3- How to maximum compress video without loosing video quality? i mean how to reduce the size of video. 100 mb to Approximate 20mb :P

4- who is the best? docky or awn? quality wise or cpu effective wise? :

5- is there anyway to change the keyboard layout directly?

6- how to add my own color scheme in gedit?

7- How to backup the softwares and upgrades i install in this ubuntu installation? 

8- what i need to chose file system? ext3 or ext2?


Any links you provided for solution is really appreciated. :P

---

### Post by jre6 on 2011-05-19
1. I think you may have to mess up with boot.ini file in Windows. The boot.ini file looks like this:
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr = "Ubuntu"

```I think that changing the third line should help, but I have no idea as to what to replace it with.

2. Recordmydesktop : [http://recordmydesktop.sf.net/about.php](http://recordmydesktop.sf.net/about.php)

3 .FFmpeg converts, but not sure if lossless. It also often gives WMA, WMV files that are unreadable in Windows Media Player. You can also install Kino or Avidemux. No experience with Avidemux, but Kino first converts any video to .dv format and then allows conversion to a few formats like FLV or AVI. Good quality conversion but not with 20% compression ratio as you were talking about.

4. Prefer to use awn. More features than docky.

6. [https://answers.launchpad.net/ubuntu/+source/gedit/+question/14370](https://answers.launchpad.net/ubuntu/+source/gedit/+question/14370)

7. After installation of the software has completed, type this in a terminal:
```

sudo cp /var/cache/apt/archives ~

```The packages will be transferred to the home directory. You can change the destination (the home directory is the destination here, so we have put "~" ).

8. 10.04 uses ext4 by default. You may read about them here:

[http://en.wikipedia.org/wiki/ext2](http://en.wikipedia.org/wiki/ext2)
[http://en.wikipedia.org/wiki/ext3](http://en.wikipedia.org/wiki/ext3)
[http://en.wikipedia.org/wiki/ext4](http://en.wikipedia.org/wiki/ext4)
[https://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions](https://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions)

---

### Post by bennachie on 2011-05-19
I'll just deal with the dual-boot issue (Q1) at this stage. I'm not quite sure what is going on here. The usual situation is to have a Windows system installed on your system before you start. That will normally be in a slice of your hard disk (a partition) formatted as NTFS. Sometimes you will have two NTFS partitions, one for the system and basic data and the second for other Windows stuff that you have explicitly chosen to put there (backups etc). 

When you come along with an Ubuntu LiveCD, and initiate the process of installing the system to the hard disk, you should have been offered the opportunity to install Ubuntu alongside Windows. If you choose that option, the installer will take over a proportion of the free space remaining in the Windows system partition, create a new partition there, format the partition as "ext4", and install Ubuntu. After completing the installation and restarting the computer, you will have the choice of booting into Ubuntu (the default) or into Windows.

Could you tell us exactly how what you did differs from the above scenario?

---

### Post by adeee on 2011-05-19
Thank you.
brother record my desktop is command line. and he has those features i require?

and
remaining? :P

---

### Post by adeee on 2011-05-19
> **bennachie said:**
> I'll just deal with the dual-boot issue (Q1) at this stage. I'm not quite sure what is going on here. The usual situation is to have a Windows system installed on your system before you start. That will normally be in a slice of your hard disk (a partition) formatted as NTFS. Sometimes you will have two NTFS partitions, one for the system and basic data and the second for other Windows stuff that you have explicitly chosen to put there (backups etc). 

When you come along with an Ubuntu LiveCD, and initiate the process of installing the system to the hard disk, you should have been offered the opportunity to install Ubuntu alongside Windows. If you choose that option, the installer will take over a proportion of the free space remaining in the Windows system partition, create a new partition there, format the partition as "ext4", and install Ubuntu. After completing the installation and restarting the computer, you will have the choice of booting into Ubuntu (the default) or into Windows.

Could you tell us exactly how what you did differs from the above scenario?

Q1- according to this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

```
A Windows OS should be installed first, because its bootloader is very  particular and the installer tends to overwrite the entire hard drive,  wiping out any data stored on it
```

same with me. when i install winxp. its wipe oout entire disk and ubuntu just appears.
you can say i want to stop wiping out. :P

and about partition question. i have read article about ext2 its says this sile system is best then ext3 so am confuse. i usually use ext3 and have no any knowledge about linux partitions.

---

### Post by jre6 on 2011-05-19
> **adeee said:**
> Thank you.
brother record my desktop is command line. and he has those features i require?


Also see XVidCap : [http://xvidcap.sourceforge.net/](http://xvidcap.sourceforge.net/) and Wink : [http://www.debugmode.com/wink/](http://www.debugmode.com/wink/) as Recordmydesktop doesn't have all that you ask for.

FFmpeg can also do that, but its diificult : [http://www.ffmpeg.org/ffmpeg-doc.html](http://www.ffmpeg.org/ffmpeg-doc.html) and [http://embraceubuntu.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/](http://embraceubuntu.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/)

> **adeee said:**
> and remaining?

Previous post edited. See that.

---

### Post by bennachie on 2011-05-19
Install Windows first, make sure it's working correctly.

Then install Ubuntu, choosing the option to install alongside Windows.

Result - happy dual-booting.

Don't worry too much about the file systems. "ext2" was, for many years, the standard Linux file-system. It was superseded by "ext3", which has a range of technical advantages over "ext2". 

Most modern Linux distributions use "ext4". This is a journaling file system (meaning, roughly, that the system keeps track of file operations in a separate "journal"). There is some overhead involved in doing so. As a result, systems installed using "ext3" are slightly more responsive in normal use. But systems based on "ext4" are quite a bit more robust, with a much greater capacity to recover from transient events such as, for example, an interruption in the power supply.

---

### Post by prshah on 2011-05-19
> **adeee said:**
> is there any way if i install windows xp and then i can get back ubuntu again. no need to install ubuntu.

Short and dirty method (Expert method)
[indent]BEFORE installing windows, backup your MBR; boot in Ubuntu, and give the command```
sudo dd if=/dev/sda of=/root/mbrbackup bs=446 count=1
``` Replace /dev/sda with your actual hdd device. Then install Windows. Then boot off the live CD (since grub is overwritten) and open the terminal (Applications-Accessories-Terminal) and use the following commands to replace the MBR```
sudo mount /dev/sdaX /mnt -o defaults,ro
sudo cp /mnt/root/mbrbackup /root/mbrbackup
sudo umount /mnt
sudo swapoff -a #also unmount any other active partitions in /dev/sda
sudo dd if=/root/mbrbackup of=/dev/sda bs=446 count=1
sudo reboot
``` After this, GRUB should continue as before the Windows (re)install.

Warning: "dd" is a dangerous command at best. Please understand what you are doing in order to prevent mistakes that can wipe data. Replace /dev/sda and /dev/sdaX with actual HDD device and linux partition device. At your own risk, please.

> **adeee said:**
> 
2- what is the best screen capture video software? i need these features.

Record my Desktop has always worked fine for me. Install it with ```
sudo apt-get install recordmydesktop
```

> **adeee said:**
> 
[LIST=1]
[*]i can zoom while i record specific area?
[*]mouse pointer have colour.
[*]voice quality not broken?
[*]and export any format i want. (avi, flv, mp4, ogg) :
[/LIST]
3- How to maximum compress video without loosing video quality? i mean how to reduce the size of video. 100 mb to Approximate 20mb :P


Cannot zoom, mouse pointer is WYSIWIG, if voice quality is broken it is a symptom of some other problem, and the video can be exported/compressed through another software called ffmpeg.

> **adeee said:**
> 
5- is there anyway to change the keyboard layout directly?
 You can cycle between installed keyboard layouts using Shift-CapsLock. This is configurable, so please check in System-Preferences-Keyboard-Layout-Options.

> **adeee said:**
> 
8- what i need to chose file system? ext3 or ext2?
ext4 is recommended. ext3 is fine too. Definately not ext2 (non-journaling file system).

---

### Post by balgaltz on 2011-05-19
> 1- i have dual boot system. and so when i try to install windows. grub boor loader not shown and ubuntu disappears. and then i install ubuntu again.  so is there any way if i install windows xp and then i can get back ubuntu again. no need to install ubuntu.Let me explain what happened:
When you first installed Ubuntu, your MBR was using grub as bootloader.
Then when you installed Windows, it overwrote the MBR. Hence the loss of the option to boot Ubuntu.

**Solution:** You can boot a LiveCD and run > sudo grub-install /dev/sda
You can find out what drive you are using with System>Administration>Disk Utility
But its usually /dev/sda if you only have one physical drive.

Regarding your other questions, our fellow ubuntu brothers did an awesome job.

---

### Post by adeee on 2011-05-20
> **prshah said:**
> Short and dirty method (Expert method)[indent]BEFORE installing windows, backup your MBR; boot in Ubuntu, and give the command```
sudo dd if=/dev/sda of=/root/mbrbackup bs=446 count=1
``` Replace /dev/sda with your actual hdd device. Then install Windows. Then boot off the live CD (since grub is overwritten) and open the terminal (Applications-Accessories-Terminal) and use the following commands to replace the MBR```
sudo mount /dev/sdaX /mnt -o defaults,ro
sudo cp /mnt/root/mbrbackup /root/mbrbackup
sudo umount /mnt
sudo swapoff -a #also unmount any other active partitions in /dev/sda
sudo dd if=/root/mbrbackup of=/dev/sda bs=446 count=1
sudo reboot
``` After this, GRUB should continue as before the Windows (re)install.

Warning: "dd" is a dangerous command at best. Please understand what you are doing in order to prevent mistakes that can wipe data. Replace /dev/sda and /dev/sdaX with actual HDD device and linux partition device. At your own risk, please.




What about this method i find. 

```
             with the Live CD Ubuntu
 sudo grub &#8211;batch 
 grub> 
 grub> find /boot/grub/stage1
 grub> root (hd0,1)
 grub> setup (hd0)
grub> quit
             

```People not understand what i want to say.
let me explain again. i have 80 gb hard and devided into 40 gb of each windows xp and ubuntu.
 
unfortunately i cant complete migrate to ubuntu. for some adobe software's. 
and as you know virus effects. :P
so i need to install xp every month.
first time i install xp first and the install ubuntu.
works fine.
now again when i try to install win xp then grub MBR just disappears. not shown the option to select or chose OS.
When i insert Live CD it show that ubuntu are in harddisk. but windows wipe out the ubuntu during installation. 

I need assistance to get again ubuntu functional. not need to install ubuntu again.:(

What you say if above procedure is best.

Dear prshah. 
i cant mess up with dangerous commands because i have too much important data on ubuntu. so i need fare method. thanxs for your assistance. Hope you understand what i want to say. and also thanxs for other answers.

and about the screen capture software.see this video

[http://www.youtube.com/watch?v=I1bnipR_9nU](http://www.youtube.com/watch?v=I1bnipR_9nU)

i want a software that give exactly magnifier option that are in this video. :KS
[http://www.youtube.com/watch?v=satMTNW5tWY&feature=related](http://www.youtube.com/watch?v=satMTNW5tWY&feature=related)

also zooming like this toturial.

---

### Post by compmodder26 on 2011-05-20
> **bennachie said:**
> Most modern Linux distributions use "ext4". This is a journaling file system (meaning, roughly, that the system keeps track of file operations in a separate "journal"). There is some overhead involved in doing so. As a result, systems installed using "ext3" are slightly more responsive in normal use. But systems based on "ext4" are quite a bit more robust, with a much greater capacity to recover from transient events such as, for example, an interruption in the power supply.

Not true.  ext3 is also a journaling file system.  ext2 is not.  And ext4 is faster than ext3.

---

### Post by oldos2er on 2011-05-20
> **adeee said:**
> 
I need assistance to get again ubuntu functional. not need to install ubuntu again.:(


Are you using legacy grub or grub2? [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

