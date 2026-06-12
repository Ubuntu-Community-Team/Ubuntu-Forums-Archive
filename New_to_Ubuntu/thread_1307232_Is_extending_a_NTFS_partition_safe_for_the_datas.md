---
title: "Is extending a NTFS partition safe for the datas?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Deist on 2009-10-30
A question not related to 9.10 for a change! (^_-) (Am waiting a few weeks before upgrading myself seeing how new releases always prove quite buggy at first)
 
So, here is my noob question:
 
I have a HD with 2 NTFS partitions + not yet allocated space.
I now wish to extend the 2nd partition in order to include all of this unallocated space.
Since Zin doesn't handle this feature (pour changer [IMG]http://forum.ubuntu-fr.org/img/smilies/lol.png[/IMG]), I'm willing to use my Ubuntu LiveCD installation process (repartitioning step only in this case obviously) to do this extending of the partition (thus avoiding to install a new software for that sole purpose!).

What I'm wondering is: 1- Wether such operation is safe or risky since I have a lot of data on the partition I want to extend (it's actually like 98% full)?
And 2- Must I choose NTFS (in the "Use as" field), or leave "Do not use this partition"?


A big thanks in advance to any of you who took time to read my humble request (and a lot more even to those who will take time to answer it!! ^^).
-- DeisT

---

### Post by Slim Odds on 2009-10-30
Resizing partitions is ALWAYS dangerous......

Nuff said, backup!!!

---

### Post by RC1139 on 2009-10-30
I've never extended a partiton but I have shrunk plenty,  I always defrag first and never had a problem.  If that's your only objective then just use GParted. You can download the live CD here.[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

---

### Post by Deist on 2009-10-31
Thx you for the reminder and warning Slim Odds! I'd have backuped alright before doing this and then wouldn't have come to bother anybody with this question.
Unfortunately though, I'm at the moment almost out of disk space, a bit short of money to buy a new HD and yet in urgent need of some gigs for work! Therefore the situation that I need to allocate this free space, but can't backup my partition datas anywhere beforehand...
Although, your reminder will keep me cautious enough not to resize without being able to backup first I guess, therefore I'm only gonna make a 3rd partition instead of extending the 2nd one, much safer that way eh?
Gonna use GParted then, thx for the link RC1139!
-- DeisT

---

### Post by RC1139 on 2009-10-31
your very welcome, best of luck

---

