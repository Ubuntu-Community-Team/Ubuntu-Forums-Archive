---
title: "hal-mtab-lock no permissions"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Luxx on 2009-05-07
I hate to do this. I posted this in General help and it just doesn't seem to be attracting much attention. I apologize for my impatience. Please help.

I have been using my USB flash drive on Ubuntu Studio 8.10 without a problem for months and suddenly a few days ago I found a file in the media folder entitled .hal-mtab-lock with a locked symbol on it and found I could no longer write to my USB drive. I found similar problems in the following archived threads:

[http://ubuntuforums.org/archive/index.php/t-237881.html](http://ubuntuforums.org/archive/index.php/t-237881.html)
[http://ubuntuforums.org/archive/index.php/t-495306.html](http://ubuntuforums.org/archive/index.php/t-495306.html)

I have a slightly different issue now.
I cleared my USB and deleted the trash folder. I can write to the USB drive again. Everything seemed to be back to normal, but then I found that my lost+found folder in File System has the same locked symbol on it and is unreadable.

This has happened 2 more times in the last 6 days. Upgraded to Jaunty and 2 days later it happened again. It doesn't happen EVERY time I try to write to USB. I'm wondering if changing file types and transfering between Ubuntu and WinXP has anything to do with it - but I never had that problem before.

Now it has become a real problem. I tried to install the latest version of Vuze in terminal and it failed because /opt/vuze folder is not writable.

I cannot write to new folders on the flash drive (but can delete them) and can't install to File System folders using sudo in terminal.

Is this a bug? There was a hal-mtab-lock bug reported for Hardy Heron. I don't seem to find other people having this problem with Intrepid or Jaumty.

Thanks for any help or advice.

---

### Post by blazemore on 2009-05-07
Try using gPartEd:
```
sudo apt-get install gparted && sudo gparted
```

Select your USB flash drive from the drop-down menu on the right, then format the partition as FAT32 (MAKE SURE YOU SELECT THE RIGHT DEVICE!!!)

---

### Post by Luxx on 2009-05-07
> **blazemore said:**
> Try using gPartEd:
```
sudo apt-get install gparted && sudo gparted
```

Select your USB flash drive from the drop-down menu on the right, then format the partition as FAT32 (MAKE SURE YOU SELECT THE RIGHT DEVICE!!!)

Currently my lost+found folder in File System is pad-locked, and I'm having problems gaining access to folders to install things. I can use the flash drive as long as I don't create a new folder.

The problem seemed to first manfest with the USB, but the problem seems to be a disconnect in permissions on my system as a whole. When I create a new folder on my desktop or on the USB drive I cannot write to it. I aslo cannot install things on my computer such as Vuze (this has nothing to do with the USB drive).

I have tried to change permissions but the changes don't save. I was able to get Vuze to install after playing with gksudo  - after several failed tries (could not find a valid option for gksudo that would do what I wanted to do) I was finally able to set up write permissions for Vuze updates using sudo chown, which had not been working before. It took me 2 days and I'm not sure what I did, but Vuze now works. 

I'm having problems whether or not there is anything in the USB ports.

---

### Post by jacksinn on 2009-05-07
I know sometimes locking (permissions) issues occur when the USB drive is not properly removed from the system e.g. the device in Windows isn't removed without using the icon in the lower-right corner by the date display.
I suggest booting into Windows and selecting to remove the hardware then physically removing it and trying it again in Ubuntu.

---

### Post by Luxx on 2009-05-08
Thanks for the replies.

Yes, that gets the flash drive working again. Also deleting all files and folders on the flash drive on the Ubuntu computer got it to work again, but that was when my lost+found folder got locked and I started having other permissions issues on the computer, such as failed installs because I don't have permissions to write to folders.

Does anyone have any idea what I can do to get my computer to allow writing to the folders when installing as it did before, and get rid of the lock symbol on the lost+found folder ?

---

### Post by lyni on 2009-05-08
to unlock folders try right clicking on the folder, then click Properties. go to the Permissions tab and click on the drop downs there and make them all Read and Write. that usually works for me.
good luck.

---

