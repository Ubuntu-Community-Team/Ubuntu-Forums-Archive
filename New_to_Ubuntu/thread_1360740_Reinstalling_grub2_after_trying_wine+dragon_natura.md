---
title: "Reinstalling grub2 after trying wine+dragon naturally speaking"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Agris on 2009-12-21
----------------------------------------------------------------------------------
Edit :
It appears that my problem had nothing to do with grub2 reinstallation.
I had moved inadvertently boot files/directories to a wrong place.
That's the reason why grub couldn't find the stuff it needed...

sudo+sensitive touchpad = evil :)
----------------------------------------------------------------------------------


Hello everyboby! I'm totally new in posting and in linux (and not so good in english), so I'll try my best to be clear and concise.

First, [here]("http://forum.ubuntu-fr.org/viewtopic.php?id=366940")'s the first place I explained my problem, if useful (on ubuntu.fr forum).
Then, my issue :
I installed wine on my ubuntu 9.10. Then I tried to install Dragon Naturally Speaking preferred 10 (¨DNS" for the following). Ubuntu froze. A reboot told me: "grub: file not found" (if I remember well the syntax).

I've read a lot of posts, especially [here]("http://ubuntuforums.org/showthread.php?t=1353062&highlight=file+directory+chroot%3A+run+command+%60%2Fbin%2Fbash%27%3A&page=3") (and links provided), but I'm still afraid I could do something wrong going further and would really appreciate some advise.

Here's the stuff I currently have:
- Dell precision M4400, x86_64, AMD64.
  Installation made with the [DVD ubuntu 9.10's image for 64 bits PC (x86_64 -- AMD64)]("http://www.ubuntu-fr.org/telechargement?methode=")
  No windows stuff installed (simple boot).
- the DVD I used for the installation

Here's some information about the ¨DNS" files that may have corrupted my system:
- "Dragon NaturallSpeaking 10.msi"
- setup.exe, that may have called for : instmsia.exe, instmsiw.exe, WindowsInstaller-KB893803-x86.exe

Here's some information about my system (thanks to [presence1960]("http://ubuntuforums.org/member.php?u=657448")'s script, in [here]("http://ubuntuforums.org/showthread.php?t=1353062&highlight=file+directory+chroot%3A+run+command+%60%2Fbin%2Fbash%27%3A")). I highlighted stuff that really puzzles me :[INDENT][I]============================= Boot Info Summary: ==============================

[COLOR=Navy] => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.[/COLOR]
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

[COLOR=Navy]Disque /dev/sda: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Identifiant de disque : 0x00000080

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       417,689       417,627  de Dell Utility
/dev/sda2    *        417,690     4,626,719     4,209,030   b W95 FAT32
/dev/sda3           4,626,720   976,768,064   972,141,345   5 Extended
[COLOR=Purple]/dev/sda5           4,626,783   937,344,554   932,717,772  83 Linux[/COLOR]
/dev/sda6         937,344,618   976,768,064    39,423,447  82 Linux swap / Solaris[/COLOR]


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0A1D" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="07D9-0A1D" TYPE="vfat" 
/dev/sda5: UUID="cb68d86a-33d7-4a42-8a35-092f813858d7" TYPE="ext4" 
/dev/sda6: UUID="1dcdf2ea-56dd-4892-b59d-ca91c908bfeb" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

[COLOR=Navy]Unknown BootLoader  on sda2
[/COLOR]
00000000  eb 58 90 4e 75 6c 6c 20  34 2e 31 00 02 08 20 00  |.X.Null 4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 9a 5f 06 00  |........?...._..|
00000020  86 39 40 00 0d 10 00 00  00 00 00 00 02 00 00 00  |.9@.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
[COLOR=Navy]00000040  80 00 29 1d 0a d9 07 4e  6f 6e 42 6f 6f 74 61 62  |..)....NonBootab|
00000050  6c 65 46 41 54 33 32 20  20 20 fa b8 00 00 8e c0  |leFAT32   ......|
00000060  8e d0 bc 00 7c fb 0e 1f  fc b8 00 00 8e d8 bf 90  |....|...........|
00000070  7d b9 3c 00 bb 07 00 b4  0e 8a 05 90 90 cd 10 47  |}.<............G|
00000080  e2 f7 eb fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  4e 6f 20 6f 70 65 72 61  74 69 6e 67 20 73 79 73  |No operating sys|
000001a0  74 65 6d 20 69 73 20 63  75 72 72 65 6e 74 6c 79  |tem is currently|
000001b0  20 69 6e 73 74 61 6c 6c  65 64 20 6f 6e 20 74 68  | installed on th|
000001c0  69 73 20 63 6f 6d 70 75  74 65 72 2e 00 00 00 00  |is computer.....|[/COLOR]
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[/I][/INDENT]On ubuntu.fr's forum, I was told to run the following commands (I got an error with the last one, and I've no idea what should be done next):
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt

-->> chroot: cannot run command `/bin/bash': No such file or directory 

```I also tried this:[FONT=Arial]
[/FONT]```
sudo mkdir /media/system
sudo mount /dev/sda5 /media/system
sudo mount --bind /proc /media/system/proc
sudo mount --bind /sys /media/system/sys
sudo cp /etc/resolv.conf /media/system/etc/resolv.conf

-->> cp: ne peut créer le fichier régulier `/media/system/etc/resolv.conf': Aucun fichier ou dossier de ce type
```So, here are my questions:

[LIST=1]
[*]Do you have any idea the ¨Dragon NS" program made to my system ?
[*]Do you think I have any chance to restore my ubuntu, and what should I do to save data/programs/emails' settings and all this sort of things...
[*]Is really sda5 the partition I should mount ? (it's only my guess. It's not as if I knew what I'm currently doing).
[*]Should I do this ? (I'm sorry to ask, but I don't even understand if "Dragon NS" installed something from Windows):
```
sudo mount /dev/sda5 /mnt[FONT=Arial]
sudo grub-install --root-directory=/mnt/ /dev/sda[/FONT]
``` (seen [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"))
or this ?
```
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda
``` (seen [here]("http://ubuntuforums.org/showthread.php?t=1014708"))
or anything else ?
[/LIST]
Thanks a lot for your future help. And... Well, I guess I shall be more careful with programs designed for Windows, from now... Sigh 
See you...

---

### Post by presence1960 on 2009-12-21
```
sda5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
[COLOR="Red"]Operating System:
Boot files/dirs:[/COLOR]

```

Above is from your script. Your Ubuntu is not there it would seem. Here is a snippet from mine. Note the difference:

```
sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

What you can do is boot the Ubuntu Live CD/USB and open a file browser under Places > Computer and navigate to the Ubuntu directory and see if your directories/files are indeed there or not. I can tell you ypu are at least missing your boot files!

---

### Post by Agris on 2009-12-21
Thank you so much for replying!

It seems that I still do have my documents and eveything.
I'm not sure of the equivalent in french for > Places > Computer but here is what I have in "Poste de travail" (workplace):

[LIST=1]
[*]A file called "Disque dur 500GB: OS" (hard disk 500GB: OS)
Here are the informations provided by "properties":
Contains nothing. Is in /media. Total capacity 2.0 Gio, 4.0 Kio used, type of system file: msdos
[*]A file called "Disque dur 500GB: Système de fichiers 478 GB" (hard disk 500GB: system file 478 GB)
Here are its properties:
Contains 21.6 Gio (some elements are said impossible to be read). Free space of 3.8 Gio
Is in computer:/// (hum ??). Volume: unknown. Free space: 3.8 Gio
[*] A file called ¨Système de fichiers" (system file)
Contains:
- /dev (not empty)
- /lost+found
- /proc (empty)
- /sys (empty)
- /home, with:
                      a) my /myname directory, with my documents, files, data. (*ouf!*)
                      b) the /wine directory I created after installing wine, trying to follow these
                      [instructions]("http://doc.ubuntu-fr.org/wine").
[/LIST]
The directory /wine was supposed to contain the files of .wine, but I probably made something wrong.
It is also there (in directory /dragon) that I copy/paster the dragon naturally speaking files.
After I tried its installation with wine, some new directories appeared here : /bin, /boot, /cdrom, /etc, /lib, lib32, lib64, /lost+found, /media, /mnt, /opt, /root, /sbin, /selinux, /srv, /tmp, /usr, /var

Do you think I copied/pasted inadvertently my boot files here ??? How can I check that ?

Thank you.

---

### Post by philinux on 2009-12-21
I would just recover grub from the livecd.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

This method works.

---

### Post by Agris on 2009-12-21
@philinux

Well, unfortunately, as I said in my first post, this method did not work for me.
I had an error at this step:
> $sudo cp /etc/resolv.conf /mnt/etc/resolv.conf (I found indications about the meaning of that last command [here]("http://ubuntuforums.org/archive/index.php/t-1156240.html"))
More importantly I think, I had an error at this step:
> sudo chroot /mntI just want to find out what is going on, now.

But thank you for replying...

---

### Post by philinux on 2009-12-21
I would reboot your livecd and go though the link I gave you again. It is slightly different from what you used. 

Just make sure you get all the commands correct for your box.

---

### Post by Agris on 2009-12-21
[COLOR=Navy]@philinux[/COLOR]

It is true, the commands indicated by the link you provided me are slightlty different:
[SIZE=1]> $sudo fdisk -l

This will show your partition table.Here is my table to understand it better :

/dev/sda1              29        8369    66999082+  83  Linux
/dev/sda2   *        8370       13995    45190845    7  HPFS/NTFS
/dev/sda3           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Now i will mount Linux (sda1 here), i have no external boot partition as you can see.(IF YOU HAVE external one, do not forget to mount it! )

$sudo mount /dev/sda1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc[/SIZE]> 

[SIZE=1] The following command is optional (it copies resolv.conf)

$sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

Now chroot into the enviroment we made :

sudo chroot /mnt[/SIZE]   Here are the commands I used:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```As you can see, the difference lies in the partition I mounted (sda5 vs sda1). In my case, the partition table provided by the command ¨sudo fdisk -l" seems to indicate that my Linux partition is sda5.

[COLOR=Navy]Do you have any reason to think it is not so ?[/COLOR]

Moreover, partition sda1 seems to correspond to some ¨Dell utilities", which, I guess, were pre-installed in my computer. When I installed karmic from the LiveCD, I asked to devote the whole free space existing on my disk to karmic, and I chose not to overwrite what was pre-existing on my computer (bought with none system installed). At this moment, I thought that some stuff may have been pre-installed by Dell, to deal with pad, wifi, videocard and all. Probably I was wrong, but anyway.

More,[COLOR=Black] [I]"Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub",[/I] as said by the script.[/COLOR]

I never installed Windows, just because I wanted to try Linux and free programs. But that's another matter.
I tried to install the Dragon program, because as far as I could found on the web, there is currently no free alternative program of voice recognition and dictation... Several free options do exist of course, but not as powerful as Dragon. And that's another matter, too.
Moreover, despite the Dragon installation cd does contain a ¨windowsIntaller" stuff, I would find it weird if it was a Windows' distribution. I guess it's more some patch to deal with various versions of Windows.

Hum... I'm being less and less concise... Sorry for that.

[COLOR=Navy]@presence1960[/COLOR]
Now, to me, it really looks like the result of an involuntary copy-paste. Property rights are supposed to avoid this kind of creepy mistakes, but I needed to be in sudo mode to install wine. Sigh.

I found this out (... err, I *may* have found this out) because I just ran this:
```
cd /media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon/etc
```[COLOR=DimGray]/etc[/COLOR] does contain [COLOR=DimGray]fstab.[/COLOR]

[COLOR=Gray][COLOR=Black][COLOR=DimGray][COLOR=Black]Then I checked this:[/COLOR][/COLOR][/COLOR][/COLOR]
```
cd /media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon/boot/grub && ls
```And, here is what it contains:
[COLOR=Gray][SIZE=1]abi-2.6.31-14-generic     initrd.img-2.6.31-14-generic  vmcoreinfo-2.6.31-14-generic
abi-2.6.31-15-generic     initrd.img-2.6.31-15-generic  vmcoreinfo-2.6.31-15-generic
abi-2.6.31-16-generic     initrd.img-2.6.31-16-generic  vmcoreinfo-2.6.31-16-generic
config-2.6.31-14-generic  memtest86+.bin                vmlinuz-2.6.31-14-generic
config-2.6.31-15-generic  System.map-2.6.31-14-generic  vmlinuz-2.6.31-15-generic
config-2.6.31-16-generic  System.map-2.6.31-15-generic  vmlinuz-2.6.31-16-generic
[/SIZE] [SIZE=1][COLOR=Red]grub[/COLOR][/SIZE][SIZE=1]                      System.map-2.6.31-16-generic[/SIZE]

[COLOR=Black][COLOR=DimGray]/grub[/COLOR] does contain [COLOR=DimGray]core.img[/COLOR] and [COLOR=DimGray]grub.cfg[COLOR=Black], and a lot of other files.
[/COLOR][/COLOR][/COLOR][/COLOR]
All this seems to correspond to your boot files/dirs.

So now, and if my guess is good, would you mind telling me where is the normal place of boot files and directories ? If *this* was my problem, I guess I gave at least some funny time for people going through this thread... :/

Thank you for your help.

NB: just to give you information about the grub.cfg file:[INDENT][INDENT][SIZE=1][COLOR=DimGray]#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set cb68d86a-33d7-4a42-8a35-092f813858d7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cb68d86a-33d7-4a42-8a35-092f813858d7
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=cb68d86a-33d7-4a42-8a35-092f813858d7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cb68d86a-33d7-4a42-8a35-092f813858d7
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=cb68d86a-33d7-4a42-8a35-092f813858d7 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cb68d86a-33d7-4a42-8a35-092f813858d7
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=cb68d86a-33d7-4a42-8a35-092f813858d7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cb68d86a-33d7-4a42-8a35-092f813858d7
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=cb68d86a-33d7-4a42-8a35-092f813858d7 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cb68d86a-33d7-4a42-8a35-092f813858d7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cb68d86a-33d7-4a42-8a35-092f813858d7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cb68d86a-33d7-4a42-8a35-092f813858d7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cb68d86a-33d7-4a42-8a35-092f813858d7 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###[/COLOR][/SIZE][/INDENT][/INDENT]

---

### Post by kansasnoob on 2009-12-21
First try this to be sure nothing is partially mounted:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

If that shows any errors run all of these regardless of errors:

```
sudo umount /mnt/dev/pts
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

Then try to mount and chroot:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

If that appears to succeed add two more;

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Just for information:

```
df -H
``` (I'd like to see this!)

Now we'll completely reinstall grub2 - packages and all:

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub-pc grub-common
```

```
apt-get update && apt-get install grub-pc
```

```
update-grub
```

**You'll hopefully see that it recognizes Ubuntu but it will likely show that it can't see other OS's, that's to be expected. We'll fix that after Ubuntu hopefully boots by running "sudo update-grub" again!**

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

**Don't worry if that shows errors at this point!**

```
sudo reboot
```

If Ubuntu boots run:

```
sudo update-grub
```

---

### Post by kansasnoob on 2009-12-21
Also, just thinking out loud here, I suspect possible partition size limitations here. That's why I asked for the output of "df -H" from the chroot.

The only other way I can think of to see how much partition space is used would be to see a screenshot of Gparted from the Live CD. That could also be helpful in recommending how to recover data to a new install.

---

### Post by Agris on 2009-12-21
[COLOR=Navy]@kansasnoob[/COLOR]
Hello. I just find out how to unmount a litlle while ago, and did it.
Just to let you check what I had before I started your commands:

```
ubuntu@ubuntu:~$ mount -l
```[SIZE=1][COLOR=DimGray]
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw) [Ubuntu 9.10 amd64]
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/OS type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush) [OS]
/dev/sda5 on /media/cb68d86a-33d7-4a42-8a35-092f813858d7 type ext4 (rw,nosuid,nodev,uhelper=devkit)[/COLOR][/SIZE]
So, as far as I understand, from this point, it is normal to obtain:
```
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
umount: /mnt/dev/pts: n'a pas été trouvé
``` Means that nothing is mounted, right?

Anyway, I ran the commands one by one. None of directory is found. Which means I guess that I correctly unmounted them. Cool, I'm learning. No more need to reboot, now :)

Then, I ran:```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
cp: ne peut créer le fichier régulier `/mnt/etc/resolv.conf': Aucun fichier ou dossier de ce type

```(cp: cannot create regular file `/mnt/etc/resolv.conf': No such file or directory)

Same error as previously... Seems that I don't have the right files in the right place.

Now here are the details about the system files you asked for:
```
ubuntu@ubuntu:~$ df -H
Sys. de fich.             Tail.  Occ.  Disp. %Occ. Monté sur
aufs                   4,2G   136M   4,1G   4% /
udev                   4,2G   312k   4,2G   1% /dev
/dev/sr0               4,2G   4,2G      0 100% /cdrom
/dev/loop0             1,3G   1,3G      0 100% /rofs
none                   4,2G   267k   4,2G   1% /dev/shm
tmpfs                  4,2G    41k   4,2G   1% /tmp
none                   4,2G    95k   4,2G   1% /var/run
none                   4,2G      0   4,2G   0% /var/lock
none                   4,2G      0   4,2G   0% /lib/init/rw
/dev/sda2              2,2G   4,1k   2,2G   1% /media/OS
/dev/sda5              471G    17G   430G   4% /media/cb68d86a-33d7-4a42-8a35-092f813858d7
/dev/sda5              471G    17G   430G   4% /mnt
ubuntu@ubuntu:~$ 
```The screenshot from Gparted is attached to this post.

Many thanks.

---

### Post by Agris on 2009-12-21
[COLOR=Navy]@kansasnoob[/COLOR]
... And please also find attached the screenshot I obtained after unmounting everything (I don't know if it&#347; useful, but anyway...)

See you.

Post-script about this remark: > **You'll hopefully see that it recognizes Ubuntu but it will likely show that it can't see other OS's, that's to be expected. We'll fix that after Ubuntu hopefully boots by running "sudo update-grub" again!**. Why should I have to other OS's ? Do you think that the DragonNS program installed Windows ? Wine isn't an OS, is it ? Hum, next time I install stuff, I'll read more and more about it before.

---

### Post by presence1960 on 2009-12-21
> @presence1960
Now, to me, it really looks like the result of an involuntary copy-paste. Property rights are supposed to avoid this kind of creepy mistakes, but I needed to be in sudo mode to install wine. Sigh.

I found this out (... err, I may have found this out) because I just ran this:

```
cd /media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon/etc
```



Then I checked this:

```
cd /media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon/boot/grub && ls
```


cd [COLOR="Red"]/media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon/etc[/COLOR]
cd [COLOR="Red"]/media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon/boot/grub[/COLOR] && ls

/etc should not be in /home & neither should /boot/grub

You say you were root when you were installing wine & dragon. You may have moved your /etc and /boot directories into your home directory. If so that is the problem and that is why no boot files are showing on the script results. Verify that the /etc and /boot directories are inside /home if they are open a terminal and cd to /etc and run ```
sudo mv /etc /
```

Next in terminal cd to /boot and run ```
sudo mv /boot /
```

Open a file browser from the Live CD to make sure your /boot and /etc directories are now in your Ubuntu root directory. Attached is a screenshot. On the right are all directories that should be in Ubuntu root. Bear in mind my screenshot was taken from within Ubuntu therefore the directories are in File System. From the Live CD you will have to look into the device that has Ubuntu on it not File System as that is the Live CD's File System!

[COLOR="Red"]P.S.[/COLOR] I just realized you will be moving /etc & /boot from the Live CD. From the Live CD open a file browser and mount the device containing your Ubuntu install (root) by clicking on it in the left pane. Now open a terminal and run ```
gksu nautilus
```

Navigate to your Ubuntu home directory (not the Live Cd's /home) and locate etc and boot directories. Highlight them, right click and select cut, then navigate to the Ubuntu install directory again and right click and select paste. This will put the etc and boot directories where they belong. Close both file browsers and reboot.

---

### Post by Agris on 2009-12-21
[COLOR=Navy]@presence1960
[/COLOR]
Ok.
I checked on dragon's cd what this one should contain.
Here are all the files/directories that currently are in /home while they shouldn't:

[COLOR=DarkSlateGray]/bin  /boot /cdrom  /etc    /lib   /lib32   /lib64  /lost+found  /media   /mnt  /opt   /root   /sbin   /selinux  /srv   /tmp  /usr  /var
initrd.img     initrd.img.old       vmlinuz    vmlinuz.old[/COLOR]

Should I just do this ?
```
ubuntu@ubuntu:/media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon$ pwd
/media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon

sudo mv each_of_them /media/cb68d86a-33d7-4a42-8a35-092f813858d7
```Is there any particular thing to do to displace directories with the command mv ? (hum... I can look for this by myself...)

Thanks for helping.

Edit: Woops. Sorry. Didn't read your post entirely. Just doing it...

---

### Post by presence1960 on 2009-12-21
> **Agris said:**
> [COLOR=Navy]@presence1960
[/COLOR]
Ok.
I checked on dragon's cd what this one should contain.
Here are all the files/directories that currently are in /home while they shouldn't:

[COLOR=DarkSlateGray]/bin  /boot /cdrom  /etc    /lib   /lib32   /lib64  /lost+found  /media   /mnt  /opt   /root   /sbin   /selinux  /srv   /tmp  /usr  /var
initrd.img     initrd.img.old       vmlinuz    vmlinuz.old[/COLOR]

Should I just do this ?
```
ubuntu@ubuntu:/media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon$ pwd
/media/cb68d86a-33d7-4a42-8a35-092f813858d7/home/wine/dragon

sudo mv each_of_them /media/cb68d86a-33d7-4a42-8a35-092f813858d7
```Is there any particular thing to do to displace directories with the command mv ? (hum... I can look for this by myself...)

Thanks for helping.

Edit: Woops. Sorry. Didn't read your post entirely. Just doing it...

I would move those directories back where they belong using root file browser (gksu nautilus). Then hopefully that will take care of the damage & you will be able to boot Ubuntu.

---

### Post by Agris on 2009-12-21
[COLOR=Navy]@presence1960[/COLOR]

Ok. I'm just really slow. I just finished to move everything. Just a last question before I reboot:
Here is what I have (please see below). Sounds correct, except for this: [COLOR=Navy].Trash-0
[COLOR=Black]It appeared after I tried to moved [COLOR=DarkSlateGray]lost+found[/COLOR] from [COLOR=DarkSlateGray]/dragon[COLOR=Black] to [/COLOR][/COLOR][/COLOR][/COLOR][COLOR=DarkSlateGray]/media/cb68d86a-33d7-4a42-8a35-092f813858d7, [COLOR=Black]saw that a [/COLOR][/COLOR][COLOR=Navy][COLOR=Black][COLOR=DarkSlateGray]lost+found [COLOR=Black]already existed in [/COLOR][/COLOR][/COLOR][/COLOR][COLOR=DarkSlateGray]media/cb68d86a-33d7-4a42-8a35-092f813858d7[/COLOR][COLOR=Navy][COLOR=Black][COLOR=DarkSlateGray][COLOR=Black] (although its was empty), and moved the [/COLOR][/COLOR][/COLOR][/COLOR]/dragon/lost+found to trash.

Should I just get rid of [COLOR=Navy].Trash-0[COLOR=Black] (and how ?) before I reboot, or is it ok ?

Many thanks.
[/COLOR][/COLOR][COLOR=Navy]
[/COLOR][INDENT]ubuntu@ubuntu:/media/cb68d86a-33d7-4a42-8a35-092f813858d7$ ls -al
total 104
drwxr-xr-x  23 root root  4096 2009-12-21 22:11 .
drwxr-xr-x   4 root root    80 2009-12-21 15:34 ..
drwxr-xr-x   2 root root  4096 2009-11-24 11:37 bin
drwxr-xr-x   3 root root  4096 2009-12-06 12:50 boot
lrwxrwxrwx   1 root root    11 2009-11-06 14:46 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2009-11-06 14:57 dev
drwxr-xr-x 140 root root 12288 2009-12-19 20:18 etc
drwxr-xr-x   4 root root  4096 2009-12-19 19:50 home
lrwxrwxrwx   1 root root    33 2009-12-06 12:50 initrd.img -> boot/initrd.img-2.6.31-16-generic
lrwxrwxrwx   1 root root    33 2009-11-24 11:40 initrd.img.old -> boot/initrd.img-2.6.31-15-generic
drwxr-xr-x  14 root root 12288 2009-12-19 19:19 lib
drwxr-xr-x   7 root root  4096 2009-11-06 15:51 lib32
lrwxrwxrwx   1 root root     4 2009-11-06 14:47 lib64 -> /lib
drwx------   2 root root  4096 2009-12-20 08:22 lost+found
drwxr-xr-x   3 root root  4096 2009-12-19 18:29 media
drwxr-xr-x   2 root root  4096 2009-10-20 01:18 mnt
drwxr-xr-x   3 root root  4096 2009-12-15 14:12 opt
drwxr-xr-x   2 root root  4096 2009-10-20 01:18 proc
drwx------  14 root root  4096 2009-12-08 18:24 root
drwxr-xr-x   2 root root  4096 2009-12-06 12:50 sbin
drwxr-xr-x   2 root root  4096 2009-10-20 00:48 selinux
drwxr-xr-x   2 root root  4096 2009-10-27 20:31 srv
drwxr-xr-x   2 root root  4096 2009-10-19 15:25 sys
drwxrwxrwt  21 root root  4096 2009-12-19 20:47 tmp
[COLOR=Navy]drwx------   4 root root  4096 2009-12-21 22:09 .Trash-0[/COLOR]
drwxr-xr-x  11 root root  4096 2009-11-06 15:51 usr
drwxr-xr-x  16 root root  4096 2009-11-24 16:12 var
lrwxrwxrwx   1 root root    30 2009-12-06 12:50 vmlinuz -> boot/vmlinuz-2.6.31-16-generic
lrwxrwxrwx   1 root root    30 2009-11-24 11:40 vmlinuz.old -> boot/vmlinuz-2.6.31-15-generic
ubuntu@ubuntu:/media/cb68d86a-33d7-4a42-8a35-092f813858d7$ 
[/INDENT]

---

### Post by Agris on 2009-12-21
[COLOR=Navy]@presence1960

I&#7743; really grateful.
[COLOR=black]I removed the .trash-0 directory and reboot. My ubuntu is back. Great!
I found your script really useful, so I posted a link to your instructions (thread
[[SOLVED reinstalling grub2?]]("http://ubuntuforums.org/showthread.php?t=1353062&highlight=file+directory+chroot%3A+run+command+%60%2Fbin%2Fbash%27%3A")[/COLOR][/COLOR][COLOR=Navy][COLOR=black]) in the forum of ubuntu.fr, in [this place]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3154784#p3154784").

Thanks everybody.
[/COLOR][/COLOR]

---

### Post by presence1960 on 2009-12-21
> **Agris said:**
> [COLOR=Navy]@presence1960

I&#7743; really grateful.
[COLOR=black]I removed the .trash-0 directory and reboot. My ubuntu is back. Great!
I found your script really useful, so I posted a link to your instructions (thread
[[SOLVED reinstalling grub2?]]("http://ubuntuforums.org/showthread.php?t=1353062&highlight=file+directory+chroot%3A+run+command+%60%2Fbin%2Fbash%27%3A")[/COLOR][/COLOR][COLOR=Navy][COLOR=black]) in the forum of ubuntu.fr, in [this place]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3154784#p3154784").

Thanks everybody.
[/COLOR][/COLOR]

Great. Glad you got it working. Actually the script is not mine. It was written by community member meierfra who keeps it on sourceforge for us to use. I have to give credit where it is due, the credit does not go to me even though I use the script quite extensively.

---

### Post by Agris on 2009-12-21
You're right. But don't worry, I've been careful about credits, [-> here]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3154784#p3154784").
Especially because a lot of people just copy/paste instructions from others sites, without reading the posts...

Happy solstice!
:)

> Bonjour.

Un script donnant des infos sur le boot que j'ai trouvé très utile.

Vu dans Re: reinstalling grub2?
[http://ubuntuforums.org/showthread.php? … bash%27%3A]("http://ubuntuforums.org/showthread.php?t=1353062&highlight=file+directory+chroot%3A+run+command+%60%2Fbin%2Fbash%27%3A")

Récupéré grâce à presence1960
Source:courtesy of community member meierfra
Info (from presence1960) :[INDENT]before you go installing and changing stuff let's get a clear idea of what you have now. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.
__________________
Boot Info Script courtesy of community member meierfra

My thoughts are images that I have made.

[/INDENT]Bonne soirée


---

