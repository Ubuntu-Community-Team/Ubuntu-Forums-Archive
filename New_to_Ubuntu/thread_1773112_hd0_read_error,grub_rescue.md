---
title: "hd0 read error,grub rescue"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by konsolelover on 2011-06-01
hello everyone i just need some serious help...wen i booted my lap with ubuntu 11 installed just saw flashing cursor for a long time then i got the error hd0 read error grub rescue

---

### Post by konsolelover on 2011-06-01
i think my hard disk is crashed..pls help i dont want 2 lost my data

---

### Post by Rubi1200 on 2011-06-01
Hi,
please do the following so we can get a better overview of the system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by konsolelover on 2011-06-04
thanks Rubi 4 ur help...i tried to run ubuntu 11.04 from liveusb after getting boot menu, tried to select to run from usb and install ubuntu ..and both didn't work nd got the error..
When i tried ls command in rescue prompt got the result hd0 , (hd0,msdos6),(hd0,msdos5),(hd0,msdos4),(hd0,msdos3),(hd0,msdos1)
wen i tried ls (hd0,msdos5) got the read error and wid other ones got the unknown file system error.
 I want to tell that i was using win7 then i formatted the drive and installed ubuntu after partitioning that drive 10 days b4

---

### Post by konsolelover on 2011-06-04
Error while runnin live cd was i got struck to the black screen wid msgs ata3.00:
exception emask 0x0 sAct 0x3 sErr0x0
ata3.00:failed command:FPDMA QUEUED
 cmd 60/08...
Status: DRDY ERR
ERror:UMC
configured for UDMA/100
EH COmplete

---

### Post by Rubi1200 on 2011-06-04
Hmm, this could indicate some kind of hardware failure.

Another suggestion is to download and run Slax as a LiveCD. I have seen people have success with that when the Ubuntu CD did not work for some reason.

If you can boot the computer then first try and save any important data and then run the boot script (no need for sudo because Slax uses a root terminal).
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

---

### Post by konsolelover on 2011-06-04
@Rubi thnx 4 the msg finally it has started booting but now it got struck at ubuntu logo screen(still watching) for over 15 mins..wht should i do now?i tested it 4 hard disk test nd it got failed..should i try to install ubuntu on usb(does it make sense at dis case?). ma prob is dat i have only single computer.shud i try windows?my lap is in warranty but it will take atleast a month to replace hd..plz recommend me somethìng

---

### Post by Quackers on 2011-06-04
My best guess would be that your hard-drive has died. If it is under warranty I suggest that you don't do anything but return it for repair. You don't want to do anything that would invalidate the warranty.

---

### Post by Rubi1200 on 2011-06-04
After some more searching, I tend to agree with Quackers that either the HDD is failing or there is some kind of serious error related to a possible bug report on Launchpad.

In any event, I suggest you take it whilst still under warranty and have it looked at.

---

### Post by konsolelover on 2011-06-04
thanx 4 ur msgs! I guess i shud give it to service centers 4 replacement bcoz tyr is only 3 months r left in my extended warranty (3 yrs) period. I think even if i get temporary solution wid slax or my windows recovery cd ,i will most probably face the problem again in fewer time.but gotta try them anyways bcoz i need my data and i dont have backup..

---

### Post by Quackers on 2011-06-04
I know it's not convenient, but it's better if you can get a new hard drive now! Much cheaper :-)

---

