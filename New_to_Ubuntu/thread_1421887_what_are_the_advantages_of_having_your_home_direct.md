---
title: "what are the advantages of having your /home directory on a seperate partition..."
date: 2010-03-04
forum: New to Ubuntu
---

### Post by switch10 on 2010-03-04
The only advantages I can see, is when you upgrade your system, and if you are dual booting several linux OS's, I'd imagine they could all share a /home.

What about your ~/Music, ~/Video, etc. directories?  Don't you have to link them somewhere where you have significant storage space?

I'm just trying to figure out why so many people do this.  There must be something I am missing...

any thoughts?

---

### Post by QIII on 2010-03-04
When reinstalling (or backing up before an upgrade), having a saved copy of your /home partition saved somewhere means that you can just pop it back in where it belongs (but you really should use the functionality in the partition manager when installing a newer version to avoid re-formatting your /home partition) and preserve your files, your preferences and applications you have installed with Synaptic or .deb files (For that, you have to issue a command in the CLI to make a list, then another command to automatically reinstall the updated versions for the new version.  You may have to reinstall most third party applications.).

Backing up your files is much easier if you care to be ready in case of catastrophic failure.

Those are my primary reasons.

---

### Post by JKyleOKC on 2010-03-04
> **switch10 said:**
> What about your ~/Music, ~/Video, etc. directories?  Don't you have to link them somewhere where you have significant storage space?These directories are inside your home directory, so if you put home where there's plenty of available space, they'll have access to it.

The "~" in their names is a shortcut for your home directory.

---

### Post by Sir Jasper on 2010-03-04
Hi,

For those with only a single internal hard drive my view is that the smaller that drive is there is less point in having a separate Home partition.

So, for someone with an ancient machine and say, a 20 GB drive I cannot see the point in having separate partitions (because there is no need to make a decision as to what size each partition should be). Also, in any event, it would not take long to copy and paste the Home folder to another backup medium.

My regards

I&#7743; a big believer in frequent clones (or images) and also backups so I see a separate Home partition as a pragmatic decision rather than a desirable option.

---

### Post by baddnady23 on 2010-03-04
Like QIII said,if your /home is on a separate partition, you can upgrade to the new version of Linux (Ubuntu or whatever you use) and tell the new installation that you would like to use the existing /home partition rather than creating a new one.  Once the install is complete then, you have access to all your music, movies, pictures, documents, etc that you had before, all without actually having to move files around to get them back.

You could also have some different Linux distros using the same home folder, for example, on one physical hard drive, I have on separate partitions:

     1. Ubuntu file system
     2. Home
     3. Kubuntu file system
     4. Swap

This allows me to access the same exact home directory with both Ubuntu and Kubuntu and whatever other flavor of linux I'm feeling at the moment.

I feel that putting your /home on a separate partition should be to only way to go.  Obviously others may disagree but it has worked amazingly for me throughout the years.  Hope this helped clarify for you!

---

### Post by louieb on 2010-03-04
> **switch10 said:**
> What about your ~/Music, ~/Video, etc. directories?  Don't you have to link them somewhere where you have significant storage space?

I use a small 2 - GB /home - and thats exactly what I do - my documents, music, videos. are in folders on a 2nd hdd.  And I put symbolic links in my home folder to them. 

The advantage is my data is not mixed in with any part of the OS. 

BTW: there a quite a few that just use a separate data partition and don't bother to create a separate partition for /home - I've though about doing it that way - but I like the fact that if I have to reinstall the OS I don't have to redo all my program configurations too. -

---

### Post by switch10 on 2010-03-04
thanks for the input everyone.

I have my /home dir backing up with rsync in a cron job every day to my file server. I don't mind just restoring that after a reinstall.   

Good to know I'm not missing anything :)

thanks all.

---

### Post by NightwishFan on 2010-03-04
I prefer a new configuration with every new install. I merely link my data into /home/user from a 3rd "Data" partition that I permanently mount at install time.

---

### Post by oldfred on 2010-03-05
Separate home is for ease of upgrading. If using mutiple distributions you may have different versions of programs and should not share /home (you can with different login names but that defeats the convenience of use). So I am one more vote for separate /data partitions. 

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of blog
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by RevKeltina on 2010-03-05
Would it be possible to back up the home dir in some other fashion....i.e. on a cdrom?  I had to chuckle over the comment about an ancient machine being 20G....I'm WAY over the hill in that case! :-)

---

### Post by J V on 2010-03-05
Also, by making / smaller it mounts a bit faster (coupla seconds boot time saved)

So making a 10G / followed by a 40G /home (With symlinks to windows if you want cross-dos) could shave off 3 or 4 seconds per boot...

In linux theres no downside to making tons and tons of partitions... and in a new install a partition that already has the /home on it will save you half an hour of copying back data (and what happens if rsync kicks in and sees an empty /home? You lose all your data...)

---

### Post by switch10 on 2010-03-05
> **J V said:**
> Also, by making / smaller it mounts a bit faster (coupla seconds boot time saved)

So making a 10G / followed by a 40G /home (With symlinks to windows if you want cross-dos) could shave off 3 or 4 seconds per boot...

In linux theres no downside to making tons and tons of partitions... and in a new install a partition that already has the /home on it will save you half an hour of copying back data (and what happens if rsync kicks in and sees an empty /home? You lose all your data...)

Awesome!!  This is more along the lines of what I'm looking for.  One more feature added to my list!

I actually just decided to repartition a spare terabyte drive to test this out myself (I wanted to test out a script i wrote as well that reinstalls all of my previously installed packages).
 
Do you generally recommend making the / partition about 1/4 the size of the /home partition?

---

### Post by swoll1980 on 2010-03-05
You can go distro hopping, and leave your home folder there. When the new distro  is installed it will mount it, and all your personal preferences for all your apps will still be intact.

---

### Post by gordintoronto on 2010-03-05
> **switch10 said:**
> 
Do you generally recommend making the / partition about 1/4 the size of the /home partition?

There's no reason to make / larger than, um, 20 to 30 GB. Most people would say 10 GB is enough.

---

