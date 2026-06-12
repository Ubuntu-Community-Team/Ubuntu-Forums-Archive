---
title: "Can I use one home folder for Mac and linux"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Kedster on 2009-12-31
I have just installed mac on to my computer and working on downloading ubuntu netbook remix, What I would liek to do is use the same home folder for both operating systems so that I can keep all my personal stuff on one partition. and availible somewhat naitivly to both OS's. 
How can I do this, i found two guids but I dont really know how to do them and they are both different. 

[http://chris.pirillo.com/how-to-move-the-home-folder-in-os-x-and-why/]("http://chris.pirillo.com/how-to-move-the-home-folder-in-os-x-and-why/")
and 
[http://www.tuxation.com/creating-home-partition-mac-linux.html]("http://www.tuxation.com/creating-home-partition-mac-linux.html")

Now my other question is, will this actually be safe to do or will it screw up both OS's?

---

### Post by Paqman on 2009-12-31
I'm no Mac guru, but i'm pretty sure OS X won't play nicely with most non-Apple filesystems, including all the Linux ones. Best to keep them separate.

There's nothing stopping you from having a shared data partition in something OS X can read/write to like FAT32 then linking your home folder locations (eg: Music, Documents) to the folders on it.

---

### Post by Kedster on 2010-01-01
Alright well if i am able symbolically link for those certain folders how would I go about doing that. would I have full compatibility in both OS's when things are symbolically linked?

---

