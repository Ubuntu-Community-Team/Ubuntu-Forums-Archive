---
title: "Need help accessing external hard drive."
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Machdonneld on 2010-01-17
Hi
I just recently installed Ubuntu (9.10 as far as i'm aware) and i cannot seem to access my backed up data on my WD MyBook Elite external hard drive.
I plug the drive in and an icon appears on the desktop yet I cannot seem to access my files. whilst using the drive to backup when i still had windows the drive had its own interface software, could this be the problem?
Any help is welcome as i am completely stumped and a bit of a novice when it comes to intricate computer language.
thanks.

---

### Post by Ozitraveller on 2010-01-17
Do you know whether the external drive in is formated FAT or NTFS?

If you double click on the icon on the desktop what do you see?

---

### Post by Machdonneld on 2010-01-17
I do not know if it is either, how would i find this out?
When i click on the icon i get a window showing two .exe files; unlock and WD SmartWare 3 folders; user manuals, WD SmartWare and user manuals, also there is a html file and a .inf file named autorun.

---

### Post by warfacegod on 2010-01-17
I suspect your folders might be hidden try hitting:

Ctrl+H when in the drive.

---

### Post by Machdonneld on 2010-01-17
this didn't reveal any hidden files.
after a bit of research I have a feeling the problem is something to do with the MyBook's virtual cd that loads up the backup interface, apparently its only usable with Mac/Windows OS.
Does this sound plausible?

---

### Post by warfacegod on 2010-01-17
Yes I do. I think the easiest solution would be to plug the drive into a Windows machine and use the software to "unpack" your backups onto the external. Be certain to "Remove Hardware Safely" from Windows When You are done. Failing to do so can cause headaches on its own in Linux.

---

### Post by mvsuperhero on 2010-02-05
Similar problem with me as well.  I own the exact same drive (the WD passport elite), but I had been using it on linux (Ubuntu 9.10) just fine up until yesterday. In the past, when I plugged in the drive I'd get an icon for the WD smartware along with another hard drive icon. Yet, for some reason today, I do not get the icon for the hard drive anymore. Just the WD smartware icon, which is useless for linux and can't be run through Wine. Any tips?   :sad:

BTW, running on an HP Pavilion dv6000 w/2G ram and 60G HD. Two external hard drives, one Verbatim 1TB (working just fine) and the other is the Passport 750G (which isn't working).

---

### Post by mvsuperhero on 2010-02-05
;) The irony is that I just put a Virtual Machine for Windows XP on that WD Passport drive last night (through VirtualBox OSE) using my linux computer. I could access the WD smartware through the Virtual Machine... but the Virtual Machine is on the hard drive which is no longer working.

... if all else fails, I'll just put a new VM on the Verbatim drive and use it to access the WD drive... but I'd rather not since that's very tedious.

---

### Post by nhasian on 2010-02-05
I dont know if the virtual disk (western digital smartware) will prevent you from using the drive in ubuntu.  i bought two external usb western digital drives this christmas and i promptly got rid of the smartware as soon i discovered it.  Its an easy two step process.  1) make sure you have the latest firmare, 2) remove the smartware with the provided app.

[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

---

### Post by mvsuperhero on 2010-02-06
Whoohoo! Nhasian, thanks! I took my passport drive to my wife's computer (she runs windows 7), and followed the steps in the link you sent. I installed all the software from the virtual disk onto her computer, then disabled the virtual disk through the VCD management program (once again, thanks for that link). Then I took the drive back to my computer, and after a restart, worked like a charm in Ubuntu. Thanks for taking the time to help.

---

### Post by MaiKeth on 2010-02-15
Yes, thank you so much for that link. I too was having issues with my wd passport not working in ubuntu because of the smartware. I followed the instructions in windows and it worked like a charm.

---

