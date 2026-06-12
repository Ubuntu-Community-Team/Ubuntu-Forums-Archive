---
title: "Ubuntu 10.04 not working after Install Fedora 13"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by bandersen on 2010-07-12
I went into the menu.lst and tried to add ubuntu back in myself. 
 
I got as far as this,
 
title Ubuntu
root (hd0,0)
kernel /boot/vmlinuz-2.6.32-23-generic ro  root=UUID=a5fb9b27-e25c-4cfc-8934-77b2179724ac
boot
initrd /initrd.img-2.6.32-23-generic
 
It doesn't work, anyone care to help?

---

### Post by Darkness Des on 2010-07-12
PROBABLY because menu.lst doesn't exist in 10.04. It uses GRUB2. Someone on the forums has a complete guide to it. Google it.

---

### Post by bandersen on 2010-07-12
Yes, but i'm using Fedora's grub loader to boot itself and ubuntu...

---

### Post by Rubi1200 on 2010-07-13
You have 2 options in my opinion:

1) ask on the Fedora forums for help (they don't bite)

2) re-install the Ubuntu bootloader:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

GRUB2 _should_ recognize Fedora and you will be back in business.

I once dual-booted Ubuntu and Fedora and let GRUB handle things (which it did very nicely), but this was with older versions of both distros.

---

### Post by oldfred on 2010-07-13
I agree with reinstalling Ubuntu's grub2.

Old grub to boot most current kernel. uses link files in root:

title Ubuntu
root (hd0,0)
kernel /vmlinuz root=/dev/sda1 ro
initrd /initrd.img

---

### Post by Yarui on 2010-07-13
I would agree that restoring grub2 in your Ubuntu install is probably the easiest solution, but if you would prefer to stick with the fedora grub I have two thoughts.

1)  It could be that (hd0,0) is the wrong partition.  Although I doubt this is the problem.

2)  Maybe you should use /vmlinuz-2.6.32-23-generic instead of /boot/vmlinuz-2.6.32-23-generic.  Generally you shouldn't designate the /boot part because that is the directory that is being read from, so it would only work if you have a recursive reference to /boot within your /boot folder, because if you specify it with the /boot the grub looks for your kernel in /boot/boot/vmlinuz-2.6.32-23-generic (I think).  I can't remember if Ubuntu has this recursive link or not and I can't seem to see inside my Ubuntu /boot directory on my current partition.

---

### Post by bandersen on 2010-07-13
I got grub2 back up and running, but now it doesn't detect fedora 13 now!

---

### Post by Yarui on 2010-07-13
> **bandersen said:**
> I got grub2 back up and running, but now it doesn't detect fedora 13 now!
Did you run the following command?
```
sudo update-grub
```
In my experience grub2 is very good at detecting other linux installations when you update the grub list.

---

### Post by bandersen on 2010-07-13
That did not work, sir.

---

### Post by v1ad on 2010-07-13
u put it in under (0, 0) make sure you got the right partition.

---

### Post by bandersen on 2010-07-13
No idea what you're talking about... I'm using Grub2 now.

---

### Post by garvinrick4 on 2010-07-13
You have to use a live CD and use these codes. Given that my Ubuntu install is sda5
and my label on the Ubuntu install is lucid. Use your own, can label in gparted or disk utility. The one mount labeled System is if you have a seperate /boot partition if you do
not ignore the directory and mounting of it.


                                 Reinstall grub 2 Live CD 

Make a directory: ```
sudo mkdir /media/lucid
```Mount your OS with grub on it:```
 sudo mount [/dev/sda5]("file:///dev/sda5")[ /media/lucid]("file:///media/maverick")
```Mount mbr on seperate partition if is one: ```
sudo mount [/dev/sda1 /media/SYSTEM]("file:///dev/sda1/media/SYSTEM") 
```Install Grub to sda: ```
sudo grub-install --root-directory=/media/lucid [/dev/sda]("file:///dev/sda") 
```Reinstall: ```
sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///dev/sda")

```Unmount partition:```
 sudo umount [/media/lucid]("file:///media/maverick") 
```Unmount MBR partition: ```
sudo umount [/media/SYSTEM]("file:///media/SYSTEM")
```When you boot into your Ubuntu lucid install.
sudo update-grub
This will install fedora 13 into your grub2 menu
sudo grub-mkconfig

---

### Post by Yarui on 2010-07-13
> **bandersen said:**
> That did not work, sir.
Just to be absolutely sure, did you run update-grub in Ubuntu or Fedora?  It should be run in Ubuntu so that the Ubuntu grub2 gets updated.  I'm sure you probably did this right, just checking.

I once had update-grub find a linux partition but didn't add it to the list for some reason, and I could never figure out what was wrong with it.  If the partition isn't auto-detected I'm not really sure what to do.  I would probably try to read more about grub2 and how to add new partitions to the menu, of course, but other than that I don't have any more ideas.

---

### Post by garvinrick4 on 2010-07-13
> **Yarui said:**
> Just to be absolutely sure, did you run update-grub in Ubuntu or Fedora?  It should be run in Ubuntu so that the Ubuntu grub2 gets updated.  I'm sure you probably did this right, just checking.

I once had update-grub find a linux partition but didn't add it to the list for some reason, and I could never figure out what was wrong with it.  If the partition isn't auto-detected I'm not really sure what to do.  I would probably try to read more about grub2 and how to add new partitions to the menu, of course, but other than that I don't have any more ideas.After reinstalling grub2 to Ubuntu then:
```
sudo update-grub
``````
sudo grub-mkconfig
```You installed grub legacy when you installed  fedora 13. Should be know
big deal at all. I have installed multiple times and on flash drives to send to my brother.
If you cannot reload grub2 to your mbr and then update-grub then something other is wrong. If you would copy this script to desktop and make the text file then copy and paste to this thread.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by oldfred on 2010-07-13
Supposedly the latest grub solved the issues with finding fedora.
See Kansasnoob comments 40 & 42 Install grub 1.98  & to fix major grub issues
here was a BIOS option setting in the boot loader device selection in the Fedora installer. Comment #44
[http://ubuntuforums.org/showthread.php?t=1415879](http://ubuntuforums.org/showthread.php?t=1415879)

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

You would have to adjust just about everything to make this one work for you.

menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

---

### Post by garvinrick4 on 2010-07-14
I have just been looking over my install of fedora 13 on my sda drive and it seems when
I installed fedora when came to where to put boot I selected no where. And if I remember right it defaults to LVM and I never use. I am sure that needed not be said. I have never seemed to have a problem with any install of fedora. Of course had to reinstall grub2 from Ubuntu install to mbr and update a few times. ( Using Intel chipset and graphics card.)

---

