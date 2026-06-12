---
title: "booting after stoping upgradation in middle"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by sibhi on 2011-05-08
I have updated my ubuntu 10.10 and after downloading in the middle of process I switched off the system. Now I am unable to boot ubuntu. After selecting ubuntu OS it is getting stuck after displaying startup screen displaying name of the system. Mouse pointer also gettting stuck at the middle of the screen

---

### Post by speedrcj on 2011-05-08
sounds like you've probably broken some important packages.  Usually grub will offer up a "recovery mode" after updating your kernel.  IMO If it does have that, try booting into it and running "sudo apt-get update" and see if any errors pop up.

---

### Post by sibhi on 2011-05-10
Now i was able to recover my ubuntu. 
I have selected recovery mode and "e" to edit it
there replaced "ro single" with "rw init = /bin/bash
booted the system 
command prompt appeared
Typed "dhclient etho"
"apt-get dist-upgrade"
then system prompted me to type a command and gave the syntax also. i could not remember that now. But I am sure that system will prompt.
I got this by searching ubuntu forums.
Thanks for the form

---

