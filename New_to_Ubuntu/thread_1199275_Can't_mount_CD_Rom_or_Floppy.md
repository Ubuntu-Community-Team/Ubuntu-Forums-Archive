---
title: "Can't mount CD Rom or Floppy"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by jivabill on 2009-06-28
All used to work fine.  Running 8.04

When I insert a floppy and try to read it the drive works awhile and a message box comes up says "unable to mount the volume".  When I click on "details" says that mount point /media/floppy0 does not exist.  It does exist however in root file browser it shows up in my Home directory:  /home/media/floppy0.  

Same problem happens with a CD

Interestingly when I try to format a floppy that works and I can do the format.


Both the CD and the Floppy were working just fine couple months ago.  What is going on???

Any ideas, this is pretty frustrating...
thanks

---

### Post by [adult swim] on 2009-06-28
try running ```
sudo modprobe floppy
``` and then see if your floppy drive works

what does ```
cat /etc/fstab
``` return?

---

### Post by egalvan on 2009-06-28
> **jivabill said:**
>   When I click on "details" says that mount point /media/floppy0 does not exist.
It does exist, however in root file browser it shows up in my Home directory:  **/home/media/floppy0.**  


Any ideas, this is pretty frustrating...
thanks

it's not supposed to be [COLOR="Red"]/home[/COLOR]/media/floppy0
this is not the correct mount point, *unless you specify it as such.*
otherwise, the system looks in** /mnt** and **/media** for these devices.

it's supposed to be /media/floppy0

so no, it does not exist. these are two different directories.


give us the info that [adult swim] asked for.
it will give us something to work with.

---

### Post by jivabill on 2009-06-29
Thank you Adult Swim and Egalvan for your suggestions.  

I got it to work after some pondering I fired up one of my laptops that has the same version (8.04) of Ubuntu on it and looked at the file system.  AND on the laptop the Media folder was not in the Home directory, it was where it is supposed to be.  So I concluded I should move it.  

Got into Root File Browser and moved the Media folder out of the Home directory.  Now the floppy and CD both mount and work correctly.  So I think I have solved my original problem.  I have not the faintest idea how the Media folder got inside of the Home directory.  I don't spend much time fiddling around with the File System.  I do have to say that this machine, a Compaq, has given me quite a bit of grief and at one point I had to just re install Ubuntu to overcome a problem.

Here is the output of cat /etc/fstab

gojollybill@CompaqBox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0d801fe5-41d8-400a-833b-bf91eac47c00 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=779dfe26-4420-4395-af26-77f62118c3df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
gojollybill@CompaqBox:~$ 

Looks to me, and I am not an expert, like the floppy is set up right.  And the CDRom also.  At least it looks the same as the cat /etc/fstab output on the laptop.
Thanks again
bill

---

### Post by jivabill on 2009-06-29
Looks like the problem is now solved per my last post moving Media folder.

Thanks again to all for the good help

bill

---

