---
title: "[SOLVED] backup apps - making the choice"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-02
can anybody advise me about apps for making backups of my data/system.  i am looking for something that i can run periodically to cover me in case my files or system gets lost/deleted/corrupted as seems tohave happened to one or two others i have read posts from.  i dont mean to sound like 'i wish it was more like windows', cos i love the way it isn't.  but something i can just click on once in a while and know that all my stuff has been backed up to somewhere so i can restore it if necessary would be really useful.  i checked the repos and there seem to be a number of possible apps to use eg sbackup and bacula but being a total divot i have no idea which would be best so a few suggestions would be much appreciated. 
thanks 
nigel:confused:

---

### Post by Michael.Godawski on 2008-12-02
From the Community Documentation:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Good place to start...

---

### Post by cek on 2008-12-02
Where are you backing your data up to?


I have a portable 200G HD that I use to keep copies of all my important stuff (music, pictures, etc.).

I turn it on periodically and mount it, then back up my stuff with a simple rsync command.

rsync -av /data/pictures /media/backup/pictures
rsync -av /data/mp3audio /media/backup/mp3audio

These two commands ensure that the contents of the folders on the /media/backup disk match what is in my /data folders.  In case something is lost, I can run the same commands simply by changing the order of the folders.

---

### Post by Sorivenul on 2008-12-02
I use rsync for almost all my backup needs.  It's documented in the link provided above.

gadmin-rsync is a graphical front-end for rsync that you may find useful.

---

### Post by mapes12 on 2008-12-02
The first thing to consider is making sure you have "/" and /home on separate partitions. /home contains all your files, settings bookmarks and anything else to do with your look & feel of your system. "/" contains your system and application software.

Here's how to split them apart: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

There are many ways to backup the separate partitions. For example try this for your "/" system partition: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) and then use some of the other suggestions on this thread to backup /home. You can even just copy everything to external media and reinstall /home in case of a catastophe.

For your "/" system files another method is to keep regular backups of your updates and applied applications using aptoncd (search for it in Synaptic Pacakage Manager and Google for its home page). Then, if your system crashes just reinstall Ubu from your regular install CD then just restore the aptoncd image to get your system back the way things were before it went wrong.

Others will no doubt have other solutions. The above is what works for me.

---

### Post by capnthommo on 2008-12-02
firtly let me say thanks to you all for the amazingly quick and comprehensive set of answers,  michael, thanks, i should have looked in the help pages first, shouldn't i?  as to alternative storage places, i am afraid i don't have any - just the laptop.  i think i shall have to look seriously at getting a separate hd.  anyway, it means i cant use any method that means using a different machine of any kind at least for the present.
Quote:- "making sure you have "/" and /home on separate partitions"  i dont undeerstand yet what his actually means.  i installed ubuntu from the disk and followed the instructions (not knowing what i was doing, i basically let the disk tell me what to do) so i dont know how it is partitioned or how to find out.  if the standard install is partitioned as you suggest then fine - if not then i need to find out how to change it, don't i?
anyway, for now i think i shall go with sbackup.
thanks again to you all - yet again ubuntu forums deliver the goods
:guitar:
nigel

---

### Post by richg on 2008-12-02
Find out if your laptop uses USB 1.1 or USB 2.0. Using 1.1 can take a lot of time for file transfers depending on the amount of files. My stepson who uses XP just bought a 500gb external drive for backups. The laptop is an older Toshiba model. Very slow so he bought a USB/Firewire PCMCIA card that has 2.0 capabilities. 
A lot faster than 1.1. He has a lot of music and videos.

I use an external hd for personal files with 8.04 on my desktop. For five years I have used the KISS principle. Copy and Paste. I do not partition. Never saw a need to. I then turn off the external hd.

Rich

---

### Post by capnthommo on 2008-12-02
yeeha!  success!  at least as far as it goes.  i installed sbackup and followed the instructions on the help link and i am now backed up on "/var/backup".  dont know if it will restore but not willing to risk it to find out.  perhaps i will create a file and do a backup/restore just for that to test it.  but it looks like it works fine.
thanks all.  see? i am learning - just not all that quickly.
nigel

---

