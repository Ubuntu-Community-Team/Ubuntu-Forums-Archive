---
title: "How do I upgrade from Gutsy to Hardy or Ibex (without Internet on Ubuntu)?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by amkr on 2009-02-21
I download all my apts on my brothers XP and install them using gdebi. Can I update my Ubuntu version in a similar way?

---

### Post by sgosnell on 2009-02-21
Yes.  You can download the .iso to a Windows box, burn it to a CD, and then install it on any computer.

---

### Post by chmbrs on 2009-02-21
i think you can use an ubuntu dvd to update.

---

### Post by Mercury_Alpha on 2009-02-21
As far as I know, the standard ISO doesn't do upgrades, only full installs. If you want to upgrade, you'll need to burn an ISO of the [Alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). At least, that's what it says on the official upgrade page.

---

### Post by sgosnell on 2009-02-22
For an upgrade without direct internet connection, these are the instructions from the Ubuntu site:
> 
Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1. Download the alternate installation CD
   2. Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
          * If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:
```

            sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0

```
   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesudo "sh /cdrom/cdromupgrade"


---

