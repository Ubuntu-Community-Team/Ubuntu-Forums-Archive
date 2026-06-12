---
title: "delete program from terminal"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by loosescrew on 2009-08-23
I would like to remove real player. It is not listed in synaptic, or add/remove. It is located at filesystem/opt/real.I have tried sudo apt-get remove realplayer. I get the message that it is not installed.It is there any ideas how to get rid of it ? I appologize, if this is an ignorant question, but i'm new to ubuntu. Thanks Joe

---

### Post by jpkotta on 2009-08-23
First, I would check the Real Player documentation about uninstalling.  But the following will probably work.  It removes the directory that Real Player is in.  Make sure there are no typos.
```
sudo rm -rf /opt/real
```

---

### Post by Katalog on 2009-08-23
I've never installed Realplayer, but it seems odd that it didn't install anything in /usr/bin, or that it didn't register when it installed. But from Googling around, it says that if it installed itself in the /opt directory from .bin that you should run this command to uninstall:

sudo /opt/real/RealPlayer/postinst/postuninst.sh

Hope that helps.

---

### Post by 3rdalbum on 2009-08-23
Programs that are installed using binary installers (i.e. it's a program that you run in the terminal) are not recognised by Ubuntu's package management system.

There's no standard way to remove these programs, so you have to look at the documentation that comes with the program.

---

### Post by staf0048 on 2009-08-23
Have you tried ```
sudo apt-get autoremove
```  That might delete any remaining unused files left over from real player.  Not sure though.

Other than that you could use ```
sudo su root
``` and then ```
nautilus
``` to get a graphical interface and then just delete the directory entirely.  

Be careful though, that could render your system or a program unusable.  However, I have absolutely nothing listed in my "opt" directory.  Use at your own risk.

---

### Post by loosescrew on 2009-08-23
Thanks jpKotta. I will check and see if there is any info there to uninstall. If not i will run that code in terminal. Thanks Joe

---

### Post by loosescrew on 2009-08-23
Thanks, jpKotta.  That code worked. 
Katalog, 3rdalbum,staf0048, I appreciate all the help. Thanks Joe

---

