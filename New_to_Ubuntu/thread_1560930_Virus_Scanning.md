---
title: "Virus Scanning"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by corncob on 2010-08-25
I'm attaching a screen shot of my gparted.  What does that triangle and ! on sda2 mean?  Its the Win Vista partition and is infected with viruses.  I noticed it because I tried to run KlamAV on it from Ubuntu but the virus scanner doesn't see the partition.  'Information' in the drop down menu says its unmounted but there is no 'mount' selection, only a ghosted out 'unmount'.

---

### Post by howefield on 2010-08-25
> **corncob said:**
> What does that triangle and ! on sda2 mean?  

Means you have the partition mounted, so GParted cannot work with it, beyond represent it in the graphic.

---

### Post by Rinzwind on 2010-08-25
if you want to know that that warning is about have a look at the details of that partition (click the partition). You get a lengthy explanation of the partition. Mostlikely that partition has bad sectors or is mounted.

Example of some one elses g-parted:

[http://ubuntuforums.org/attachment.php?attachmentid=97165&d=1229889335](http://ubuntuforums.org/attachment.php?attachmentid=97165&d=1229889335)

---

### Post by Rubi1200 on 2010-08-25
Are you running GParted from within Ubuntu (meaning you installed it and are displaying the results from the install not the LiveCD)?

---

### Post by corncob on 2010-08-25
Something definitely is wrong with the windows partition, like its loaded with viruses and I can't do anything in it.  Fortunately my wife had let me install Ubuntu a while back so I can use the computer with that.  (Ubuntu is on the same drive as windows -- dual booting).  The triangle and ! are now gone and replaced by keys meaning its mounted (on /).  The info file is not as long as before (I should have taken a screen shot then) but says nothing spectacular now.   KlamAV or the File Manager still don't see the partition.  Something to do with being mounted on /?  I can't seem to unmount it either with gparted or pysdm.

---

### Post by Rubi1200 on 2010-08-26
It is highly unlikely that you have viruses on the partition.

I understand that you are being cautious, which is to be expected when you encounter something you do not have an explanation for, but there is probably a more basic reason behind this.

The yellow warning triangle is GParted telling you there is something wrong with the partition; most likely bad sectors or something similar.

I suggest you boot into Windows and run a chkdsk:

[http://www.windows-help-central.com/windows-vista-chkdsk.html](http://www.windows-help-central.com/windows-vista-chkdsk.html)

---

### Post by corncob on 2010-08-26
> **Rubi1200 said:**
> It is highly unlikely that you have viruses on the partition.

I understand that you are being cautious, which is to be expected when you encounter something you do not have an explanation for, but there is probably a more basic reason behind this.

The yellow warning triangle is GParted telling you there is something wrong with the partition; most likely bad sectors or something similar.

I suggest you boot into Windows and run a chkdsk:

[http://www.windows-help-central.com/windows-vista-chkdsk.html](http://www.windows-help-central.com/windows-vista-chkdsk.html)

Thanks.  I'll work on it from that angle but I have to go on errands right now.  Thing is, I can't seem to do anything in Windows:  Windows keep popping up saying I have a virus and programs won't start because it says they're infected.  I succeeded in mounting the partition and Klamwin, scanning from Ubuntu, quarantined 130 files but its still the same.  I'm trying to convert my wife to Ubuntu but there are programs she uses in Windows.

---

### Post by Rubi1200 on 2010-08-26
> **corncob said:**
> Thing is, I can't seem to do anything in Windows:  Windows keep popping up saying I have a virus and programs won't start because it says they're infected.  I succeeded in mounting the partition and Klamwin, scanning from Ubuntu, quarantined 130 files but its still the same.

This you did not mention before! This makes things different. 
1. do you have an antivirus program installed in Windows?
2. have you tried booting Windows in Safe Mode and running a scan?
3. have you looked at these options? 
[http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/](http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/)
You can use the antivirus programs on a LiveCD to clean a Windows infection.
4. do you have the Windows installation CD?
5. have you been backing up regularly?

---

### Post by corncob on 2010-08-28
I didn't disappear, just been working on getting Ubuntu set up for my wife.  The big problem is that print shop, version 20 or 21, won't install with wine.
Ubuntu is installed on the same drive and is working fine.  I copied all her pictures, documents, etc into it from windows.  I had installed Clamwin in windows but it has disappeared.  I ran Windows defender in safe mode and it found nothing but I had already run Klamav from Linux and it had moved 130 files into quarantine.  Windows Defender was disabled from running in the background and I couldn't enable it.  Now I can't even start it.  I did try one of those things in the link you gave me but it didn't seem to do anything.

---

### Post by DrMelon on 2010-08-28
Sounds like you've got rogue antivirus stuff on there popping up false warnings, etc.
If you can boot into safe mode, run "Malwarebytes Anti-Malware". It's a very thorough malware scanner. Saved me many times in the past.

---

