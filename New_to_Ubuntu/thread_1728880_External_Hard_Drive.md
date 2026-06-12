---
title: "External Hard Drive"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by corncob on 2011-04-14
I had installed Natty Alpha on an external USB HD just to see what it looked like.  Now I find that the computer won't boot if I remove the HD -- it just goes to the grub rescue prompt (which I don't know what to do with).  I'd like to eventually upgrade the 10.10 installation on the computer but don't think that would fix the problem: I'd like to take the USB drive off and use it for other things.  Please help.

---

### Post by rosencrantz on 2011-04-14
Did you let the Natty install overwrite your Grub configuration?
Maybe your hard drive order is messed up - the USB drive is hd0 and the built-in is hd1. 
Boot, with the USB stick removed, from grub rescue. Do you remember which partition Maverick is installed to? The following is for sda5:

set root=(hd0,4)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

Edit: root=(hd0,4) should probably be root=(hd0,5) on grub2

(taken from [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2))

---

### Post by rosencrantz on 2011-04-14
I forgot: after a successful boot, do sudo update-grub.

---

### Post by oldfred on 2011-04-14
Grub almost always defaults to installing its boot loader in the MBR of sda. So any install to another device overwrites the boot loader of the usually first boot device. You have to use manual install to have a choice on where to install grub's boot loader.

If you can boot into your internal install you can just reinstall grub2's boot loader to the MBR of sda from there. If you want to boot the external directly you can do the same from that install (you have to have booted into the install) but to sdb or whatever drive it is. Only one line is actually required. The rest are to confirm which drive you are using and to update if necessary.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by ajgreeny on 2011-04-14
I am fairly certain that you let the USB installation put its version of grub onto the internal hard disk, which is always the default on install unless you choose otherwise from the "Advanced" button that appears somewhere in the install.

You can restore grub from your 10.10 very easily with a live CD.  See section 13 of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by rosencrantz on 2011-04-14
Something I didn't realise (still mainly on grub1):
Apparently the grub2 syntax is different from grub1 with sda5 being (hd0,4) on grub1 and (hd0,5) on grub2.(Source [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)). If you are trying stuff from my previous post, please amend it.
If you can only boot from a live CD, try the CHROOT method. 
[https://help.ubuntu.com/community/Grub2#METHOD](https://help.ubuntu.com/community/Grub2#METHOD) 3 - CHROOT

---

### Post by corncob on 2011-04-14
Thanks Guys & Gals!  Disconnecting the external drive and running
```
corncob@eeebox:~$ sudo grub-install /dev/sda
[sudo] password for corncob: 
Installation finished. No error reported.
corncob@eeebox:~$ 

```
I went on to run other stuff oldfred suggested.  I'll mark the thread as solved.

---

