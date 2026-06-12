---
title: "Ubuntu Studio wifi drivers not working."
date: 2016-03-11
forum: Networking &amp; Wireless
---

### Post by squirrel3 on 2016-03-11
Hi all,

So, I'm giving Ubuntu Studio a whirl. Installed just fine alongside my Win7. Only problem is, I can't seem to get around the wireless driver issue, I don't have ethernet connection at the moment. Is there a way to install it directly from the ISO cd, or can I download my version? Thanks in advance for any help.

By the way here's my Broadcom version:
> 
lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)



[B]Solution:
[/B]
If no wired connection exists, sometimes this works. From LiveCD, go to:
Sytem > Admin > Synaptic Package Manger
Ensure CD rom is in the drive
From Synaptic Package Manager, open Settings > Repositories > Ubuntu Software
Check "Installable from CD-ROM/DVD" option and finally close. Simply reload and disregard connectivity errors.
Search for "bcmwl-kernel-source"
Right-click and mark for installation
Apply changes and reboot

---

### Post by Hadaka on 2016-03-12
hi your card BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) per this guide..
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
performs best with the b43 driver.

To load the b43 driver with no internet access, first drag and drop the attached 
b43 zip file to the Desktop. Then at the b43 zip icon on the Desktop 
>right click then choose > Exrtract Here.
Next open a terminal...ctrl/alt/t..then please copy and paste one line at a time.
ignore any error or file not found on the first two commands.
This removes the bcmwl-kernel-source driver if it was installed by error or default.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
Then to install the b43 driver, please copy and paste..
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe b43
```

boot 

* Attached Zip File *
[ATTACH=CONFIG]267779[/ATTACH]

---

### Post by glassbender101 on 2016-03-12
Thank you all very much your help was excatly what I needed

---

### Post by squirrel3 on 2016-03-12
Thanks, great solution.

---

