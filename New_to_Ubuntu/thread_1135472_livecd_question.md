---
title: "livecd question"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by tim1970 on 2009-04-24
I want to get an image of my hard drive before I install Ubuntu so I am going to boot up using the live cd first.  Since partimage is not installed by default, I will need to install it.  My question is how is this installed?  Does it just install it in memory, or does it temporarily use a part of my hard drive?


Tim

---

### Post by Peter09 on 2009-04-24
The LiveCD does not use your hard drive at all, just RAM (memory).

---

### Post by indytim on 2009-04-24
I believe there are some LiveCDs that have partimage built in (probably in the rescue-type of Live's).  I'm Windows-bound right now and don't have my Linux resources available to give you a complete answer.

IndyTim

---

### Post by finippino on 2009-04-24
Well to answer your first question, I dont do images of Linux.  I just do a complete Tar of my system files.  See the following link, [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311).
It works like a charm.  Has gotten me out of jams before and just did a restore.  

The second questions:  Im not exactly sure but I believe it is using a temporary space which does not stay after you remove the LiveCD so I would not worry about it.

Hope that helps.

---

### Post by Didius Falco on 2009-04-24
System Rescue CD has it right on it.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I just made my own Ubuntu 8.10 Live CD with partimage already on it. Just used it yesterday to back everything up in anticipation of installing 9.04 today.

I may upload it for distribution if I can find a spot that wants it. I still want to refine it more though - just customize the wallpaper, etc. 

Anyway, that Rescue CD should do the job for you.

---

### Post by ranch hand on 2009-04-24
All live CDs have some partition editor included.  You need it to install so it is there.

Ubuntu uses Gparted which is very nice.  In terminal you should have sfdisk and cfdisk.
I really like cfdisk.

You will have both sfdisk and cfdisk when you install your OS.  Gparted is in synaptic when you have updated your sources.

The easiest way to do that is in teriminal type  "sudo apt-get update"   give your password and let it roll.  When that is done just type "sudo apt-get install gparted" and that will be installed and ready to use.

---

### Post by Didius Falco on 2009-04-24
ranch hand,

He's looking for Partimage, to back up his partitions.

---

### Post by ranch hand on 2009-04-24
You can copy a partition to another with Gparted.  You can copy your home folder to another partition with just the Live CD because you hav very super user status on the Live CD.

---

