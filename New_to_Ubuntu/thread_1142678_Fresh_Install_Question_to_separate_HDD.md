---
title: "Fresh Install Question to separate HDD"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by gwmbox on 2009-04-29
I initially installed ubuntu after windows and thus had an install and unintall in windows, however I have now attached a third physical drive.  So now I have C: (Windows system 400GB) D: (My data/documents 1000GB) and now E (NTFS volume empty 400GB).

I want to install ubuntu as a fresh install to the current E Drive so that E drive becomes a linux only drive.  I however need to have a dual boot option, at least for now and need to know how I go about this without it affecting my existing C and D drives.

Is this just a case of insert the CD and tell it to install to E:?  How do I set it up to have the boot choice menu?

Cheers for the easy steps please :)

---

### Post by adw on 2009-04-29
Hi!
Have a look over here
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
I think your best bet is to set the Ubuntu drive as Master and Windows as slave, and then edit Grub on the Ubuntu drive to mirror your drive settings.
[http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)
Good luck:)

---

### Post by kansasnoob on 2009-04-29
Multiple drive set-ups are not simple!

This guide should be helpful:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I prefer a method somewhat like this:

[http://mywebsite.bigpond.net.au/dfelderh/p22.html](http://mywebsite.bigpond.net.au/dfelderh/p22.html)

That way I know what the drive layout is like using Gparted without making any changes before continuing any further. But that involves only one drive.

The following guide describes a multi-drive set-up but it uses the text installer which I don't recommend:

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

There's a lot you need to understand. I'd begin by physically installing the drive and then (after checking to see that you can still boot into Windows) boot the Ubuntu Live CD, check for defects, then run it without making any changes, and go to Gparted (aka: partition editor) just to identify how Ubuntu sees your new drive structure.

You'll see in the upper right hand corner you can toggle thru the various drives:

[ATTACH]111682[/ATTACH]

I'd make no changes at that point but rather come back here with some more info:

#1. While you're running the live CD go to terminal and run the command:

```
sudo fdisk -l
```

BTW, that's a lower case L.

Then post that full output here. That'll give us some idea where we should tell you to install Ubuntu.

#2. What version of Windows are you running? We'll need to decide what bootloader to use and make some plans on how to set that up.

Just be patient, plan ahead, and only when you're sure you know what you're doing proceed!

---

