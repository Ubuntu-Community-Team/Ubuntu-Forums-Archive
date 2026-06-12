---
title: "Finished with Wubi, going to try and install on a partition"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-11-28
Okay, I'm on an acer netbook and have no CD drive, so what software can I use to create a partition on my HDD?  I currently have Windows Vista installed.  Basically, I'd like a step by step walkthrough on how to create a partition and then install ubuntu on it (from a live CD via usb drive).  

Also, when I tried installing with wubi, grub wouldn't work and I would just be left with a black screen and command prompt.  Will this happen again when I install on a partition?  If so, will I be able to access Windows again?  Thanks in advance.

---

### Post by Temposs on 2009-11-28
You should use the UNetbootin program to create a bootable USB drive:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Then set your BIOS to boot from the USB drive before the hard drive, and you'll be able to test drive Ubuntu through its LiveCD functionality. If it works well enough, then go ahead and install.

---

### Post by Space-Wolf on 2009-11-28
Okay, but how do I go about creating a partition without messing with my Windows files?

---

### Post by Temposs on 2009-11-28
During the Ubuntu installation, it will give you the option to install Ubuntu side-by-side with another OS that's already installed. You just choose that option, and it will create a partition for Ubuntu and leave your Windows install completely untouched :-)

---

### Post by oldfred on 2009-11-28
With different versions of windows & Ubuntu the screens may change somewhat but the process is the same. Some examples with some updated:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by jrrader on 2009-11-28
Or

Go to the start menu in Vista and search for "partition".  The Windows partition editor will allow you to safely resize your partition and add another partition for Ubuntu while Windows is running.  Doing this through Windows rather than with Gparted will keep the files in your Windows partition safe.  You might also want to properly degfrag your drive before doing this.  I know vista defrags all the time, but the software windows gives you for defragging is really weak.  [www.piriform.com/defraggler]("http://www.piriform.com/defraggler") will do a much better job.

---

### Post by Space-Wolf on 2009-11-28
Okay so I don't even have to use GParted or anything?  And will grub actually work properly this time or is it gonna give me the same crap as last time?

---

### Post by jrrader on 2009-11-28
I made a typo in my last post.  I meant that the Vista partitioner will work while vista is running, not while Ubuntu is running.  But yeah, Wubi and a real install are completely different.   Because you're installing next to Vista you might get an error that says "auto-chk not found" when you try to boot into vista.  Doesn't always happen, but it's fairly common.  There are a number of ways to fix this (easiest being to pull out the hdd and put it into another computer and then boot up- I just said that in another post... but it tends to work for windows boot errors.) But grub will be able to find Vista, even if vista refuses to load.

---

### Post by Space-Wolf on 2009-11-28
Okay.  And I just realized, I forgot to uninstall Wubi before I started using the Ubuntu installer, but that won't mess anything up will it?

---

### Post by jrrader on 2009-11-28
I'm not too sure.  Is it too late to uninstall wubi?

---

### Post by Space-Wolf on 2009-11-28
alright I think I messed something up.  Ubuntu was being retarded so I shut down the comp.  Vista is still fine but now I have a bunch less space, as if it partitioned but I know it didn't go well.

---

### Post by jrrader on 2009-11-28
You shut down during the install?  As long as you can get back into Vista you're okay.  Probably a good time time to remove wubi.  Vista's partition editor should show you where that space went to.  Check your installer from the menu next time you boot in to it before running the install.

---

