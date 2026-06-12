---
title: "Ubuntu won't boot"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by purplequark on 2011-02-09
I activated my ATI driver and now Ubuntu won't boot.  Just goes to a black screen. I've installed another copy of Karmic beside my (previously) working one and I can see all of my files are there but can't get Ubuntu to load into the right copy.  Guessing that I'm screwed - can't find anything comparable to a Windows Restore in Ubuntu.

---

### Post by robsoles on 2011-02-09
Welcome to UF!

Using LiveCD or your other install find the /etc/X11 directory of the partition containing the copy of Ubuntu you can't boot into right now and delete xorg.conf from it - try booting into the broken copy of Ubuntu again and let us know how that goes.




Please consider using 10.04 if you simply must have long term support. Please consider trying 10.10 or 11.04 if you want to have a snazzier experience.

---

### Post by purplequark on 2011-02-10
Thanks for the reply.  I found the file but can't delete it - says I'm not the owner and can't change permissions.  Kind of thought that sounded too easy :P

Using this distro because my wireless adapter doesn't work with the upgrade.



um nevermind ... used nautilus to change password, deleted file, rebooting now.

back to black screen ugg....

---

### Post by purplequark on 2011-02-10
Rebooted again and I can now state with full certainty that you, Robsoles, are a god.  Thank-you.

---

### Post by robsoles on 2011-02-10
Very welcome, glad to hear it worked! Thanks for the high praise, I at least try not to be the devil :p

I hope you find an upgrade path soon, 10.10 is great and 11.04 is looking pretty darn good too - maybe you can try the latest one in your 'other partition you put another copy of Karmic in' till they correct the problem it sounds like they might have introduced for your wifi card in 10.04(?)

Please consider marking your thread solved.

---

### Post by purplequark on 2011-02-10
I just ran the upgrade on that extra install and no luck with the wireless.  Doesn't even see that I have a wireless adapter.

Now I just need to find out how to remove the extra ubuntu installs that I have so I'm back to just the working one....  Amazed at how easily I messed the OS up...

---

### Post by robsoles on 2011-02-10
Don't just follow this advice, please google and research it a bit at least:

Use 'disk utility' to re-write the partitions with the 'failed' OSes to whatever file-system you would prefer them to be and then```
sudo grub-udpate
```*should* reset your operating systems menu on bootup to only have the last remaining OS listed.

I am at work with no time right now to double check my advice so I beg you to Google it at least a bit and check for information to back my advice up before applying it.

---

### Post by purplequark on 2011-02-23
So I did some research and thought I'd worked it out, extra partitions gone.  Rebooted machine and now it goes to error 'partition not found'
grub rescue>
-------------------
Should have left it alone.  Machine won't even load from my live cd anymore, goes straight to grub rescue...  Will boot from windows cd but I don't have windows installed anymore so running the cd will format the entire machine.  Guessing that I've lost everything now.... live and learn.

---

### Post by wilee-nilee on 2011-02-23
> **purplequark said:**
> So I did some research and thought I'd worked it out, extra partitions gone.  Rebooted machine and now it goes to error 'partition not found'
grub rescue>
-------------------
Should have left it alone.  Machine won't even load from my live cd anymore, goes straight to grub rescue...  Will boot from windows cd but I don't have windows installed anymore so running the cd will format the entire machine.  Guessing that I've lost everything now.... live and learn.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by robsoles on 2011-02-23
> **purplequark said:**
> So I did some research and thought I'd worked it out, extra partitions gone.  Rebooted machine and now it goes to error 'partition not found'
grub rescue>
-------------------
Should have left it alone.  Machine won't even load from my live cd anymore, goes straight to grub rescue...  Will boot from windows cd but I don't have windows installed anymore so running the cd will format the entire machine.  Guessing that I've lost everything now.... live and learn.

Where you say it also goes to the 'grub rescue' prompt from the LiveCD makes me think your BIOS is not set to try booting from your CD/DVD drive anymore - please check your BIOS settings till you can boot off the optical drive and then follow wilee-nilee's advice regarding the boot script; one of us should have you 'back on' shortly after a squiz at the output of that...

---

### Post by purplequark on 2011-02-23
Yeah double checked, I even had my hd disabled so the only boot choices are from cd and my linux boot cd doesn't load.  Gets a windows error saying to insert correct disk and hit enter.... When I set it to boot first from cd and then to hdd, the cd spins but then it stops and it goes to the grub rescue prompt.

---

### Post by purplequark on 2011-02-23
Started a new thread  [http://ubuntuforums.org/showthread.php?p=10488742#post10488742](http://ubuntuforums.org/showthread.php?p=10488742#post10488742)

---

### Post by purplequark on 2011-02-24
> **robsoles said:**
> Where you say it also goes to the 'grub rescue' prompt from the LiveCD makes me think your BIOS is not set to try booting from your CD/DVD drive anymore - please check your BIOS settings till you can boot off the optical drive and then follow wilee-nilee's advice regarding the boot script; one of us should have you 'back on' shortly after a squiz at the output of that...
It sees that there's a disk in it but it can't read it, I know the cd works.  Says 'DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER'  Again, if I put a windows cd in it, it will run.  Even tried booting it from the ISO that I used for my netbook, on usb, still won't go.  Isn't there a grub command that I can use to get it to boot?

---

### Post by robsoles on 2011-02-24
it's rather painful that you cannot boot from an Ubuntu LiveCD ISO because it's the first step in the way(s) I know how to re-write the grub bits required to boot a system...

Might it be that the Windows CD you are playing with is 'from the shops' and you burnt the Ubuntu CD yourself? Perhaps the 'burn' of the Ubuntu CD isn't as good and lovely as it could be and the drive in the machine in question is 'going blind'? Of course, that shouldn't stop you booting from a USB stick.

Can you use unetbootin (in Windows **on another PC**) or Startup Disk Creator (in Ubuntu **on another PC**) to make a bootable USB of Ubuntu 10.XX LiveCD to try?

---

### Post by purplequark on 2011-02-24
Yes, the liveCD is one that I made but I tried it on another machine and it works.  Messed with my machine for a few hours then gave up, ended up formatting it and reinstalling windows.  Will reinstall linux later.  I know, I'm not a very patient girl :) anyway needed a fresh start I guess.  Thanks for all the help though :)

---

