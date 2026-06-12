---
title: "KArmic lost my flash drive"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Leonasha on 2009-11-29
Hi folks,

Since installing Karmic, my computer no longer sees my usb flash drive. Actually it did appear once, when I deleted the content off of it in preparation for making a usb startup disk, but it hasn't appeared since. I never had any problem in 9.04. I am sure there is some simple line of code I can enter that will mount it, but I don't know what that is.

Any help would be appreciated!

---

### Post by Redmage913 on 2009-11-29
I'd suggest plugging in the flashdrive, and running GParted.  Select your thumbdrive in the dropdown box in the top right, and see if your device is listed there.

Your device might still exist, but it isn't mounted or for some reason the file system went FUBAR on you.  If it isn't mounted, you can right-click the flash drive's partition and attempt mounting it.  If the file system went screwy, you can set up a new FAT32 partition.

If you don't have gparted, install it from the terminal using:

```
sudo apt-get install gparted
```

Hope this helps!

---

### Post by Leonasha on 2009-11-29
thanks! turns out I did need to install gparted ... but now (painfully simple question) how do I run it? it didn't start automatically on install or anything, maybe due to another problem I am struggling with ([http://ubuntuforums.org/showthread.php?p=8409328#post8409328](http://ubuntuforums.org/showthread.php?p=8409328#post8409328)).

---

### Post by wilee-nilee on 2009-11-29
Stay away from the computer janitor it removes the install cache and the install. So we don't know what all has been removed from your system by using the janitor, but a sudo apt-get install gparted in the terminal should load it, and it is in system-administration if you have not removed to many things. Some installs need to have the menu edited to tick off then on to show. Right click on applications then edit menu then administration to see if gparted shows, if it does tick it off then on.

---

### Post by Leonasha on 2009-11-29
thanks!

and for the record, the flash drive problem happened before I ran the computer janitor.

will try this out as soon as I get home.

---

### Post by wilee-nilee on 2009-11-29
> **Leonasha said:**
> thanks!

and for the record, the flash drive problem happened before I ran the computer janitor.

will try this out as soon as I get home.

With flash drive problems in my experience, I have had little problems though when I have it has been due to formatting.

I was unsure of removed stuff as far as installing gparted, I think the evil little janitor mainly removes third part stuff. I used it once and watched it remove something in whole and not just the install cache. Are you familiar with Ubuntu Tweak it is a pretty easy program for adding some native, some third part ppa's and keys and is a good cache cleaner, and has other uses as well. If you install it get the ppa version.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by k3nz13 on 2009-11-29
For the purpose of diagnostic inquiry, you could always run
```
tail -f /var/log/messages
```
To see what is happening when you insert/remove your USB drive.

---

### Post by Leonasha on 2009-11-29
> **wilee-nilee said:**
> Stay away from the computer janitor it removes the install cache and the install. So we don't know what all has been removed from your system by using the janitor, but a sudo apt-get install gparted in the terminal should load it, and it is in system-administration if you have not removed to many things. Some installs need to have the menu edited to tick off then on to show. Right click on applications then edit menu then administration to see if gparted shows, if it does tick it off then on.

gparted did not appear in System - Administration or in the edit menus option.

---

### Post by Leonasha on 2009-11-29
update - Palimpsest disk utility DOES see my flash drive! it is formatted WIN 95 FAT32 (LBA).The startup disk creator sees it too, but with a warning "!" next to it, and it does not allow startup disk creation. maybe I should reformat?

Edit: ok, I tried using Palimpsest to reformat the flash drove and got this error message:
"Error creating file system: helper exited with exit code 1: helper failed with:
init :: non DOS media
Cannot initialize '::'
mlabel: Cannot initialize drive"

---

### Post by Leonasha on 2009-11-30
well, I don't know what I did, but it worked! I have made a usb startup disk successfully, and am able to access other flash drives.  thanks for all your help!

if you feel like helping me out with my other problem, involving Computer Janitor and its impact on Adobe Air, I would appreciate it! See the link below.

[http://ubuntuforums.org/showthread.php?p=8409328#post8409328](http://ubuntuforums.org/showthread.php?p=8409328#post8409328)

---

