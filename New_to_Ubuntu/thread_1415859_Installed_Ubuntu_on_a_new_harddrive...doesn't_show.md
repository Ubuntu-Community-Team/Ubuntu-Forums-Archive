---
title: "Installed Ubuntu on a new harddrive...doesn't show the whole harddrive in filesystem"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by fromdebal on 2010-02-25
Hi,

In this system, I used to have only one harddrive of 20 GB...and I have been using WinXp for a long time.

Recently, I got curious about Ubuntu...So bought a new harddrive of 320 GB...installed this additional harddrive and installed Ubuntu on it successfully.

Now, inside Ubuntu, when I go to "computer", I see Ubuntu OS on 5 GB filesystem (around 3.9 GB occupied & 1 GB free space) and another filesystem of 20 GB (Windows XP). Where can I find the other 315 GB (320 - 5) from inside Ubuntu?

Just for reference, if I boot with Windows XP, I can see the 20 GB drive and also the whole 320 GB drive.

Any help will be greatly appreciated.

Thanks

---

### Post by Sef on 2010-02-25
How did you install Ubuntu?

---

### Post by fromdebal on 2010-02-25
1) Loaded Windows XP
2) Installed Ubuntu from the installation CD
3) Chose the option so that I can use both the OS's.

Thanks

---

### Post by philinux on 2010-02-25
Open a terminal. Apps>access>terminal

```
df -h
```

Post back what this command shows.

---

### Post by Sef on 2010-02-25
Applications > Accessories > Terminal

Then copy and paste this code:

```
sudo fdisk -l
```then copy and paste the results here.

That code is for showing how your partitions are set up.

---

### Post by fromdebal on 2010-02-25
**df -h :**

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            3.6G  2.7G  817M  77% /
udev                  1.8G  284K  1.8G   1% /dev
none                  1.8G  340K  1.8G   1% /dev/shm
none                  1.8G   88K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda1             299G  4.7G  294G   2% /host
none                  3.6G  2.7G  817M  77% /var/lib/ureadahead/debugfs


[B]sudo fdisk -l :
[/B]
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5035f2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e700e70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2427    19494846    7  HPFS/NTFS

Thanks

---

### Post by egalvan on 2010-02-25
> **fromdebal said:**
> Hi,
Just for reference, if I boot with Windows XP, [COLOR="Red"]I can see[/COLOR] the 20 GB drive **[COLOR="Red"]and also the whole 320 GB drive.[/COLOR]**


> **fromdebal said:**
> **df -h :**

Filesystem            Size  Used Avail Use% Mounted on
**/dev/loop0  **          3.6G  2.7G  817M  77% /
**none**                  1.8G  340K  1.8G   1% /dev/shm
**none**                  1.8G   88K  1.8G   1% /var/run
**none**                  1.8G     0  1.8G   0% /var/lock
**none**                  1.8G     0  1.8G   0% /lib/init/rw
[COLOR="Red"]/dev/sda1             299G  4.7G  294G   2% /host[/COLOR]
**none**                  3.6G  2.7G  817M  77% /var/lib/ureadahead/debugfs


**sudo fdisk -l :**

**Disk /dev/sda: 320.1 GB,  bytes**  ***<--- 1st drive***
[COLOR="Red"]Disk identifier: 0xb5035f2c[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7 [COLOR="Red"] HPFS/NTFS[/COLOR]

**Disk /dev/sdb: 20.0 GB,  bytes** ***<--- 2nd drive***
[COLOR="Red"]Disk identifier: 0x0e700e70[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2427    19494846    7  [COLOR="Red"]HPFS/NTFS[/COLOR]



The highlighted, colored parts are saying that only Windows-type files systems are present on your hard drives.
Another factor is that XP cannot "see" a *nix-type file system, 
so another clue that Linux is not "installed" on the drive.

Bottom line is that you have a WUBI install,
which is Linux "inside" XP, not as a separate install.

---

### Post by fromdebal on 2010-02-25
Then how can I uninstall this Ubuntu? I want to do a fresh installation of Ubuntu on this new 320 GB harddrive.

Thanks

---

### Post by egalvan on 2010-02-25
According to the main web site..

*Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way.*


And this is the location of a FAQ, which includes "howto uninstall"

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)


I've never used WUBI, so I cannot offer any further insight.

---

### Post by fromdebal on 2010-02-27
I have uninstalled Wubi Ubuntu from Windows "Add/Remove Programs". But I am still getting Windows XP/Ubuntu option during booting. How to clean that? I want to clean everything of Ubuntu before installing fresh Ubuntu (the whole original Ubuntu) in the new partition.

---

### Post by sandyd on 2010-02-27
Run -> type in "msconfig"
its in the startup tab.
alternatively, you can show all hidden files, then edit C:\boot.ini

---

### Post by fromdebal on 2010-02-27
Thanks Carlee. Now I can see boot.ini.
 
Should I delete the line containing Ubuntu? That won't cause any problem...right?
 
Here is my boot.ini.
 
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin /usepmtimer
[COLOR=darkred]C:\wubildr.mbr = "Ubuntu"[/COLOR]

---

### Post by sandyd on 2010-02-27
> **fromdebal said:**
> Thanks Carlee. Now I can see boot.ini.
 
Should I delete the line containing Ubuntu? That won't cause any problem...right?
 
Here is my boot.ini.
 
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin /usepmtimer
[COLOR=darkred]C:\wubildr.mbr = "Ubuntu"[/COLOR]
no, it shouldnt cause problems. however, you can blame my MCITP courses if something goes wrong.

---

### Post by fromdebal on 2010-02-27
Carlee,
 
It worked. Now I am ready to install the full version of Ubuntu. 
 
Thanks

---

