---
title: "What is the best way to integrate 9.04 into my existing windows environment"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by xtraspecialj on 2009-06-22
Hi,
Alright, I want to install 9.04 on this old desktop (I previously had 8.10 installed and screwed it up over the last 4 months).  I just want to wipe it clean and install fresh.  What I want is it to serve media to my wireless media device upstairs and with my windows machines in the house (A windowsXP desktop and Windows Vista64 laptop), and, to share files seemlessly with my two windows machines (both ways), and be a print server and web server.  I had successfully setup mediatomb and a LAMP server on my previous 8.10 version, but I never did get file sharing to work properly.  From what I understand, with Samba installed on the Ubuntu machine, I should be able to do all the sharing through the System>Administration tabs.  I shouldn't have to go in and edit config files (that is what got me all messed up with my previous installation).  Also, should I have the same user name on my Linux machine, and both my Windows machines?

---

### Post by medic2000 on 2009-06-22
Hmm i don"t know much about sharing but first and advice to you: Always backup conf files before editing. There is a great tutorial about samba:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by raedbenz on 2009-06-22
Where did you install your previous Ubuntu 8.10? was it installed in a separated partition or not?

if yes, then format that partition after taking the useful stuff, then install Ubuntu 9.04 in the clean partition.

---

### Post by xtraspecialj on 2009-06-22
yeah medic, that is something I have learned the hard way.

no redbaenz, I hadn't partitioned the drive up.  I plan on it this time though.  Know any good tutorials for that.  

Also, should I have the same username on all three machines?

---

### Post by Celauran on 2009-06-22
> **xtraspecialj said:**
> Also, should I have the same username on all three machines?

You'll want to create accounts for each Windows user on the Linux machine. Add these users to a group and give that group read/write access to the directory you want to share.

---

### Post by xtraspecialj on 2009-06-22
oh, also medic, is that really necessary with Ubuntu.  Doesn't Samba just work without having to go into the config files.  I had the printer set up on the ubuntu machine useable by the windows machines by just going through System>Administration>Printing>Server>Settings>Publish Shared Printers connected to this system.  It worked fine UNTIL I started reading Samba tutorials and messing with stuff.  That is when everything got all screwed up.

---

### Post by xtraspecialj on 2009-06-22
I am pretty sure I know how to do that Celauran, but in the spirit of the "Absolute Beginners Talk" forum, and because I am not completely sure, how exactly do I do that?

---

### Post by nhasian on 2009-06-22
Hello xtraspecialj,

use the 9.04 Alternate CD so you can setup EXT4 volumes during the install (EXT4 will be the default filesystem in 9.10) so this will save you the trouble of having to start fresh again in a few months...

filesharing in ubuntu is even EASIER than in windows vista.  After Ubuntu is installed, simply right click on your folder and choose *sharing options*.  If you dont already have samba installed, it will prompt you to install them.  now you should see your shares on the windows network.  thats something we still cant get right with windows vista in my house...

If you need the media shared via a DLNA server for ps3, xbox360, or some newer TVs that have built in DLNA clients, you can install ushare to share your media.

```
sudo apt-get install ushare
```

---

### Post by xtraspecialj on 2009-06-22
Awesome Nhasian, I kinda got the impression it was that easy after I set the printer up kinda like that.  I should have tried it before I started manually configuring Samba all over the place and screwing it all up.  Oh well.  Maybe as my knowledge gets better I will get into the manual thing a little bit more.  
So, doing it the way you say, is it still necessary for me to setup Windows users on my Ubuntu machine?  Because I didn't have to do that with the printer share

---

### Post by nhasian on 2009-06-22
no you dont have to setup windows users.  just turn on the guest option in the share.  otherwise you'll need to use your username/password from ubuntu.  also if you've fubar'd your samba config you can blow it away with:

```
sudo apt-get purge samba
```

then reinstall it with:

```
sudo apt-get install samba
```



> **xtraspecialj said:**
> Awesome Nhasian, I kinda got the impression it was that easy after I set the printer up kinda like that.  I should have tried it before I started manually configuring Samba all over the place and screwing it all up.  Oh well.  Maybe as my knowledge gets better I will get into the manual thing a little bit more.  
So, doing it the way you say, is it still necessary for me to setup Windows users on my Ubuntu machine?  Because I didn't have to do that with the printer share

---

