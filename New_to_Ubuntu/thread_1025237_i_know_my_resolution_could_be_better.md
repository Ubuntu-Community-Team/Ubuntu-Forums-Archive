---
title: "i know my resolution could be better"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by adamogardner on 2008-12-29
one day my graphics took a dump and one of you called me up and remotely talked me through the proceedure of finding my graphics card and resolving my screen to something really sharp.  Now my options for screen resolution in my preferences menu does not offer (again) the highest resolution that my graphics card is capable of.  Because I did it last time over the phone, I have no record of the steps I took to 1 identify my card, 2 use my card or have it's potential listed in the options menu.

thanks

---

### Post by taurus on 2008-12-29
```
lspci | grep VGA
```
Look in System -> Administration -> Hardware Drivers to see if your graphic card is listed there.

---

### Post by Raynman37 on 2008-12-29
If you go to *System > Administration > Hardware Drivers* are your graphics drivers all up to date and activated?

EDIT: pfff, Taurus types faster :P

---

### Post by adamogardner on 2008-12-29
it's a nvidia driver, the box is checked and is 'in use'.  I also update/upgrade my system regularly.

---

### Post by Raynman37 on 2008-12-29
Last time you did this, did you have to edit your /etc/X11/xorg.conf file?  I found some people talking about that here:

[http://www.linuxquestions.org/questions/ubuntu-63/screen-resolution-584353/](http://www.linuxquestions.org/questions/ubuntu-63/screen-resolution-584353/)

---

### Post by adamogardner on 2008-12-29
'x.org' sounds familiar.

---

### Post by Raynman37 on 2008-12-29
I would take a look at this thread here:

[http://ubuntuforums.org/showthread.php?t=803519](http://ubuntuforums.org/showthread.php?t=803519)

There are a lot of different attempts at a fix and one of them may work for you.  Also, I don't know much about editing the xorg.conf file, so I would either wait here for someone who knows more about it, or Google it to find out more, but it may come down to adding a setting in that file.

**EDIT:** Check here:

[http://www.linux.com/feature/118108](http://www.linux.com/feature/118108)

This seems to be a very good guide on editing the xorg.conf file.

---

### Post by adamogardner on 2008-12-30
thanks,  all of this was useful.  I fixed my graphics and have a better undeerstanding of how it works.

---

