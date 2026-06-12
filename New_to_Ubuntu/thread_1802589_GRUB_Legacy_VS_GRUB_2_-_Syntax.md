---
title: "GRUB Legacy V/S GRUB 2 - Syntax"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by avnd on 2011-07-12
Hello!

I have installed Chromium OS along with my Ubuntu today following instructions at the following website.
[http://chromeos.hexxeh.net/wiki/doku.php?id=multiboot]("http://chromeos.hexxeh.net/wiki/doku.php?id=multiboot")
The problem is that the author has given help regarding altering the Grub 2 menu list to be able to boot into Chromium. But I have configured my system in such a way that I have a Grub Legacy residing in a separate boot partition through which I boot into various OS's. I have my system configured with help from the instructions at the following page.
[http://ubuntuguide.org/wiki/Multiple_OS_Installation]("http://ubuntuguide.org/wiki/Multiple_OS_Installation")
Now I need help in altering the changes the author has given for Grub 2 so I could introduce them in my Grub Legacy so that I am able to boot into both Ubuntu and Chromium.

I tried comparing the previous entries in Grub Legacy and tried some adaptations. But as I'm a tech newbie, I'm having trouble with it.
[noparse]
The lines given by the author of the guide are the following.

menuentry "ChromiumOS" {
	insmod ext2
	set root=(hd0,x)
	linux   /boot/vmlinuz root=LABEL=C-ROOT rw noresume noswap i915.modeset=1 loglevel=1 quiet
	initrd  /boot/initrd.img
}

I have my C-ROOT in /dev/sda9 and my C-STATE in /dev/sda8.
So, I substituted (hd0,x) with (hd0,8).
Trying to adapt, I tried the following code.

title Chromium
root  (hd0,8)
kernel /boot/vmlinuz root=/dev/sda9 ro (I tried rw istead of also here)
initrd /boot/initrd.img

But I get an error when I choose 'Chromium' in my Grub menu saying, "File missing" or something like that. I'm not exactly sure of the exact words of the message.

Can anyone help me out here?
Thanks!
Cheers! :)
[/noparse]
The smileys are actually (hd0,eight) :)

---

### Post by grahammechanical on 2011-07-12
Hi

It is more than a year since I messed around with Grub menu.lst. I no longer have a copy on my machine. so, forgive me if I am stating the obvious.

You are copying information about Grub 2 into legacy Grub. Are you phrasing things in the legacy Grub style? Are you use the right syntax?

My second point is this, why are you editing Grub at all. From the guide that you are using I see that you only put that information into a Grub file if you are using Grub 2. Then you edit the 40_custom file. 

For legacy Grub, as seen under the heading Grub (pre Karmic Koala) the guide says this,

> Once your machine partitions are updated, remove all USB keys. Run the following command 

The command is > sudo update-grub

It seems to me that that is all you need to do. The update Grub command would search for the new OS and make the changes to the Grub menu.lst. 

This is how I understand the instructions. I am sorry if this does not help.

Regards.

---

### Post by avnd on 2011-07-12
Thanks for your reply, Grahammechanical.

Forgive me if I'm sounding stupid and missing some very obvious point here. I'm a newbie. I've been using Windows for years, but it is only 2 months since I installed any operating system (including Windows) on my own. 

Following the Ubuntuguide wiki, I now have a set of Grub configuration files in the separate boot partition. Now, my MBR points to that boot partition which has the menu file I want. I'm still not clear as to where the Grub Legacy itself actually is (the MBR or the Boot partition).  

From what I can understand, I used to mount the menu.lst file that resides on the boot partition to some folder everytime I install a new OS (yes, I have installed 3 or 4 distros in 2 months even though I'm not a techie just for the heck of it :) ) and add an entry that chainloads the bootloader of that specific distro which I install only in the specific partition where the OS resides.  

Now with this Chromium OS, I don't exactly have any bootloader in the partition which I could just chainload from Grub Legacy (it would've been easy). So, I assume I have to manually point it to the booting files or whatever they are (which is where adding the entry specified in Hexxeh's website comes into the picture).

With regard to updating Grub, I don't exactly understand where I'm supposed to do it from. Grub now is on a separate partition without being associated directly with any OS (that was the whole point of me installing it in a separate partition, so that I could delete any one of the multiple OS's without disturbing the others). 

So, which distro's terminal am I supposed to run the update from. If I indeed do that, how do I point that to the boot partition. And if I update it, it should go to Grub 2, which I do not want (I actually don't mind the update if it would retain all the current menu entries exactly as it is. But I don't know for sure about it).

I hope I conveyed my views clearly without confusion. Please do correct me if I have understood something wrong. I'm still on the steeper part of the learning curve. :)

Cheers! :)

---

