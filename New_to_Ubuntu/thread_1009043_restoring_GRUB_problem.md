---
title: "restoring GRUB problem"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by fletcham on 2008-12-12
Hello,

I attempted to set up a dual boot last night by installing XP on a hard drive that already has Ubuntu. There was 25GB of unpartitioned space on the HDD which i installed XP on. Everything went fine until I restored GRUB. To restore GRUB i did the following:

1. Boot into ubuntu using the live CD
2. Open terminal and enter the code: 'sudo grub'
3. then i entered 'find /boot/grub/stage1' which showed (hd0,1)
4. then i entered 'root (hd0,1)'
5. then i entered 'setup (hd0)'
6. then i entered 'quit'
7. then i entered 'exit'

I thought this was it but when I restarted the computer it went into the GRUB menu and had about 11 different option to select. I tried to select every option and for each one I get the message - **'Error 17 - cannot mount selected partition'**. If i selected the ' other operating systems' option it says - **'Error 11 - cannot mount selected partition'**. This was so frustrating to happen at half three in the morning!!!

If i press 'e' on the options in Grub to edit the command it shows root (hd0,2). Shouldn't this say (hd0,1). Im stuck as to how to sort this out so any help would be very much appreciated. 

By the way im pretty hopeless on computer, but learning, so please keep it fairly simple.

Cheers everyone

Fletch:popcorn:

---

### Post by louieb on 2008-12-12
> **fletcham said:**
> ...it shows root (hd0,2). Shouldn't this say (hd0,1). 
Great that you got this far. Your close.  Highlight the root (hd0,2) line and press [B]e.

[/B]Edit the the line to root (hd0,1) press enter then press **b** to boot and see what it does

---

### Post by tomtom1982 on 2008-12-12
An other (and much easier way) to restore grub is to use the SuperGrubDisk.

There you only have to choose what you want to do and the supergrubdisk does it for you.

You can find the ISO-Image at

[http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/super_grub_disk_0.9689.iso](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/super_grub_disk_0.9689.iso)

---

### Post by fletcham on 2008-12-12
I

---

### Post by fletcham on 2008-12-12
I tried what louieb said to do and it booted up with no problems. Cheers louie!
What should i do now to permanently fix the pronlem?

Shall i use the super grub cd thing?

thanks again

Fletch:popcorn:

---

### Post by logos34 on 2008-12-12
gksudo gedit /boot/grub/menu.lst

change the 'root' line to match

---

### Post by fletcham on 2008-12-12
Sorted, i can now boot into ubuntu again. I cant boot into windows tho. The only option on the grub menu is other operating systems and if i select that it says - 'Error 11 - cannot mount selected partition'. 

What do i need to do now to be able to boot up windows?

Also, how do i remove some of the options from the grub menu. There are like 11 options to select. Can i not have it set up so I can either select ubuntu or XP. 

Cheers for all your help, I'd be screwed otherwise!

Fletch :popcorn:

---

### Post by Duck2006 on 2008-12-12
From the terminal

sudo fdisk -l

see what partition on then add these lines to your menu.lst

gksudo gedit /boot/grub/menu.lst

title windoze xp
root (hdx.y)    "the output of fdisk for where win is use hear."
chainloader +1

Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by fletcham on 2008-12-12
Thanks for that link Duck, all sorted now.

Nice one fellas!!!!

---

