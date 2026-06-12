---
title: "Upgrading to Jaunty"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by alket on 2009-04-23
Does upgrading in Jaunty erases my files ?

---

### Post by anjilslaire on 2009-04-23
in-place upgrades, no.
Clean install, yes if you don't have a separate /home partition.

---

### Post by alket on 2009-04-23
thanks, now I have a new question
I downloaded 9.04 and I burned it on CD, how can I upgrade it in 8.04 ?

---

### Post by cariboo on 2009-04-23
Short answer, you can't. In order to update from 8.04 to 9.04 you need to update to 8.10 first. the upgrade path would be 8.04.2-->8.10-->9.04.

---

### Post by anjilslaire on 2009-04-23
It appears they recommend using th alternate cd to do disc-based upgrades
[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)
> 
Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download the alternate installation CD
   2.

      Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
          *

            If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:

            sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0

   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"


At least you can download the alternate ISO and do the upgrade without burning a new cd.

---

### Post by anjilslaire on 2009-04-23
> **cariboo907 said:**
> Short answer, you can't. In order to update from 8.04 to 9.04 you need to update to 8.10 first. the upgrade path would be 8.04.2-->8.10-->9.04.

He didn't mention using 8.04, and his profile lists 8.10. It should be fine.

---

### Post by phantom3113 on 2009-04-23
If you downloaded and burned a cd, all you have to do is insert it and install to upgrade.

---

