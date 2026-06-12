---
title: "Reducing Size of Windows XP Partition"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-02-06
I've just bought a fairly old desktop HP PC from an acquaintance. Windows XP is installed on the internal 250 Gb HDD.

What I need to do is reduce the size of the Windows partition by about 30 Gb, so that I can install Ubuntu 9.10.

But I've no idea how to reduce the size of the Windows partition without using something like Gparted, which I think reformats the whole HDD, doesn't it?

I've installed Auslogics Disk Defrag, which has nicely optimised all the files on the HDD onto the first portion, meaning that I should be able to reduce the back of the partition without deleting any files or file fragments.

So, does anyone know how I can reduce the Windows partition using XP?

---

### Post by yeats on 2010-02-06
> But I've no idea how to reduce the size of the Windows partition without using something like Gparted, which I think reformats the whole HDD, doesn't it?

No, actually.  It will do what you're looking to do without harming anything.  There are several gparted tutorials out there - some on the gparted website for instance.  Defragging is a smart first step.

---

### Post by llawwehttam on 2010-02-06
Gparted does NOT reformat the HDD. Boot from the ubuntu live cd and open gparted  then resize the xp partition from the end. If you resize from the beginning you may have problems.

---

### Post by underquark on 2010-02-06
From Windows, disable swap file and then defrag the hard disk (maybe a couple of times).  Then download ubuntu .iso and burn a Live CD.  Boot from the CD and you can use Gparted to shrink the Windows partition.  Now choose to install ubuntu and it will give you the option of installing alone (using all the disk) or alongside Windows (dual-booting).

---

### Post by raymondh on 2010-02-06
you'll need to use a 3rd party disk management utility (like gparted) as XP's disk utility does not have the ability to shrink.

-  Save files elsewhere
-  Defrag (2x if you have the patience)
-  download and burn a [live gparted CD]("http://gparted.sourceforge.net/download.php").  You can use gparted from the ubuntu liveCD as well.
-  when using gparted, uncheck the 'round-to-cylinder' box.

Are you not presented (when trying to install) a 'side-to-side' option and the ability to use/drag a slider to allocate partitions?  Sorry, it's been a while since I've seen a karmic install.

Raymond

---

### Post by underquark on 2010-02-06
I think the stumbling block will be GParted's reluctance to touch a heavily-fragmented Windows partition, hence the advice to defrag it first from within Windows.  Disabling the Windows swapfile is necessary because it exists as a fixed chunk of disk that won't move with the defrag process.

---

### Post by Roger Allott on 2010-02-06
Thanks to all. I didn't disable the swapfile and I didn't uncheck the 'round-to-cylinder' box, but everything seems to be fine disk-wise.

A very odd thing though is that my desktop is shifted right by about 50 pixels, meaning that I have a thin strip of black down the left side of the screen and the rightmost strip of desktop is missing.

The screen resolution is correct, but for some reason Ubuntu starts the display at the wrong pixel.

I had run the Live CD for both Ubuntu and Xubuntu before doing the proper install, and I had that issue both times. Windows doesn't do that shift, so I doubt it's that I need to adjust my horizontal shift on my monitor.

Anyone got a solution to this?

---

### Post by Roger Allott on 2010-02-06
I've just rebooted, which finished off the enabling of the nVidia driver, and the screen location issue is solved.

---

### Post by underquark on 2010-02-06
Woo-hoo!  Please mark this thread as [solved].  This helps both those looking for a solution to a problem and those who want to skip solved issues but who might help in an unsolved thread.

---

