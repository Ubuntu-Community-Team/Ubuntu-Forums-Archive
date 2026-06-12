---
title: "gathering ideas for uninstalling Ubu from usb drive"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by psanscarti01 on 2011-01-30
Ubuntu will not uninstall from my flash drive.  I've posted this, and the responses I've received are too technical to follow, or too presumptive and lack some detail which hinders my follow through.

Par example:

"you can install a linux bootloader called lilo, from a live Ubuntu cd booted; to restore the MS boot."
What does this mean?

I downloaded "lilo", unzipped it, and there appears to be no executable file.  What does 'live' mean?  What does 'from a live Ubuntu cd booted' mean?  Does it mean to put the unzipped files onto a cd/dvd then boot my system from this...cause that did not work. 

Please answer in simple terms.  I trusted this Ubuntu to install and uninstall easily, now I'm left holding the bag. If one needs to be a technogeek to use it, please warn newbies to stay away.

I shouldn't be cross with people trying to be helpful, but geez louise, what good are suggestions that i don't understand? What good is a free excellent operating if it holds my computer hostage like that unfree crummy operating system does?

Thank you

---

### Post by Matt__ on 2011-01-30
format the drive (assuming your using windows)

insert USB, right click and FORMAT. (check quick format and leave all other options as default)

a 'live' cd is one that runs only in RAM from a cd or usb drive...its what you should have used to try ubuntu BEFORE installing it anywhere.

have you installed Ubuntu on your hard drive or just the USB?
/edit never mind I've read your other posti suggest you follow this as posted before.
> **wilee-nilee said:**
> You can install a linux bootloader called lilo, from a live Ubuntu cd booted; to restore the MS boot.[COLOR="Blue"](boot using ubuntu on a usb/cd and select "try ubuntu without making changes")[/COLOR]

Restore basic windows boot loader - universe enabled([COLOR="Navy"]enable universe repository from "software sources")[/COLOR]
sudo apt-get install lilo[COLOR="navy"](command to type into terminal(like a dos box))[/COLOR]
sudo lilo -M /dev/sda mbr[COLOR="navy"](another terminal command)[/COLOR]
May show error messages about the rest of lilo missing, ignore, we just want MBR

These commands would be if your HD is sda[COLOR="navy"](this is the hard drive designation/name instead of window C: etc)[/COLOR], if the HD is another adjust accordingly. You sound as though you can't boot XP on its own, this will reload a bootloader that will.

:P

---

### Post by C.S.Cameron on 2011-01-30
Have you tried formatting the flash drive?
If there is only one partition you can do it in Windows. Right click on it in Explorer and select format, use FAT32.
If the flash drive is multi partition, you should format using gparted from the Live CD, choose FAT32.

---

### Post by uRock on 2011-01-30
You need to install Lilo using a LiveCD with an internet connection.

Here are the steps I followed for installing Lilo in the past.
> **presence1960 said:**
> You can repair the MBR to a windows MBR from  ubuntu or the ubuntu live CD. Install lilo by running in terminal  ```
sudo apt-get install lilo
```Ignore the warning and next run in  terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your  disk/device, i.e. sda, sdb,sdc, etc

---

### Post by arpanaut on 2011-01-30
Have you had a look here:  [http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread](http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread)

It is well written and addresses many issues dealing with wubi installs.
You will have to repair the win bootloader,  and that is covered in there.

---

### Post by HermanAB on 2011-01-30
Howdy,

Looking at the comments above, I can feel your pain...

You need to format the flash disk.  The easiest way to do that is using a Windows machine, as suggested above.

You can also format the disk using a Linux machine of course:
Insert the flash disk

Look at the kernel messages to get the exact name of the disk (it depends on how many hard disks you got):
$ dmesg
for example /dev/sdb and a primary partition /dev/sdb1

Now format the drive using mkfs:
$ sudo mkfs.vfat /dev/sdb1

Now unplug and plug it again and it should automount under /media.

---

### Post by psanscarti01 on 2011-01-30
Thanks to the 9(both posts) who have come to my aid.  Your effort is gratifying to me.  Like a stranger stoppingto  help a person with a flat tire, your kindness is appreciated.

I will implement one or more of your solutions, and report back soon.  Again, although it was a new operating system I was messin' with, the lure of simplicity triggered a go.  I thought I was being prudent enough by dedicating a flash drive to Ubuntu, but that backfired for the uninstall process.

My goal is to install the Ubuntu OS on my second drive.

Thanks again

---

### Post by psanscarti01 on 2011-01-31
Thanx to all but specifically to wilee-nilee and matt__.  The instructions worked, though it took much searching around for the elements needed to get to the next step.  So Ubuntu is my friend if I know where to find the apps and commands. 

Now I would like to install Ubuntu on my second drive.  I have two drives, one is IDE and the other SATA.  The SATA is 230GB and should make a nice home for Ubuntu.

Will anyone, particularly those who posted suggestions even read this post?

Thanks again

---

### Post by Matt__ on 2011-01-31
> **psanscarti01 said:**
> 
Will anyone, particularly those who posted suggestions even read this post?



sure they will :D

have fun with Ubuntu...all those thousands of pieces of software to play with, no virusses, no crashing, no defraging and one huge family to help if anything goes wrong.



[COLOR="White"].[/COLOR]

---

