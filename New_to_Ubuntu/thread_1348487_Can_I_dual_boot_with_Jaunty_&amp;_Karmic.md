---
title: "Can I dual boot with Jaunty &amp; Karmic"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2009-12-07
I am super happy running Hardy on my desk top and UNR jaunty on my Eee PC netboot. Since Karmic has been released I now want to install it on the netbook. Since I have a 160 Gig hard drive I thought I could install it along side of Jaunty so I could dual boot.  Can I make a single home partition for both OS to use?  If so what must I do to accomplish that?  Does it matter that my Jaunty is UNR and the Karmic is the regular release?

---

### Post by Yvan300 on 2009-12-07
Ah that's easy, but you may have to wipe your hard drive clean. Ok so first you boot your live cd, open gnome partition editor and now you would see the partitions. Now what to do is make 4 partitions. One for jaunty, one for karmic, one for the home folder and one for the swap. Now as you are install jaunty/karmic, when the partitioner comes up, choose manual. When you do this you will be given the option of what the partition will be used for. / is where the os will be installed and /home is your home folder. So all you have to do is choose the 2 / for each os and choose the same /home. 

Pretty simple, but hard to explain lol. :)

---

### Post by CaptainMark on 2009-12-07
i think you dont have to wipe your drive, just do a normal dual boot, in the new os add a line to /etc/fstab that mounts the first os's file system somewhere out of the way and then just make the second os's home folder a symbolic link to the first os's home folder. Feel free to disagree, ive never done this just heard of it being done.

EDIT: Yvan300's idea does give you a home folder on a completley seperate partition which is always safer if your going to be messing around with dual boots and resizing partitions.

---

### Post by Rex Bouwense on 2009-12-07
Thanks for the quick responses.  After rereading my own post I'm not sure if I was clear.  Anyway, I have two ideas and will pursue them both.  Since I already have the important data backed up to a flash drive the only things I might possibly lose are the settings and they cane be recovered if necessary from the desk top (or at least most of them.)  What I should have done when I initially installed was make the home folder but live and learn.  Thanks again.

---

### Post by oldfred on 2009-12-07
While many recommend a separate /home for ease of upgrading sharing /home may not be a good idea. Most applications in a newer install will update setting if it is a newer version, but I bet they do not know how to downdate ( is that a word?) any settings. You could share /home with different userid's but that defeats the purpose.

I suggest you create a /data partition for all your data. 

I found several users who have done this, and I am going to combine their methods, but have not yet.

I did not save the links but did save some of the comments:

 Morgan Hall said:
My personal solution (yes, I use thunderbird) -- I make my data directory a partion mounted on /usr/local so my homebrew apps are in /usr/local/bin. A data directory there contains the working directories for home data -- /usr/local/morganh/Data
Directories in /usr/local/morganh/Data include Downloads, Video, VirtualBox, mozilla, mozilla-thunderbird and so forth.
I install the new distribution, mount my /usr/local, strip out everything except Desktop from /home/morganh then run:

for i in `echo /usr/local/morganh/Data`;do; ln -s $i; done

 and another version:
map other partitions in as /media/main, /media/data and /media/backup, which is easily done when installing Ubuntu for example, then in those areas I have created a directory with my username just as in the home directory and used chown and chgrp to change ownership. I keep my essential data and backups in those areas. I also have a script which only needs to be run after installing a distro that creates a link to the directories I need in the home directory of the new install e.g. ln -s /media/data/username/video /home/username/video. I find this works well. The script also renames the dotted directories created by Firefox, Thunderbird and others, and creates links to the dotted directories for those as well. This carries my bookmarks and emails through each install.

---

### Post by ranch hand on 2009-12-07
If you already have your installed OS on 2 partitions it should not be hard to share the /home partition.

The critical thing is to make sure, as oldfred pointed out, is that your settings do not get tangled.

You must use a different user name for each of your OS'.  This way the settings for OS1 with user "Abe" do not mix with OS2 with user "Bob".

---

### Post by egalvan on 2009-12-07
> **oldfred said:**
> 


 and another version:...
map other partitions in as /media/main, /media/data and /media/backup, ...
in those areas I created a directory with my username just as in the home directory,...
 and used chown and chgrp to change ownership....
 I keep my essential data and backups in those areas.
 **I have a script** which only needs to be run after installing a distro that creates a link to the directories I need in the home directory of the new install e.g.
 ln -s /media/data/username/video /home/username/video...
 **The script also renames the dotted directories **created by Firefox, Thunderbird and others,
 and **creates links to the dotted directories for those as well**.
 This carries my bookmarks and emails through each install.

Sounds like an interesting script. Would be nice to find it and share it.

---

