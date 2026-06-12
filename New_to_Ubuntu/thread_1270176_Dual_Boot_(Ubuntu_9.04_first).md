---
title: "Dual Boot (Ubuntu 9.04 first)"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by al.adab on 2009-09-19
hi 

I'm trying to set up a dual-boot on my machine. Ubuntu 9.04 is already installed and I'd like to create a 2nd partition to install Vista on it. 

This is what I've done: 

1) through the Ubuntu Live CD, I resized /DEV/SDA1 (right to left) and allocated around 10GB for Vista; 
2) I re-booted the machine with the Vista CD, chose (installation type) "CUSTOM"; 
3) a list of three options appeared: the one in the middle is called "DISK 0 UNALLOCATED SPACE". I selected it and clicked NEXT, but was told  I can't proceed from here; 
4) I then pressed SHIFT + F10 and typed in the following:

---

### Post by slibuntu on 2009-09-19
If you do succeed in installing Vista, you will not be able to boot Ubuntu, Vista will overwrite GRUB and the MBR. You will need to restore GRUB somehow. 

What is the error message you are getting when trying to install Vista?

---

### Post by mapes12 on 2009-09-19
Have a look at this:

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by al.adab on 2009-09-20
Apologies - I can't figure out how I manage to publish this unfinished. Anyway, in the meantime I found the following

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

and realised the reason I was having troubles was that I hadn't named NTFS the partition created through the Partition Editor at the Live CD. 

I didn't carry on though, as the part that "Vista will overwrite GRUB and the MBR. You will need to restore GRUB somehow" kind of worried me. At the link above the writer seems to have a solution, which I haven't tried out. 

Would be great if anyone did try it out and knew about risks, etc. I keep coming across threads about people having troubles with dual-boot, and I just don't need that right now. The only reason for having a dual-boot is that I occasionally need to use Sonicstage...

---

### Post by mapes12 on 2009-09-20
> The only reason for having a dual-boot is that I occasionally need to use Sonicstage...Then you could try to use that application through [WINE]("http://ubuntuforums.org/showthread.php?t=885111").

---

### Post by al.adab on 2009-09-21
Been there :) not even Wine can cope with Sonicstage...(unless miracles do happen). Really no-one has tried out the dual-boot Ubuntu/Vista - Ubuntu installed first?

---

