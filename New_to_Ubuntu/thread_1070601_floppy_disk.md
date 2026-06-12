---
title: "floppy disk"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-02-15
I searched for info on floppy drives and found nothing.
I am using Ubuntu 8.10 and want to move a file that's on a floppy to somewhere in Ubuntu. How/can do I do this? Is there even a function in Ubuntu for Floppy use? I am also
confused as to where to put the file. Would I have to create it first in places/home?
I know that it can be done with a CD but for small files a floppy is so much quicker.

---

### Post by NewJack on 2009-02-15
I have an external USB HP Floppy Drive that is in my parts bin from my wife's old laptop setup.  When I plug it in and place a floppy in it, it takes about 30 or so seconds and it gets recognized as "1.5 MB Media".  I didn't do anything special in Intrepid to make it recognized.  I keep it around just in case a floppy pops up from somewhere in storage.

---

### Post by Jack Shankle on 2009-02-15
Thank you Newjack for replying.
I have an internal Floppy drive and it doesn't show up anywhere.
I looked under Computer and it's not there. The CD and HDs are there.
More Ubuntu stumbling blocks.

2% Ubuntu working in 3%

---

### Post by NewJack on 2009-02-15
Just found this post from the forums: [http://ubuntuforums.org/showthread.php?t=78986](http://ubuntuforums.org/showthread.php?t=78986)

Give a look through that and see if that helps.  It mentions an app called "pmount" that you may need to install.  I just checked and it is in Synaptic (v 0.9.17-2).  Also, in that thread there are mentions of maybe having to edit your fstab to get pmount to work.  I would try pmount without it first.

Good luck again!!

---

### Post by Elfy on 2009-02-15
I understood that floppy wasn't installed by default any longer and needs to be added to the loaded modules in /etc/modules

If you don't have floppy if you do

```
cat /etc/modules
```

Then try adding it in and rebooting

---

### Post by Jose Catre-Vandis on 2009-02-15
More simply, open a terminal and type:
```
sudo modprobe floppy
```
enter password and your floppy drive should spring to life. If you only need to do this occasionally then repaet the above command each time, otherwise add "floppy" to etc/modules as described by "forestpixie" above  :)

---

### Post by kansasnoob on 2009-02-15
Install fdutils either from synaptic or from terminal:

```
sudo apt-get install fdutils
```

Then open /etc/modules with the text editor in terminal:

```
sudo gedit /etc/modules
```

You'll see this:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

Below "lp" you want to add floppy so it looks like this:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
floppy

Then click on Save, then go to File > Quit.

And you'll have to restart!

---

### Post by Jack Shankle on 2009-02-15
Thank you very much Kansasnoob for your detailed instructions.
I restarted once and the floppy was still there.
I powered down once and the floppy was still there.
I thank you for instructions that leave nothing to the imagination.
It is necessary for guys like me. 
I now have a working Floppy drive.
One more question.
Is this problem going to be fixed by the Gurus? Reason I ask is that
I use Floppies for moving and saving very small files as it's much
faster than fooling with a floppy. I don't have a usb stick so I use 
floppies and CDs.

---

### Post by kansasnoob on 2009-02-15
> **Jack Shankle said:**
> Thank you very much Kansasnoob for your detailed instructions.
I restarted once and the floppy was still there.
I powered down once and the floppy was still there.
I thank you for instructions that leave nothing to the imagination.
It is necessary for guys like me. 
I now have a working Floppy drive.
One more question.
Is this problem going to be fixed by the Gurus? Reason I ask is that
I use Floppies for moving and saving very small files as it's much
faster than fooling with a floppy. I don't have a usb stick so I use 
floppies and CDs.

I think floppy technology is getting phased out. Like I still have old CD tapes tucked away from the Tandy years but have no way of reading them.

I did notice running the new Debian Lenny release today that it still supports Floppy so we'll definitely have a work-around for quite a while yet!

I still like being able to boot an older "dead" computer using Super Grub Disk on Floppy ............. but it's going away!

My guess is 2 to 3 years!

---

### Post by Kellemora on 2009-02-15
We never liked all the data loss with 3-1/2 floppies, so we used 5-1/4 floppies right up to this very year!

We have old single sided single density floppies that we used a paper punch to punch a hole in them so we could use both sides and STILL never lost data on a 5-1/4 floppy.

But 3-1/2's we usually had to make 4 or 5 of each, just so we KNEW we had at least one that would work.

As far as Ubuntu and using 3-1/2 floppies, I've NEVER been able to use them successfully.  Could read a few, but the standard formatting codes for Floppies is NOT a part of Ubuntu or anything you can add to Ubuntu.
And I think it only reads one file format to.  I don't remember now!

We keep a few DOZE machines around here in order to be able to use Ubuntu, it's almost like having the DOZE is a Dependency that Ubuntu requires for a lot of things!

TTUL
Gary

---

### Post by kansasnoob on 2009-02-15
> **Kellemora said:**
> We never liked all the data loss with 3-1/2 floppies, so we used 5-1/4 floppies right up to this very year!

We have old single sided single density floppies that we used a paper punch to punch a hole in them so we could use both sides and STILL never lost data on a 5-1/4 floppy.

But 3-1/2's we usually had to make 4 or 5 of each, just so we KNEW we had at least one that would work.

As far as Ubuntu and using 3-1/2 floppies, I've NEVER been able to use them successfully.  Could read a few, but the standard formatting codes for Floppies is NOT a part of Ubuntu or anything you can add to Ubuntu.
And I think it only reads one file format to.  I don't remember now!

We keep a few DOZE machines around here in order to be able to use Ubuntu, it's almost like having the DOZE is a Dependency that Ubuntu requires for a lot of things!

TTUL
Gary

"it's almost like having the DOZE is a Dependency that Ubuntu requires for a lot of things!"

Ouch! That's rough, but somewhat true. There are situations where any old Windows is needed if you have stuff that requires Windows.

I have an old PII with Win 98 (no internet) just because I have some old proprietary software for creating a family tree that won't even work on XP, let alone Ubuntu!

Hell, I have old photo files that can only be read in Ubuntu with xnview and while it's good it's far from perfect!

And it does come down to: when am I going to convert all of this?

It's like asking when someone is going to convert all of their 8 track tapes to digital. Or what am I going to do with those old Beta movies?

Some stuff gets lost! I have old WWI and WWII images; photos and postcards that are deteriorating, and I can scan them but eventually the original dies!

---

