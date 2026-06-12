---
title: "Auto mount cd when it is inserted"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-09-28
Hi all,
    
     I'm using Ubuntu 8.04 LTS and kernel version 2.6.24-24-generic. I want to auto mount CD as soon as when it is inserted to Cdrom. How can I do this?. If I make /etc/fstab entry to 'auto'. I need to restart the computer to mount. I want to  auto mount the cd as soon as it is inserted without typing "mount /dev/cdrom". Please anyone help me on this...

---

### Post by realzippy on 2009-09-28
sudo hal-disable-polling --enable-polling  --device /dev/cdrom

---

### Post by jimingkui on 2009-09-28
When you insert a CD into CD-rom,does it not automounted?
I will see an icon on desktop when I insert a CD and see where it is mounted to by typing command:**mount** in terminal.

---

### Post by t0p on 2009-09-28
My cd drive automatically mounts when I insert a cd.  My /etc/fstab file looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=859e2180-bf64-42af-bb88-8ebc511b9ae0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ab85239b-e82c-4f53-894f-dc9582718d40 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Is that of any help?

---

### Post by wojox on 2009-09-28
You could also run:

$gconf-editor

Go to apps > nautilus > preferences
see if "media_automount" option is checked.

---

### Post by vipin.balakrishnan on 2009-09-28
Hi,

   When I insert CD .It is not showing any shortcut in  my Desktop. My /etc/fstab entry is given below. Please anyone help me on this..

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fd2acb7c-8497-4350-91f7-026a9df71069 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=c576e07b-9442-4ccc-8f67-faa6a79bffc8 /boot           ext3    relatime        0       2
# /dev/sda4
UUID=7237c46e-8127-4bca-b690-3e7943f96262 /home           ext3    relatime        0       2
# /dev/sda3
UUID=10bad994-f01b-459b-aed6-3bfd94c6248b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,cdfs,iso9660 user,auto,exec,utf8 0       0

---

### Post by t0p on 2009-09-28
Go to a Nautilus (file manager) window - such as the window that you get when you click on somewhere in Places.  Go to Edit > Preferences > Media, and tick the box for Browse media when inserted.

That may solve your problem.

---

### Post by vipin.balakrishnan on 2009-09-28
Hi,
   
    I checked that this will work only for blank disc. If I can get a shortcut of cd in desktop as soon as insert that also enough for me.

---

### Post by vipin.balakrishnan on 2009-09-29
Hi all,

   At last i found a solutions for my problem
Goto System -> Adminstration -> Users and Groups . Add the current user to haldaemon. Provided auto should be given for cdrom in /etc/fstab

---

