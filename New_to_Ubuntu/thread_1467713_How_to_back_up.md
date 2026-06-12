---
title: "How to back up?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by llmunro on 2010-05-01
Hello...

Just wondering what the best method is for backing up Ubuntu?  How should I go about it and what needs to be backed up?

Thanks much.
Best,
Lisa

---

### Post by cap10Ibraim on 2010-05-01
maybe  no one is willing to answer because its a recurring question with some details do some googling and search the forum

---

### Post by llmunro on 2010-05-01
Sorry.  Disregard, then.

Best,
Lisa

---

### Post by Ralph L on 2010-05-01
I have been using Ubuntu for a couple of years, but I am really a newbie.  However, I looked at backup systems about a year ago and was disappointed.  There are a number of them and I tried sbackup.  It was very "brittle", in that when it got interrupted during a backup,it did not complete writing the tar (or whatever) compressed file.  It gave no error messages, but when I tried to do a restore, it could not read the compressed file.  In my experience (on other systems) use of a compressed single file to hold all my files is not a good design.  If that single file has any defects, the entire backup is no good.  (Hence brittle).  

Anyway I am currently doing my backups using a simple copy to a usb hard drive.  I have everything I want backed up in my "Documents" folder, including all my email, all my contacts, all my email group lists, and all my Firefox bookmarks.  Then I just bring up Terminal and type "cp -a Documents destination".  In my case destination is an ext3 partition on my external usb hard drive.  Note that it is important to backup to a Linux partition, not a Windows partition--as all new hard drives have.  The problem with Windows partitions is that Linux allows more special characters in file names than does Windows and you will get an error if you try to copy a file with one of those special characters in the name.  

I created the ext3 (now I would create an ext4 partition), using gparted.  It may be necessary to install gparted with Synaptic.  Note that cp is much faster the a Nautilus drag and drop.  It will also copy ACLs which is important for me.  

It is also a good idea to keep a 3 (or more) deep rotation of backups.  In other words erase the 4th newest backup, but keep the 3 newest ones.  The do the backup.  In this way even if the newest backup cannot be read, there will be an older one, so not everything is lost.  Also remember that you may want to recover a single file or folder that you erased by accident, so your backup system should support that.

There is a newer backup called luckybackup, of which I read good reviews.  I will try it and other backup systems when I get a chance, but this is where I stand.

Although it doesn't yet have backups discussed, I have a web site for newbies (sharing how I did things) at [http://ubuntulinuxnoviceguide.webs.com/](http://ubuntulinuxnoviceguide.webs.com/)

Ralph

---

### Post by llmunro on 2010-05-01
Hi Ralph,

Thanks much!  I'm considering switching to ubuntu as more or less my main OS, but am paranoid about backing up.  I think your idea of keeping the last few most recent backups is a good idea.

Also, thanks for sharing your website!  I will be visiting it often!

Best,
Lisa

---

### Post by lazymangaka on 2010-05-01
Honestly, the best backup software I've found on Ubuntu is Deja Dup. It's very similar to Time Machine in Mac OS X in that it just works. You can tell it to back up your home folder or your entire computer if you want, and it can be scheduled to do it to external drives or online sources.

---

### Post by llmunro on 2010-05-01
Lazymangaka,

Thanks for the Deja Dup suggestion!  I just downloaded it and will be trying it out with my external hard drive.  Thank you! :)

Best,
Lisa

---

### Post by oldsoundguy on 2010-05-01
Really, the only thing you need to back up is your ~/home folder (under  places). All you need is that and your install CD if a drive crashes to put it all on a new drive.

You can drag and drop all of the folders in the home folder to a thumb drive.  

IF you have to re-install, do the install and plug the thumb drive in and drag and drop the folders back to the NEW home folder .. and OVERWRITE.

You are back in business .. including EVERYTHING you have loaded out of the repositories and all of your tweaks!  

(go take a look at the folder .. you will see just what is there!)

---

### Post by llmunro on 2010-05-02
I am pleasantly amazed, as backing up (which I had assumed was some complicated process), seems fairly easy!

Thank you for taking the mystery out of it!
Best,
Lisa

---

