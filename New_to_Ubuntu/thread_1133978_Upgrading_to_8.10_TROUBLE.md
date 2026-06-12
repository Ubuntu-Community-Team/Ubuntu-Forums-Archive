---
title: "Upgrading to 8.10 TROUBLE"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by MikesGuitar on 2009-04-23
Hey guys, heres to deal:
I typed 'update-manager -d' into terminal and run app. The first time I did this, update manager said there was a new release I could upgrade to (8.10, i have Ubuntu 8.04). I clicked upgrade to see what would happen. It starts to do some preliminary stuff, then stated it could take up to two hours to upgrade. I did not have to battery power to wait that long so before it began I canceled. Now when I do the same thing again, nothing comes up in my update manager. Before I closed my comp the update manager siad somehting like 615 updates available, now it just says im up to date. I really want to get 8.10 so i can move up to 9. Any suggestions?

---

### Post by anjilslaire on 2009-04-23
Download the 9.04 iso, and do an install from the cd. Much quicker.

---

### Post by AXeS on 2009-04-23
> **anjilslaire said:**
> Download the 9.04 iso, and do an install from the cd. Much quicker.


Fresh-install or just ugrade?

---

### Post by anjilslaire on 2009-04-23
Either, I believe.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
> 
Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download the alternate installation CD
   2.

      Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
          *

            If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

           ```
 sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0 
```

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"


---

### Post by markharding557 on 2009-04-23
just fresh install from cd

---

### Post by raymondh on 2009-04-23
> **markharding557 said:**
> just fresh install from cd

If you do, consider also separating /home (and possibly /etc) from  /

It could save you tons of time later on.

Best of luck.

Raymond

---

