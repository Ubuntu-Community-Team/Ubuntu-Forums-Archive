---
title: "One set data for 2 os's?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by comethalley on 2010-02-19
I've already installed ubuntu netbook remix- dual booting with xp.  I was actually pleasantly surprised at how easy it was - even the internet worked out of the box! But I noticed - probably obvious to anyone who knows a thing about computers - that the data would not go between the 2 os's.  Is there a simple way to configure the computer so you can access data from either os?  I saw something like it on lifehacker, but it didn't give simple enough instructions for a noob like me.  :p Now that I know how easy getting unr to work is, I'd reinstall it if it meant getting my data from either os.

---

### Post by mikeyphi on 2010-02-19
1. Home folders/Documents etc, on one Ubuntu OS are available to another Ubuntu OS. Just check under 'Places' and select the appropriate file system.

2. Otherwise, or if needing to use the data via differing styles of OSs, such as Ubuntu and MS, you might want to create a separate data partition.
See here for more info:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by comethalley on 2010-02-19
Thanks!  I'm still confused about what this does, though.  So it creates a data partition.  Could I see this partition while inside an os partition?  Could my documents be saved into that partition automatically?  If not, how would I get them there?  Sorry about the noob questions - I just don't want to do anything to my computer that I don't get.

---

### Post by uRock on 2010-02-19
Ubuntu can access the Windows partition easily, but Windows can't mount the Ubuntu partition.

To mount the Windows partition, go to places and click on the 123GB Filesystem. Check out the screenshot.

---

### Post by snowpine on 2010-02-19
As mentioned above, you can easily access your Windows partition from Ubuntu by clicking the Places menu.

If you want to access your Ubuntu partition from Windows, there are a few shareware applications available exactly for this purpose. I am not sure whether they will work with the new ext4 filesystem though.

I agree with the above that a separate "data" partition is the most elegant solution. However, it will certainly involve backing up all your data (on both OS's) and modifying your partitions using a Live CD.

---

### Post by theozzlives on 2010-02-19
Check [this]("http://ubuntuforums.org/showthread.php?t=1244185") out, there's no need for a data partition.

---

