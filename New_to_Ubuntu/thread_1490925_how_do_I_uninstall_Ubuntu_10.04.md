---
title: "how do I uninstall Ubuntu 10.04?"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by jredkai on 2010-05-22
does anyone know the correct way to uninstall 10.04 off of a laptop setup to dual boot Vista and Ubuntu. I accidentally installed the 32-bit version and I wanted the 64-bit, now that I have the 64-bit I need to get rid of the 32 and keep windows. So, how should I go about this, do I do it from windows or Ubuntu? Any tips would be awesome.

---

### Post by Phrea on 2010-05-22
Just install Ubuntu 64b where you installed the 32b version.

---

### Post by Ozymandias_117 on 2010-05-22
So, are you saying that, right now you have three operating systems on your computer? Also, were they installed through Wubi or did you repartition your HDD

---

### Post by Rasa1111 on 2010-05-22
> **Phrea said:**
> Just install Ubuntu 64b where you installed the 32b version.

 yup. +1

---

### Post by jredkai on 2010-05-23
yes, as crazy as it sounds I have three operating systems on my laptop......yeah, so now that the 64 Lucid is on here can I just delete the 32 partition from the 64 and not mess up GRUB or the dual boot for vista and 64 Lucid???
Again, I'm a crazy newb and any advice is appreciated. Oh yeah, all I used was the installer for Ubuntu, so I didn't use Wubi or anything like that, and during the installation I just let Ubuntu make it's own partition on the hard disk.

---

### Post by Elfy on 2010-05-23
If you have the 32bit as well - you can remove that from within the 64bit - assuming you installed 64bit last it will have installed grub for itself and added the 32bit to it's grub.

Once you have removed the other one run

```
sudo update-grub 
```

and it will remove the 32bit from the list.

---

### Post by fidamehran on 2010-05-23
Dear Friends, I think jredkai mentioned already that he is a complete newbie. How would he know how to delete the 32Bit version from within the 64 Bit installation. I would have told him how, but I also don't know.
Care to explain a bit elaborately?

---

### Post by SoFl W on 2010-05-23
[]("http://ubuntuforums.org/member.php?u=1078108")jredkai
I would suggest a complete new install of the 64 bit version using both the current 64bit and the 32 bits disc space but using a separate home partition.  However this may not be easy.  I had a tri-boot system with W2K, another distro of linux and Ubuntu.  When I upgraded to 10.4 I did a clean install and removed and created new partitions for the 10.4 install.  

This however is a project in itself if you are a newbie but a great learning experience.   How much data/work do you have and can you save that to an external source?

---

### Post by KIAaze on 2010-05-23
> **fidamehran said:**
> Dear Friends, I think jredkai mentioned already that he is a complete newbie. How would he know how to delete the 32Bit version from within the 64 Bit installation. I would have told him how, but I also don't know.
Care to explain a bit elaborately?

1) Boot from a Live-CD
2) Start the partition editor (gparted):
System->Administration->Partition editor
3) Delete the partition corresponding to the 32-bit version
4) Resize the partition of the 64-bit version to use the new space

To find out which partition an OS uses, the easiest and safest way is to boot into it and run "df -h".
You'll get something like this:
```
df -h
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
**/dev/sda6             227G   15G  201G   7% /**
none                 1001M  320K 1000M   1% /dev
none                 1005M  260K 1005M   1% /dev/shm
none                 1005M  204K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw

```
The line in bold telling you that it is installed on /dev/sda6 in this example.

---

### Post by ronnielsen1 on 2010-05-23
> yes, as crazy as it sounds I have three operating systems on my laptop

[http://www.justlinux.com/forum/showthread.php?threadid=147959](http://www.justlinux.com/forum/showthread.php?threadid=147959)

> **[B][SIZE=4][COLOR=Blue]How to install and boot 145 operating systems in a PC[/COLOR][/SIZE]**[/B]

This is the "howto" I promised to write after [[COLOR=Red]**[SIZE=2]this thread[/SIZE]**[/COLOR]]("http://www.justlinux.com/forum/showthread.php?threadid=143973").

The 145 systems are:-

3 Dos
5 Windows
137 Linux

---

### Post by Ozymandias_117 on 2010-05-23
Do you want the HDD space from the 32b to go back to Windows or to Ubuntu?

---

### Post by Ozymandias_117 on 2010-05-23
@ronnielsen1 Holy crap, that is so incredibly unnecessary, but SO awesome!

---

