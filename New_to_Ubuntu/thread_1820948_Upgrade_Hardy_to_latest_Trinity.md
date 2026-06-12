---
title: "Upgrade Hardy to latest Trinity"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by jimwill on 2011-08-08
I'm currently running Hardy on my desktop. I have been thinking about upgrading, but I don't like the KDE4 desktop. I know that Trinity is KDE3.5, but worry that upgrading to Trinity may cause the loss of some things I have on my drive, since if I read correctly I have to go through all the normal upgrades to Kubuntu before running the Trinity upgrade.

The other option I have is that I have a 40 gig partition that I set aside for virtual machines (I've got 3 or 4 on it, but wouldn't worry too much about loosing them). Would it be better to just install Trinity on that partition and keep my Hardy where it is, undisturbed? That would leave the option of transferring data/software from Hardy to Trinity.


Whats your opinion? (and no - I don't want to use the KDE4.desktop!)
Thanks for any suggestions/pointers/help!

---

### Post by ankspo71 on 2011-08-09
Hi,
I am assuming your Hardy partition is larger than your separate 40 gig partition, so I have another suggestion. Use that 40 gig partition as a place to backup all of your important files and settings. Then download the latest Trinity CD and install it where Hardy is (replacing Hardy). Then copy your files and settings back from the 40 gig partition to the new Trinity partition. If your files and settings don't amount to alot of space you might be able to keep your virtual machines too.

Or you can simply burn all of your files and settings to a CD or DVD (or any other storage device) and copy them back onto the hard drive after you have installed the latest Trinity CD.

CD images for the latest Trinity can be found here:
[http://apt.pearsoncomputing.net/cdimages/index.html](http://apt.pearsoncomputing.net/cdimages/index.html)
Try it out as a live cd for a while before installing it though.

I'm not going to recommend upgrading your system (in your case), because the upgrade process either works by upgrading one *ubuntu version at a time or one *ubuntu LTS version at a time, so to upgrade from Hardy would require at least two separate upgrades to become current with the latest Trinity (Maverick). Something could go wrong along the way and you will still be stuck upgrading to KDE4. Then if you don't want kDE4 you would have to remove KDE4 and then finally add the Trinity repositories to install Trinity's KDE3. So the upgrade process from Hardy to Maverick (or Natty) is actually much more work and will cost you alot more bandwidth and time.

Hope this helps.

---

### Post by ankspo71 on 2011-08-09
Also, if your Hardy installation has a separate partition for /home, you could try the advice I said in this thread: [http://ubuntuforums.org/showpost.php?p=11130033&postcount=2](http://ubuntuforums.org/showpost.php?p=11130033&postcount=2)
(Note that the Trinity CDs are based on Ubuntu so you shouldn't run into any problems.)

---

### Post by beew on 2011-08-10
> **jimwill said:**
> I'm currently running Hardy on my desktop. I have been thinking about upgrading, but I don't like the KDE4 desktop. I know that Trinity is KDE3.5, but worry that upgrading to Trinity may cause the loss of some things I have on my drive, since if I read correctly I have to go through all the normal upgrades to Kubuntu before running the Trinity upgrade.

The other option I have is that I have a 40 gig partition that I set aside for virtual machines (I've got 3 or 4 on it, but wouldn't worry too much about loosing them). Would it be better to just install Trinity on that partition and keep my Hardy where it is, undisturbed? That would leave the option of transferring data/software from Hardy to Trinity.


Whats your opinion? (and no - I don't want to use the KDE4.desktop!)
Thanks for any suggestions/pointers/help!


Hardy is dead (unless you are running a server) Instead of installing the new versions in virtual machines you should instead update your OS. Upgrade will not work as far as I know (since all the repos and support infrastures for Hardy has been taken down), you must do a clean install.

Time to move on, my friend. :)

---

### Post by jimwill on 2011-08-14
Thank you ankspo71. I think I'm going to try the backup of what I want to keep, and hope I don't overlook anything!

beew - I think you miss-understood me. (not hard for the way I say things sometimes) On the vm I run winxp, puppylinux, an ubuntu server (for experimenting), and mikeos (again for experimenting) but kubuntu is my host machine. I have trinity on a laptop. And I do know that hardy isn't supported, which is why I was thinking of upgrading to trinity. Thanks for your input anyway!!

---

