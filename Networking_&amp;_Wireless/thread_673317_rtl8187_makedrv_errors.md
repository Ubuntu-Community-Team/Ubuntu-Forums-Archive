---
title: "rtl8187 makedrv errors"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by shoppy123 on 2008-01-20
I am trying to get the aircrack-ng suite to work with my rtl8187 driver. I have got it to work before using PCLOS so I know it is possible. I know what the problem is I just don't know how to fix it. I follow the directions on this page [http://www.aircrack-ng.org/doku.php?id=r8187&s=rtl8187](http://www.aircrack-ng.org/doku.php?id=r8187&s=rtl8187) and when I run ./makedrv after running sudo make install I get the error message "INIT_WORK" passed 3 arguments, but takes just 2.
The solution on that page is "Solution: This typically occurs after you have upgraded your kernel version. Delete the all the patch files and install a fresh version. You should now be able to compile it successfully. Also ensure that you have matching kernel header files." I am stuck because I have not upgraded my kernel version. I have a fresh install of gutsy. But the second part is interesting and it says to make sure I have matching kernel header files. The only problem is I don't know how to check that. I need help. Any suggestions on making this work?

---

### Post by kevdog on 2008-01-20
sudo aptitude install linux-headers-`uname -r`

Copy and paste that command into the terminal for the header files.

---

### Post by shoppy123 on 2008-01-20
Still get the same error. I think that it just won't work on gutsy

---

### Post by kevdog on 2008-01-20
where did you get the rtl8187 driver?  Are you working with a pci or usb device?  This chipset is problematic for many and there are many different drivers floating around.

---

### Post by shoppy123 on 2008-01-20
I downloaded it from the url in my first post. And after searching around some more I found this very interesting post. [http://ohioloco.ubuntuforums.org/showpost.php?p=3031478&postcount=14](http://ohioloco.ubuntuforums.org/showpost.php?p=3031478&postcount=14) It gives a lot of insight into the kernel and why it doesn't work. It looks like quite a bit of editing is going to need to be done. I'm going to begin looking into it and hopefully I'll be able to get this going on gutsy.

---

### Post by kevdog on 2008-01-20
Good find -- and good luck!

---

