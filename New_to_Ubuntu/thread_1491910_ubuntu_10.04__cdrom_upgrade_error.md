---
title: "ubuntu 10.04  cdrom upgrade error"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-05-24
i have a slow internet collection  so i decided to upgrade my ubuntu 9.10 to 10.04 using an alternate iso cd but i get the following errors pls help:confused:



[B]Could not download the upgrades

The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100317.1)]/pool/main/d/db4.7/libdb4.7_4.7.25-9_i386.deb Disk not found.
Failed to fetch cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100317.1)]/pool/main/n/ntfs-3g/libntfs-3g54_2009.4.4-1ubuntu5_i386.deb File not found
Failed to fetch cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100317.1)]/pool/main/t/ttf-kacst/ttf-kacst_2.0+mry-2_all.deb File not found
Failed to fetch cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100317.1)]/pool/main/t/ttf-vlgothic/ttf-vlgothic_20100126-1_all.deb File not found
[/B]

---

### Post by wilee-nilee on 2010-05-24
Did you check if the disc was a good download with the check disc at the choose to install window or do a md5 sum check.

---

### Post by 1991sudarshan on 2010-05-24
no i did not check

---

### Post by 1991sudarshan on 2010-05-24
is there are any other way to upgrade through cd? in the middle to the upgrade it asks for 10.04 beta cd!!!:confused:

---

### Post by wilee-nilee on 2010-05-24
> **1991sudarshan said:**
> is there are any other way to upgrade through cd? in the middle to the upgrade it asks for 10.04 beta cd!!!:confused:

I have never used the alternative cd to do a upgrade, I can't help other then to say that you want to make sure that you have a good download of the cd and that it is burned at the slowest speed possible 4x would be the most in speed. You might consider backing up what you can't lose and doing a fresh install with a CD ordered from Canonical.

If you have a very slow connection, there may a possibility of corruption of the download as well as the upgrade.

Here is a link on how to check the md5 sum on a cd.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Here is a link for ordering a free cd or dvd, I don't think that the alternative version is available though for a upgrade that keeps some things intact. I could be wrong on this though so hopefully others may know differently.
[http://www.ubuntu.com/getubuntu/purchase](http://www.ubuntu.com/getubuntu/purchase)

---

### Post by wilee-nilee on 2010-05-25
Here are some instructions on using the alternative cd and how to mount it rather then burn it. But you have to confirm you have a good download and a good burn to a cd no matter what with the links in my previous post. I am also assuming that you are familiar with upgrading and keeping your stuff.

Upgrading Using the Alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

 1. Download the alternate installation CD
 2. Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.
If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting    the ISO as a drive with a command like:

 sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0

  3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
      umcd1.png
  4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Now these instructions are to get the upgrade started, bu as I have said I haven't used this method to upgrade from 1 distro to another.

I am wondering if you didn't download the minimal cd, it should be this.
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

