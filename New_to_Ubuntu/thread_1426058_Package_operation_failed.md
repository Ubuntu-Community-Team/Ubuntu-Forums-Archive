---
title: "Package operation failed"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by JohnJD on 2010-03-09
I just installed ubuntu (9.1) on my desktop. Everything seemed fine at first--I was able to install wine from the software center and run FF. Then I installed some updates and now Fire Fox won't work. Also, everytime I try to download or remove something with the software center, I get a "Package operation failed" with the details: 
 
installArchives()failed: Selecting previously deselected package [program name]. (Reading database ... dpkg: unrecoverable fatal error, aborting: files list file for package 'ure' is missing final newline.
 
??? I am stumped. (Also, I am new to ubuntu/an idiot, so any explanation in the most dumbed down way would be helpful. Thank you.)

---

### Post by Miljet on 2010-03-09
Are you saying that you installed Wine and are running Firefox under Wine? If so, why? Firefox is part of the basic Ubuntu install.

You can try the following command in a terminal,  Applications -> Accessories -> Terminal
```
dpkg --configure -a 
```

If that does not work, post the contents of your sources.list file.
```
cat /etc/apt/sources.list
``` Copy and post the results here.

---

### Post by JohnJD on 2010-03-09
Sorry, I meant that I was using firefox in addition to being able to download stuff through the software center--not using firefox through wine.  Now FF will kind of start but then nothing will pop up after a few seconds of the circle thing.  Everytime I try to download something in the software center, I get that error message.
 
Here is what came out of the terminal:
 
For dpkg --configure -a, I got "dpkg: requested operation requires superuser privilege"
 
For cat /etc/apt/sources.list, it said "# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - release i386 (20091028.5)]/ karmic main restricted..."
 
And then some stuff about N.B. softwar from this repository and uncomment the following two lines to add software from the 'backports'.  I can't copy and paste the whole thing since I don't have a usb card on me at the moment.

---

