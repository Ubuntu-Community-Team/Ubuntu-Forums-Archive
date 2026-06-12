---
title: "How do I remove everything ubuntu but keep windows so I can start again?"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by ambient007 on 2010-07-02
I'm helping my friend but ubuntu on her netbook that already has Windows 7.
 
1st we installed 9.10 which she 'upgraded' to 10.4
 
There were a few problems (really long boot time etc) which she wanted fixed so I installed 10.4 netbook remix from USB alongside Windows 7 & the original ubuntu installation.
 
I used the automatic partitioning setup in the installation (or what ever it's called).
 
After this, neither installation of ubuntu would boot up. After selecting the OS in GRUB on startup, is would say some thing like:
"Gave up waiting for root device/ Common causes are......
 
...ALERT! /dev/disk/by-uuid/..blah bah... does not exist. Dropping to a shell!
 
Not good.
 
Windows 7 still works fine but you have catch it at start up or it automatically starts booting the bad ubuntu installation.
 
 
However, I can still run Ubuntu straight from the USB (try first option).
 
I tried to install it again, thinking something must have gone wrong during the installation, but that does the same thing.
 
Now I have 3 instances of Ubuntu, 2 of which are the netbook remixes, and none of them work.
 
There are partitions all over the place now and I'm having a hard time figuring out what is what.
 
 
Now my question is:
 
[COLOR=red]**How can I remove all installations, partitions and anything to do with Ubuntu whilst preserving Windows 7 (starter) and any data on the partitions associated with it. **[/COLOR]
[COLOR=red]**Then  I can start again and hopefully get it working properly.**[/COLOR]
[COLOR=red][/COLOR] 
 
 
Sorry for the long post, but I need help.
 
Cheers.

---

### Post by akureikorineko on 2010-07-02
You should be able to modify your partitions when you start up the installer. When it gets to partitions, delete the two ubuntu partitions and just leave the windows 7 one alone.That should create "free space" where you should be able to install ubuntu to.

---

### Post by ambient007 on 2010-07-02
So, if I use that third option (manually configure partitions or whatever), do I then need to add & name partitions for the new installation or can I then go back and make it do it automatically?

Also I *think* it may be a problem with what ever chooses and loads the different operating systems as I installed a new version then a previously working old version stopped working as a result. Though the windows 7 OS keeps working...

Will deleting the partitions change this? Will it then automatically boot Win7 on startup without any menu to choose from?

---

### Post by k3lt01 on 2010-07-02
You can use the LiveCD to do a fresh install and use it to clean the "Ubuntu" partitions so you can start again.

I would suggest you take a look at [this]("http://www.psychocats.net/ubuntu/installing") and [this]("https://help.ubuntu.com/community/GraphicalInstall"). Bookmark Psychocats as it is a brilliant resource from a long time community member.

---

### Post by ambient007 on 2010-07-02
> **k3lt01 said:**
> You can use the LiveCD to do a fresh install and use it to clean the "Ubuntu" partitions so you can start again.

I would suggest you take a look at [this]("http://www.psychocats.net/ubuntu/installing") and [this]("https://help.ubuntu.com/community/GraphicalInstall"). Bookmark Psychocats as it is a brilliant resource from a long time community member.

Thanks, that's pretty much what I wanna do. 

I'm pretty confident doing installations with the 'Install them side by side' and 'Erase and use entire disk' options.

Though to do what you describe I would need to use the 'specify partitions manually' option. 
That should be fine for deleting partitions, but I don't really know what to do when specifying the partitions for the new installation.

---

### Post by k3lt01 on 2010-07-02
The partition manager will "see" Windows and Ubuntu sowhen you get to it write down what partitions are what. Then select manual partitioning and once your in there just delete the Ubuntu partition while leaving Windows alone. You should then get a Windows partition and a blank partition, now just install Ubuntu on the blank (i.e. old Ubuntu partition) following the partitioning advice in the links supplied as though you are treating the "blank Ubuntu" partition as the hard drive.

---

### Post by ambient007 on 2010-07-02
> **k3lt01 said:**
> The partition manager will "see" Windows and Ubuntu sowhen you get to it write down what partitions are what. Then select manual partitioning and once your in there just delete the Ubuntu partition while leaving Windows alone. You should then get a Windows partition and a blank partition, now just install Ubuntu on the blank (i.e. old Ubuntu partition) following the partitioning advice in the links supplied as though you are treating the "blank Ubuntu" partition as the hard drive.

Would I have to specify the SWAP or name the ubuntu partition anything specific?

Or, at that point (after I've deleted everything I need to) can I go back and use the automatic 'install side by side' option. If you follow what I mean...

---

### Post by k3lt01 on 2010-07-02
Yes you choose the file system, so for / and /home you would choose ext4 and for SWAP you choose SWAP.

I doubt you could go back and install side by side, I have never tried it though so I can't give a definitive answer sorry.

---

