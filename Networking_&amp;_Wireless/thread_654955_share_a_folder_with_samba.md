---
title: "share a folder with samba"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by Gallo_Pinto on 2007-12-31
Hi all.
I've read most of the samba config documentation from help.ubuntu.com, a thread or two here, and the samba.conf man page. It doesn't seem to explain my exact situation.

I want to share /media/hda1/Music so that it can be accessed from a Windows Vista box. I dual-boot this box with windows XP. When I'm booted in XP the Vista box mounts the network drive //GALLO/GPMUSIC. I would ideally like my Samba to provide the same shared path.

Of course, I can always change my XP's share settings to match that of Samba if it's tricky to get that. I just don't understand how to specify a folder to share that is not just a user's home.

Thanks!!

---

### Post by kegobeer on 2007-12-31
Just so I understand - you have Ubuntu and XP installed on the same machine?

---

### Post by at0myx on 2007-12-31
I am having the exact same problems in the thread: [http://ubuntuforums.org/showthread.php?t=653337](http://ubuntuforums.org/showthread.php?t=653337)

For some reason, I think there is some additional security when it comes to sharing a mounted volume.  It shares fine when I use a folder in my home directory.

---

### Post by Gallo_Pinto on 2007-12-31
kegobeer- yes, this machine dual-boots XP and Ubuntu.
at0myx- thanks, I'll have a look-see

---

### Post by kegobeer on 2007-12-31
In Ubuntu, it's System -> Administration -> Shared Folders.  Pick the folders you want to share.  I would also install system-config-samba, a GUI that makes it very easy to administer the Samba system.

---

### Post by Gallo_Pinto on 2008-01-01
Okay kegobeer: I didn't know that!  But I still ahve the same problem that at0myx has. I can click the button to add a shared folder, navigate to my mounted volume (the folder I wish to share is not on the physical HD that the system is installed on), but I cannot get to any folders on it because of the permissions. It looks like at0myx has tried many things. I think I'll maybe have a go at setting the "octal permission??" (don't know if that's the right name) in the terminal. Will find a how-to on that and see if it works.
Thanks

---

### Post by BLTicklemonster on 2008-01-01
Look at the link in my sig. Remember to reboot. I've been using Ubuntu for 2 years now, and just recently got the XP boxes on the network to see my shares.

Good luck.

And don't forget to reboot.

---

### Post by Gallo_Pinto on 2008-01-02
BLT-
I've followed your tutorial, and I'm able to my ubuntu box from my vista box. There's one problem:  I wanted to share /media/hda1/music, but instead it has now shared /media/hda1, which therefore shares ALL of my data drive, some of which is a tad personal and I don't want other users accessing it. 

I can't think of any particular reason why only the root of the physical drive can be shared. I tried setting permissions on /media/hda1 to 777, but perhaps this is barking up the wrong tree or setting permissions on the mountpoint without setting them on the device?  Anyway, it's a touch confusing, but better than nothing.

Thanks for the link

---

### Post by BLTicklemonster on 2008-01-02
I have the same problem, yet my /home/bill/Shared shows up alone. 

I don't know why it does that, but like you said, it's better than nothing! 

I'm sure one day the correction will present itself.

---

### Post by Gallo_Pinto on 2008-01-02
Haha! Gallo had a brainwave. Last night, I lay awake in bed and I thought to myself:

It wants to share the root of a mounted volume, so I can just mount the music folder..

```
gallo@GALLO:~$ sudo mount /media/hda1/Music /media/Music
[sudo] password for gallo:
mount: /media/hda1/Music is not a block device
gallo@GALLO:~$ man mount
gallo@GALLO:~$ sudo mount --rbind /media/hda1/Music /media/Music
gallo@GALLO:~$ ls /media/Music
   and now it lists everyhting nicely!!

```

I had to look at the man page to figure out how to get around that block device thing. Now the only problem is, I need this to automount at boot.  So I guess I should have a stab at modifying my fstab. Is there a way for me to put the --rbind thing in the fstab?

Almost there...  I hope at0myx is reading this..  might help there too.

---

