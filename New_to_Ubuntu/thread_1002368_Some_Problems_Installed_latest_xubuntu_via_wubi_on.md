---
title: "Some Problems: Installed latest xubuntu via wubi on toshiba satellite 2800"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by ajfan on 2008-12-04
I have a problem with my keyboard.  When I hit shift-2, it displays " instead of @.  When I hit the key that should normally show the '', it shows @.  Can anyone help me with this?

Also, I told wubi to create a 5gig install.  After install, I only had 2.2 gig free.  After updates, I only had 1.98gig free.  Is it to be expected that xubuntu take up so much space?  Any way that I can skinny anything down to free up more room?

Lastly, one of the updates failed.  linux-image-2.6.27-7-generic fails to install.  It tries to back up but fails.  Is it to be expected that this can't update if in a wubi install?

Thank you for your help.

---

### Post by abn91c on 2008-12-04
for the keyboard go into the control center and make sure you have a USA layout, for the other in synaptic or whatever package manager you are using remove unwanted applications such as the bluetooth, palm pilot stuff, tape back up torrent and chat programs if you are not going to use them. also in a terminal d type sudo dpkg --configure -a followed by sudo apt-get install -f to try to fix the kernel issue
also do sudo apt-get autoremove to remove packages no longer needed.

---

### Post by ajfan on 2008-12-05
abn91c,
Thank you for your help.  One of the commands suggested didn't seem to work:
type sudo dpkg --reconfigure -a
sudo is hashed (/usr/bin/sudo)
dpkg is /usr/bin/dpkg
bash: type: --reconfigure: not found
bash: type: -a: not found
I tried it removing the "type" and also removing one of the - in front of reconfigure and it didn't seem to work either.  
Bear with me as I am not a linux guru:)

---

### Post by Paqman on 2008-12-05
> **ajfan said:**
> I have a problem with my keyboard.  When I hit shift-2, it displays " instead of @.  When I hit the key that should normally show the '', it shows @.  Can anyone help me with this?


Looks like your keyboard is set to UK.

> 
Also, I told wubi to create a 5gig install.  After install, I only had 2.2 gig free.  After updates, I only had 1.98gig free.  Is it to be expected that xubuntu take up so much space?  Any way that I can skinny anything down to free up more room?


That's about a normal amount of space. Most Operating Systems take up a lot more. 

You can [clear out unwanted files]("http://ubuntuforums.org/showthread.php?t=140920") (such as locales you don't use) or you could simply expand the size of your virtual disk with [LVPM]("http://lubi.sourceforge.net/lvpm.html")

> 
Lastly, one of the updates failed.  linux-image-2.6.27-7-generic fails to install.  It tries to back up but fails.  Is it to be expected that this can't update if in a wubi install?


No, Wubi-installed systems update themselves like normal. The command abn91c mentioned should be:
```
sudo dpkg --configure -a
```

---

