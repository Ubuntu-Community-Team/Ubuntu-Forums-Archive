---
title: "Help with Hydra install"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by jakester05 on 2007-02-21
Hello,

I am trying to install hydra with the GUI version, xhydra. I get this error when I do the make command:

root@jakester:/home/jakester/Desktop/hydra-5.3-src# make
cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: configure wasnt happy. Analyse this:
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: [xhydra] Error 1 (ignored)

I have no clue on why I'm getting this error...and I have no clue what GTK packages/libraries are packed with Ubuntu 6.10. Anyone out there have any ideas or thoughts???

---

### Post by real_fan on 2007-03-12
if u wanna install hydra a better option, if ur a newbie(like me), is to install it using the debian package installer.

  go to the link :
[http://blog.goukihq.org/2006/07/28/the-hackers-choice-hydra-on-ubuntu/]("http://blog.goukihq.org/2006/07/28/the-hackers-choice-hydra-on-ubuntu/")
 follow the instructions and u can double click on the package file downloaded and install it.

 Hopefully it helped u. 
p.s. i was also searching for info regarding this and luckily i found the link i told u.
  the gui for hydra is in "/usr/bin/". a binary file called "xhydra". just type the name and it will work. 
 :-({|=

---

### Post by jakester05 on 2007-03-12
Thanks for the help!!! Works great!!!

---

### Post by zilch0 on 2007-08-06
> **real_fan said:**
> if u wanna install hydra a better option, if ur a newbie(like me), is to install it using the debian package installer.

  go to the link :
[http://blog.goukihq.org/2006/07/28/the-hackers-choice-hydra-on-ubuntu/]("http://blog.goukihq.org/2006/07/28/the-hackers-choice-hydra-on-ubuntu/")
 follow the instructions and u can double click on the package file downloaded and install it.

 Hopefully it helped u. 
p.s. i was also searching for info regarding this and luckily i found the link i told u.
  the gui for hydra is in "/usr/bin/". a binary file called "xhydra". just type the name and it will work. 
 :-({|=

Great link, just thought I owed you a "thanks!" ;-)

---

