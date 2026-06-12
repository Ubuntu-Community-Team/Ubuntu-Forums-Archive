---
title: "[SOLVED] I broke something"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by tropdoug on 2008-12-31
I was moving my /home to a new drive, but things went a little wrong. So I reversed the process, and checked to make sure no files were left behind. All hidden files were back where they should be. However I obviously broke something

On login my password is accepted the screen blanks out then returns to the login. I have reset my password from the root shell in recovery mode. But same thing occurs. I do not really want to re install, and am using the live CD to do this. 

I think it could be the X server is broke maybe. Any ideas? V8.10

---

### Post by cb34 on 2008-12-31
im a semi newbie so i dont have any super cow powers or anything:p but real quick first thought is, find out if it's not allowing the login part of the equation, or the login is going through, but then its a xorg.. gnome or filesystem problem.. so.. i would look to the logs in /var/log and also in your home dir, if it even is registering in there and writing to it, the xsession-errors file, and maybe even nuke that log file, so it starts fresh and you can see things more clearly. try to see where its getting stopped so you know how to move forward, that's what i would do, but someone with more experience, or maybe this exact problem might have a "real" solution for you.
peace.

---

### Post by Ender41 on 2008-12-31
> **tropdoug said:**
> I was moving my /home to a new drive, but things went a little wrong. So I reversed the process, and checked to make sure no files were left behind. All hidden files were back where they should be. However I obviously broke something

On login my password is accepted the screen blanks out then returns to the login. I have reset my password from the root shell in recovery mode. But same thing occurs. I do not really want to re install, and am using the live CD to do this. 

I think it could be the X server is broke maybe. Any ideas? V8.10

It's possible, try sudo dpkg-reconfigure -phigh xserver-xorg from root shell. Note you may need to reinstall the restricted drivers if you were using them as well.

---

### Post by decoherence on 2008-12-31
what method did you use to move your home?

---

### Post by tropdoug on 2008-12-31
found a thread at [www.ibm.com/developerworks/library/l-part](www.ibm.com/developerworks/library/l-part) .... something or other it didn't print out fully. 

I used cp ax * /media/Home/newpart to copy the home files, but It didn't seem to go right, it would not copy a directory contained in the original /home so I did 

cd /media/Home 
then cp ax * /home  to copy the files back :-(

PS I labeled the new drive as Home and it has ext3 fs on it

---

### Post by cb34 on 2008-12-31
so you put the directory newpart in /home

so now you have all your original /home files in /home/newpart, instead of putting them back into /home ..i think from what i can tell.

instead of copying everything that was inside the directory newpart back to /home, you put the directory newpart into /home.

is that right from what i understand from your post?

edit-> "cd /media/Home" should have been "cd /media/Home/newpart" if i got this straight..??

edit#2-> if this is what you did, you may be able to fix it by copying everything **inside** the newpart dir into /home

---

### Post by tropdoug on 2008-12-31
Aha see where your coming from, I forgot to say, that I also saw that, and copied all the files out of /home/newpart into /home 

Sorry

& then deleted /home/newpart

Is there a way to just reinstall the xserver maybe?

---

### Post by cb34 on 2008-12-31
sudo apt-get purge xorg (backup /etc/X11/xorg.conf file first in my opinon if you need it for some reason later)
then
reinstall it
sudo apt-get install xorg (may be a good idea to reboot first ?)

then after that, if still problems, maybe you have to reinstall your vid card driver..?
(which during the vid card driver install it would usually automatically setup the xorg.conf file at that time)
[(install for nvidia cards)]("http://ubuntuforums.org/showthread.php?t=1026163") - you dont have to use the 180.06 version like in that post[noparse];)[/noparse]
if you have nvidia card

---

### Post by Ender41 on 2008-12-31
> **cb34 said:**
> sudo apt-get purge xorg (backup /etc/X11/xorg.conf file first in my opinon if you need it for some reason later)
then
reinstall it
sudo apt-get install xorg (may be a good idea to reboot first ?)

then after that, if still problems, maybe you have to reinstall your vid card driver..?
(which during the vid card driver install it would usually automatically setup the xorg.conf file at that time)
[(install for nvidia cards)]("http://ubuntuforums.org/showthread.php?t=1026163")


 Why would moving the home directory break xorg, it might stop a user using it because one of the /home/user files is corrupted but I don't think it would break the whole thing. 

If the suggestion I made above doesn't help then post the output of
cat .xsession-errors.

---

### Post by cb34 on 2008-12-31
i have no idea, he just asked how to reinstall xorg, assuming after he tried your suggestion to try reconfiguring, so i posted how to do it.

the first thing i did suggest was to check his logs including ~/.xsession-errors to hunt the problem down ;)

---

### Post by Ender41 on 2008-12-31
> **cb34 said:**
> i have no idea, he just asked how to reinstall xorg, assuming after he tried your suggestion to try reconfiguring, so i posted how to do it.

the first thing i did suggest was to check his logs including ~/.xsession-errors to hunt the problem down ;)

 Fair enough and I appologise for missing his asking what you suggested, it just strikes me as such a windows way of thinking.
ie if it doesn't work reinstall rather than trying to find a solution.

---

### Post by cb34 on 2008-12-31
i completely agree with you and i am a mental freak ranting all the time about exactly that point, how in linux you dont ever have to just reinstall or reboot, and that's why i purged winxp from my drive and love anything linux, but sometimes when it comes to things like nvidia main drivers, and main programs like xorg, i've found it to be simpler and pretty smooth to just reinstall these things.. but i completely am with you man, i dont know why im just going along and giving instrictions to purge and not helping all the way to figure out the problem.. im just not that good yet i guess, and i know it.. hehe you're so right Ender41 man.
i'll calm down with the purging. :p

---

### Post by tropdoug on 2009-01-01
well I checked th logs, couldn't see anything obvious, tried a few little tricks here and there, but all to no avail. so yes I succumbed and reinstalled. (I know it's the easy way out, but hey I am still learning LOL)

Anyway thanks for the help

---

