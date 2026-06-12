---
title: "Backing up for clean install 10.04 - guidance please!"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by prenoob on 2010-04-22
I'm new to Ubuntu (about three months on 9.10) and I'm planning to upgrade to 10.04 by clean install.  I am backing up my system, using the "Sbackup" tool to an external drive (USB) and using its default settings.  These are to save /var/ - /home/ -/usr/local/ - /etc/ .

Am I thinking along the right lines and can I be sure that 10.04 will have the corresponding "Sbackup Restore".  It's all academic if it doesn't!

Trev

---

### Post by duanedesign on 2010-04-22
Since you are going to do a clean install I would look into creating a separate /home partition. A separate /home allows you to keep your settings and files in the event you reinstall Ubuntu.

---

### Post by nhasian on 2010-04-22
> **prenoob said:**
> Am I thinking along the right lines and can I be sure that 10.04 will have the corresponding "Sbackup Restore".  It's all academic if it doesn't!

sbackup isn't installed by default.  you would have to install it after installing Ubuntu 10.04.  also i'm not sure how well it would work backing up from one version of ubuntu and restoring it to another.  it may cause problems.  your best bet would be to simply 

1) copy your /home folder to an external hard disk.
2) use the 10.04 LiveCD to create new EXT4 partitions for / and /home
3) copy your data back to the new /home folder
4) then proceed to install Ubuntu 10.04 Lucid Lynx

---

### Post by indytim on 2010-04-22
Wouldn't you want to do #4 BEFORE #3?

Indytim

---

### Post by prenoob on 2010-04-22
Thanks everyone and apologies for the delay (I was called out).  I get the pictur but I am not keen on creating a partition, as I have never done it and am very much on my own here!

So do I take it that it is enough to copy the /home folder?  I am wondering about settings which I would want to keep if possible - Sun Java, for instance - any thoughts?

---

### Post by nhasian on 2010-04-23
> **indytim said:**
> Wouldn't you want to do #4 BEFORE #3?

Negative.  its easier to copy your /home directory back THEN install ubuntu.  that way all the permissions will be setup properly for you.  :popcorn:

---

### Post by nhasian on 2010-04-23
> **prenoob said:**
> Thanks everyone and apologies for the delay (I was called out).  I get the pictur but I am not keen on creating a partition, as I have never done it and am very much on my own here!

So do I take it that it is enough to copy the /home folder?  I am wondering about settings which I would want to keep if possible - Sun Java, for instance - any thoughts?

Here is step by step instructions with pictures for how to make a /home partition (not folder)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

almost all your preferences are saved in your home folder.  firefox bookmarks, pidgin, empathy, evolution data, etc.  on some rare occasions some programs will save data to /etc like grub2.  The only program i've run that saved data there that i needed to save (to my knowledge anyway) was just hellanzb.

---

### Post by mikodo on 2010-04-23
> **nhasian said:**
> sbackup isn't installed by default.  you would have to install it after installing Ubuntu 10.04.  also i'm not sure how well it would work backing up from one version of ubuntu and restoring it to another.  it may cause problems.  your best bet would be to simply 

1) copy your /home folder to an external hard disk.
2) use the 10.04 LiveCD to create new EXT4 partitions for / and /home
3) copy your data back to the new /home folder
4) then proceed to install Ubuntu 10.04 Lucid Lynx
Being that you are new, I would like to point out that I believe nhasian is talking about doing a **manual install** (option in the Live CD offered), point to the (/) and /home partitions in Step 4, as using those partitions for installation and your data and preferences he mentioned, will be in your new Lucid OS.

---

### Post by otriades on 2010-04-23
You can read this on partition in linux/ubuntu:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html)
[http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System](http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System)

---

