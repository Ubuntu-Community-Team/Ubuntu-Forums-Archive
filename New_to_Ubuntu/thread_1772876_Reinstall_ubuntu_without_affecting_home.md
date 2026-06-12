---
title: "Reinstall ubuntu without affecting /home"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by kuckunniwi on 2011-06-01
Hi!

I'm planning on upgrading from Lucid to Natty (new install). I have root installed on one partition (sda1) and /home on another (sda3). If during installation, I choose *sda3* as /home directory, but don't format that partition, will it leave my home intact? (I realize how newby-ish this question is, but better safe than sorry!)

May I encounter any software related problems after installing? (I have *calibre* and *Jdownloader* installed in the home folder).

Thanks!

---

### Post by satanselbow on 2011-06-01
Yep mounting your existing /home is the way to go - as you say yourself DO NOT FORMAT!

Good luck ;)

---

### Post by seawolf167 on 2011-06-01
Aye, all you do is specific the partition to mount at /home as /home. Do not format it. You can do the same thing with your swap partition.

If you are concerned (and regardless, it is a good idea), back up with [Clonezilla ]("http://www.clonezilla.org")before you reinstall, so if something happens (accidentally or otherwise) you can go back to the start easily and try again.

---

### Post by kuckunniwi on 2011-06-01
> **seawolf167 said:**
> Aye, all you do is specific the partition to mount at /home as /home. Do not format it. You can do the same thing with your swap partition.

If you are concerned (and regardless, it is a good idea), back up with [Clonezilla ]("http://www.clonezilla.org")before you reinstall, so if something happens (accidentally or otherwise) you can go back to the start easily and try again.

Thanks! I'll definitely give Clonezilla a try!

---

### Post by oldfred on 2011-06-01
If you have a larger hard drive with space for another 10 or 20GB partition just install the new version, keeping old verison. Old version may end up with settings in /home that are not compatible but most things would still work. Then if you have issues of something you forgot to save then you could still boot old version.

If you have installed a lot of applications:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by kuckunniwi on 2011-06-02
> **oldfred said:**
> If you have a larger hard drive with space for another 10 or 20GB partition just install the new version, keeping old verison. Old version may end up with settings in /home that are not compatible but most things would still work. Then if you have issues of something you forgot to save then you could still boot old version.

If you have installed a lot of applications:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade


I've backed up my home folder, and intend on using my current home folder for the new install, and hope everything works well. I've read it's also important to choose the same name for the system and same user name to avoid access problems in the new installation. Hopefull, upgrade will be smoothc and I'll get no software conflicts later between newer and older versions. Even if I do, it's worth a try, because if it works, I avoid having to reinstate over 150Gb of files. If not, I just format again, and since installation is less than 1/2 an hour, it's no big loss.

What I am wondering is...if I have software conflict-related problems after installing (using current /home folder), would it be viable to boot using the liveCD, mount my /home partition, delete all the hidden files snd program info (leaving only Music, Pictures, Documents, etc. folders) and then make the new install using my current /home?

I understand that I would lose my program settings, but would I possibly avoid software conflicts this way?

Thank you to everyone for your help!

---

### Post by oldfred on 2011-06-02
The only issue you might have would be if you booted the older version with a separate new verison. Software is designed to be updated, just not rolled back. So you should have no problems using your current /home with a new install.

I find the hidden user settings in /home are small, on the order of 250MB. Since I install each new version of Ubuntu into a new partition, I only copy some settings from /home to my new install and keep /home inside root. But I have all my data in separate partitions. I started with some data in a shared NTFS with XP. Now I have most of my data in a /data Linux partition and link folders into /home so it looks just like every other install.

---

