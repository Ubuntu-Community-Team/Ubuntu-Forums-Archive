---
title: "install from different partition"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Garthhh on 2010-07-01
link to the instruction set I am trying to follow
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
the iso is in the download file
assuming the 1st 2 lines are right  the procedure looks something like this

Code
mkdir /tmp/install_cd
 mkdir /tmp/installer

the next 2 lines are modified as I would read the directions 



sudo mount disk-image.kubuntu-10.04-desktop-i386.iso -o loop /tmp/install_cd
sudo mount /dev/sda /tmp/installer

problem is I get an error of no such directory
this note book has no CD/DVD & the broken one isn't plugged in
the iso is from a torrent & sitting in download directory
Do I need to move the iso or modify the command

---

### Post by varunendra on 2010-07-01
> **Garthhh said:**
> 
sudo mount [COLOR=Red]**disk-image**[/COLOR].kubuntu-10.04-desktop-i386.iso -o loop /tmp/install_cd
sudo mount /dev/**[COLOR=Red]sda[/COLOR]** /tmp/installer

The error should be occurring after both commands. In the linked tutorial, when it says "disk-image.iso", it means you have to replace it with the full path of 'your' iso image file.
It seems that the name of the iso file in your case is **kubuntu-10.04-desktop-i386.iso **which is sitting in the 'Downloads' folder. So the command for the first line would be
```
sudo mount **~/Downloads/kubuntu-10.04-desktop-i386.iso** -o loop /tmp/install_cd
```

Then in the next line, you've tried to mount a whole hard-disk (sda) while it should have been a partition of that hard-disk (e.g.- sda1). So it would be-
```
sudo mount /dev/[COLOR=Black]**sda1 **[/COLOR]/tmp/installer
```

Correct it as above & you should be able to go ahead.

---

### Post by Garthhh on 2010-07-01
thanks 
I'm getting closer

I'm on the part where I modify grub2, which must be correct as it is the instruction set that matches what I find exactly in my files
i'm at 
ect//grub.d/40 custom  
as directed
my problem is when gedit opens, it is read only. I  can't change permissions as the owner is root
here are the directions I'm trying to follow


With Grub2, the bootloader in new installations of  9.10, the procedure is a little different. You should edit the file /etc/grub.d/40_custom  and add the lines 

menuentry "installer" {
        insmod ext2
        set root=(hd0,1)
        linux /casper/vmlinuz boot=casper root=/dev/ram1 ramdisk_size=1048576 rw
        initrd /casper/initrd.lz
}

---

### Post by VastOne on 2010-07-01
```
ect//grub.d/40 custom 
```

must be 

```
sudo gedit /etc/grub.d/40_custom 
```

---

