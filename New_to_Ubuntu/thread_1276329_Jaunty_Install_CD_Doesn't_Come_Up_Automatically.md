---
title: "Jaunty Install CD Doesn't Come Up Automatically?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-09-26
I want to install 9.04 over what is currently 8.04, but when I restarted my computer to do the installation, the install screen didn't come up as expected.  Instead, 8.04 just booted normally.  I dual boot Vista and 8.04, so I decided to see if it would work when I went into Vista, but Vista, too, booted normally.  Did my disk burn incorrectly, or is there something special I need to do since I'm dual booting?

Just to clarify, I want to install Jaunty over Hardy and keep Vista.

---

### Post by SteelCore on 2009-09-26
The installation cd should start before you access Vista or 8.04.  You probably need to make sure that the boot sequence is correct with 'boot from cd' at the top of the list.

---

### Post by powel212 on 2009-09-26
After you reboot and the computer goes down, the screen goes black and then the computer "BEEPS" once. Hit "delete" to enter bios. Check to make sure first boot device is "CD" or "DVD".

Alternatively you could upgrade from within Ubuntu 8.04

in a terminal type 

```
sudo do-release-upgrade
```

I hope that helps.

Powel

---

### Post by Wataru8675 on 2009-09-26
> **powel212 said:**
> After you reboot and the computer goes down, the screen goes black and then the computer "BEEPS" once. Hit "delete" to enter bios. Check to make sure first boot device is "CD" or "DVD".

Alternatively you could upgrade from within Ubuntu 8.04

in a terminal type 

```
sudo do-release-upgrade
```I hope that helps.

Powel

...no new release found!?!?!?  I knew something was shaky with my...whatever it's called where Ubuntu gets it's info from the Internet. -_-  Thanks for the terminal tip, but it looks like I'm stuck with the CD for now.

---

### Post by wildman4god on 2009-09-26
You need to get into your computers bios and change the boot order to allow cd drive before hard disk. To get into your bios you need to watch as your computer comes on the first screen (called post) will say which key to press to bring up the bios, it varies from pc to pc but is usually F2, DEL, or F12, your computer may also have a quick boot select option, which lets you select the boot device for that one time, the post screen should also tell you this, if it doesn't check the manual.

---

### Post by Wataru8675 on 2009-09-26
Alright, so I'm into the installation of 9.04 now, but I can't figure out how to make it completely overwrite 8.04 AND JUST 8.04.  I have the options to either run my OS'es side by side, but that doesn't remove 8.04, install 9.04 over everything, which I don't want, and to specify the partitions manually.  I went to Specify Manually and I don't understand what to do in here.  It looks like I can name a partition size, but how can I specify where I want Jaunty to be installed to?

---

### Post by peculiar penguin on 2009-09-27
Choose the "Manual" option and you'll get a list of partitions found on the disk. Identify which one belongs to Ubuntu, select it and click "Edit partition". Leave the size as-is, in the "Use as" dropdown select a file system (ext3 would be the default recommendation), tick the "Format the partition" checkbox, and select the appropriate mount point (e.g. "/" for the main/root partition). If you have a setup with multiple partitions (e.g. separate ones for /var, /home, or whatever) then repeat as needed, just make sure you select the right mount point each time and stay away from your Windows partitions (these should say "ntfs" in the type column).

---

### Post by Wataru8675 on 2009-09-27
About the multiple partitions, I have no idea if I do or not......if I installed Ubuntu straight from the CD over everything doing all the default options, what would I have?

---

### Post by Wataru8675 on 2009-09-27
And also, my current installation of 8.04 doesn't have a mount point listed......should I just leave it blank, then?  None of the other OS partitions have mount points either...

---

### Post by peculiar penguin on 2009-09-27
That's deliberate, it won't touch any partition unless you explicitly tell it to do so.

Can you take a screenshot of the partition list? Or post the output of "sudo fdisk -l"?

---

### Post by wildman4god on 2009-09-27
Yeah, When you try to uninstall an os from a multiboot system and/or replace it with another os is where things get fun, Do what the guys above said and also since your not use to doing this back up your data from all partitions (not system or os files just the ones you use or create that can't be replaced). Also is ubuntu 8.04 the only os on your drive or do you also have windows?

---

