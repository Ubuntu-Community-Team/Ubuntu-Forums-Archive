---
title: "[SOLVED] Single profiles for windows/ubuntu"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by RonPDX on 2009-01-05
Good morning everyone, 

A couple months ago I decided to install ubuntu, I currently run XP and 8.10 as a duel boot on the same drive.

What I trying to figure how to do is share profiles for Firefox and Thunderbird. I ran across an article that explains how to do this however for the life of me I can not view or mount my windows partition, the only drive that is showing is my slave which is being used as for all of my backups. I would also like to view and maybe edit some of the files that I have on the XP side. 

I have been researching this all night and am just stuck. Any help would be appreciated.  [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by supererki on 2009-01-05
is the question : how to mount ntfs partition in ubuntu? sorry it was a bit confusing... anyways. if thats what you want to do then i personally use ntfs-3g  (sudo apt-get install ntfs-3g) .

then add
/dev/sdx /mount_point ntfs-3g defaults,locale=en_US.UTF-8 0 0

to /etc/fstab

---

