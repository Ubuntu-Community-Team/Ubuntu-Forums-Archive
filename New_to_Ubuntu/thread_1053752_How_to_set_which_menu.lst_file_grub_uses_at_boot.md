---
title: "How to set which menu.lst file grub uses at boot?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by bhold on 2009-01-29
I have 3 partitions - /dev/hda5, /dev/hda6, /dev/hda7. Each has a version of linux installed. Each has its own /boot directory and its own 
/boot/grub/menu.lst file.

It always seems that my most recent linux install - whichever partition that is on - determines the "active" partition from which the boot process obtains the menu.lst file.

Question - suppose grub is currently using the menu.lst file from /dev/hda6 at boot time, and I want to instead use the menu.lst from /dev/hda5. How do I accomplish this?

Related question - given my setup, instead of 3 menu.lst files would it be ok to have a menu.list file on one of the partitions and symbolic links from the other partitions?

---

### Post by kansasnoob on 2009-01-29
Well, that's fairly simple ........... but just know that not each menu list is going to show all operating systems!

Whether from a Live CD or any booted Ubuntu derivative you can just go to Terminal and type:

```
sudo grub
``` 

That will drop you into grub mode which will look like this:

>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 



You can then follow by typing (or using copy-n-paste):

```
find /boot/grub/stage1
```

That will ouput something like this:

> grub> find /boot/grub/stage1
 (hd0,4)
 (hd0,6)
 (hd0,8)



Obviously I could boot from either of three OS's, but only the latter will give me all three boot options .......... only in my case the latter is hosed, so I added a boot option for the last install to the one just prior to that.

Basically it goes like this:

> Boot up your live CD
In the desktop, open terminal (Applications -> Accessories -> Terminal).

sudo grub

This will set it to grub mode

find /boot/grub/stage1

This will locate your boot partition. If you already know the location, you can ignore this step.

root (hd0,0)

Replace the (hd0,0) by your boot partition number. If your Ubuntu is installed in the second partition, then change it to (hd0,1)

setup (hd0)
quit

Reboot your system. You should be able to access the Grub bootloader now.

Of course that's totally generic!

---

### Post by bhold on 2009-01-30
Did not work... here is what I did. (Grub currently takes menu.lst from /dev/sda6 at boot time,I am trying to get it to use the menu.lst on /dev/sda5.)

sudo grub

> root (hd0,4)
> setup (hd0,4)
> quit

Next, rebooted the system. I can tell from the options menu that menu.lst from /dev/sda6 is still being used.

Maybe syntax is wrong because my partition names are sda5, sda6... should I use (sd0,4) to specify partition in the grub commands?

---

### Post by kansasnoob on 2009-01-30
> **bhold said:**
> Did not work... here is what I did. (Grub currently takes menu.lst from /dev/sda6 at boot time,I am trying to get it to use the menu.lst on /dev/sda5.)

sudo grub

> root (hd0,4)
> setup (hd0,4)
> quit

Next, rebooted the system. I can tell from the options menu that menu.lst from /dev/sda6 is still being used.

Maybe syntax is wrong because my partition names are sda5, sda6... should I use (sd0,4) to specify partition in the grub commands?

setup is wrong! When you do "root" you set the drive and partition. hd0,4 = sda5

When you do "setup" you're only "setting up" the drive! Like  (hd0) which = sda.

So it should be:

> root (hd0,4)
> setup (hd0)
> quit

And the 0,s must be "zeros", not O's as in Oh!

That would setup sda5 to boot.

---

### Post by bhold on 2009-01-31
kansasnoob, that worked - thanks for clearing that up for me.

---

