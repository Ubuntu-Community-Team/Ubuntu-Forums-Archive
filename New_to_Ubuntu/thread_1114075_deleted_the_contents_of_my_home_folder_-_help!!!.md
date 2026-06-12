---
title: "deleted the contents of my home folder - help!!!"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by kapi on 2009-04-02
Feel like a right numpty! I wasnt paying attention and was trying to deleted the contents of a datastick, must have been in the wrong drive and delete the contents of my home folder. Am worried it will screw up Ubuntu 

what do I do next? do I have to reinstall anything?

Lost a weeks worth of web design - feel like crap please help

I know, i know, backup more often - lesson learned

Thanks

Kapi

---

### Post by philinux on 2009-04-02
Look in the trash can first.

---

### Post by kpatz on 2009-04-02
It won't screw up Ubuntu, just your settings under your account will get reset back to the defaults (e.g. desktop, preferences, etc.).

Worst case, you create a new user account and delete the old one.

---

### Post by unutbu on 2009-04-02
The first thing to do is to shutdown and reboot from a LiveCD.
This will stop the OS from writing into the physical hard drive space that contains your deleted home data.

Do research. Do not jump into anything. Your data, as much as can be recovered, will still be there in half an hour, tomorrow, and in a week from now. Take a walk. Planning your next moves carefully will help.


The next thing to do is clone the partition containing your home directory using a tool like PartImage. (See [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) and [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522))


Finally, to begin recovering your files, you can try PhotoRec or any of the tools listed here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). Apply PhotoRec to the cloned partition. By using a cloned partition, you can try more than one recovery tool, and never risk making the situation worse.

Here is aysiu's (psychocat's) guide on using PhotoRec:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

Here is a linux.com article on the same topic:
[http://www.linux.com/articles/56588](http://www.linux.com/articles/56588)

(Despite it's name, PhotoRec can recover many file types, not just photos: [http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec))

Note that you'll need a lot of hard drive space to do all this. 
The cloned partition has to be at least as big as the partition holding your home partition.
And the recovery tool (like PhotoRec) will need an equal amount of space to save what files it recovers.

If you are really keen on recovering as much as possible, and if your home directory was on an ext3 partition, Calo Wood has a very interesting explanation of how he recovered from a problem similar to yours: [http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by kapi on 2009-04-02
Phew, thanks. 

I have folders in the var/www folder. if I create a new account will it remove them or will they be OK?

---

### Post by unutbu on 2009-04-02
LOL, if your files are in /var/www, then creating a new user is completely safe. :)

---

