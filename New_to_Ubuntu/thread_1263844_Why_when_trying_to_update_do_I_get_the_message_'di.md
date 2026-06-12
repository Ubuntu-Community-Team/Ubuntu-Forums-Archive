---
title: "Why when trying to update do I get the message 'disk full'"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by bwallum on 2009-09-11
Hi

I have been without Broadband for about 3 months. I'm now enabled and tried to update my system. I have received the message:
> The upgrade needs a total of 274M free space on disk '/'. Please free at least an additional 274M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I have run sudo apt-get clean. The system drive is one of 3 drives (640GB, 160GB and 80GB). The system drive is 80GB of which about 10GB is used. When I run Disk Usage Analyser it reports all mounted drives in total and then says that the filesystem is 78GB. I also have a usd external drive attached (320GB).

Why does Ubuntu give me the above message when the system drive has about 60GB+ free?

---

### Post by philinux on 2009-09-11
Try

df -h

also see this.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by bobbhs77 on 2009-09-11
i have a problem connecting to a server, can someone help? i registered at mydisk.se and am trying webDAV with  [https://mydisk.se/bobbhs.shared](https://mydisk.se/bobbhs.shared) as tne server name. i'm using only the correct username but get the message:Ort »davs://bobbhs.shared@https//mydisk.se/bobbhs.shared« konnte nicht angezeigt werden
HTTP-Fehler: Cannot resolve hostname

---

### Post by philinux on 2009-09-11
> **bobbhs77 said:**
> i have a problem connecting to a server, can someone help? i registered at mydisk.se and am trying webDAV with  [https://mydisk.se/bobbhs.shared](https://mydisk.se/bobbhs.shared) as tne server name. i'm using only the correct username but get the message:Ort »davs://bobbhs.shared@https//mydisk.se/bobbhs.shared« konnte nicht angezeigt werden
HTTP-Fehler: Cannot resolve hostname

This has nothing to do with the posters fault. Please start a thread of your own. No one would find your problem buried in here. :P

---

### Post by bobbhs77 on 2009-09-11
sorry new here, i hadn't found the start thread button. thanks for the quick reply

---

### Post by bwallum on 2009-09-11
Hmmm, the diversion didn't help the fix either! I have tried to locate files as advised. I found 50GB in 'Simple Backup' files although these were on another hard drive. I found 10GB on a root trash folder. I have removed 'Simple Backup' and tried to remove residual back up files using sudo nautilus. I tried to remove the root trash files in a similar fashion. The files kept coming back. sudo as root is not the all powerful thing I thought it was.

Having found the files how do I get rid of them?

EDIT: Here is an example of what is happening (see screenshot). I am using an external hard drive with Ubuntu to try and fix my 'no space left' internal hard drive "disk-1".

When I use sudo nautilus and delete trash files they are simply replicated adding a .2 to the file name.

How do I get past this?

---

### Post by bwallum on 2009-09-11
Firstly, in answer to my question, concentrate on what you are doing. The How to from phillnux is good but not dingbat proof so use **gksudo** in front of nautilus. Once in nautilus, working as root, then right click on an offending file and with the **shift key** pressed down select move to deleted items folder. You will be presented with a dialogue that says the system can only delete the file so choose delete.

---

### Post by mapes12 on 2009-09-12
This may help: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by Malta paul on 2009-09-12
If it any help their are two trash bins, one in root:
/root/.local/share/trash
and one in your home folder:
/home/~/.local/share/trash

The root trash bin is not emptied from the desktop, because its in root. You can use Alt+F2 > Gksudo nautilus (caution you are now in permanent root)
:D

---

### Post by bwallum on 2009-09-12
> **mapes12 said:**
> This may help: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Indeed it does, another very good guide to unclogging hard drives.

Thanks, bob

---

