---
title: "lost my ntldr!!!!!! help!!!!!!"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by joelrstevens on 2009-09-06
installed ubuntu on my laptop. lost my ntldr to vista!!!! if i try to boot into it, it tells me it is not found and prompts me to ctrl>alt>delete
how do i get it back???????

---

### Post by coldReactive on 2009-09-06
This thread might help:

[http://ubuntuforums.org/showthread.php?t=983476](http://ubuntuforums.org/showthread.php?t=983476)

---

### Post by joelrstevens on 2009-09-06
i don't have a recovery cd! do i have any other options. my recovery drive was on my 2nd partition. i can't access that either

---

### Post by jimingkui on 2009-09-06
This might what you need:
[http://ubuntuforums.org/showthread.php?p=5082723#post508272]("http://ubuntuforums.org/showthread.php?p=5082723#post5082723")3

---

### Post by pedro3005 on 2009-09-06
More specifically, this:
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)

---

### Post by joelrstevens on 2009-09-06
concernig step 1 which states the following:
**Step 1) Mount your windows partition in Linux**


 	Code:
 	sudo mkdir /Win
sudo mount /dev/sda5 /Win    
ls /Win 
(here /dev/sda5 must be replaced by the device name of your Windows partition. Use "sudo fdisk -l" to determine the device name)

The last command lists all the files in the System directory of your Windows Partition. Look for the files "boot.ini", "NTLDR" and "NTDETECT.COM". If you already have these files, skip Step 2.


ok....... i did the sudo fdisk -l command and got this:


 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       46630   374554451    7  HPFS/NTFS
/dev/sda2   *       46956       48641    13541376    7  HPFS/NTFS
/dev/sda3           46631       46955     2610562+   5  Extended
/dev/sda5           46631       46933     2433816   83  Linux
/dev/sda6           46934       46955      176683+  82  Linux swap / Solaris


How should my code look next?????

---

### Post by Bodsda on 2009-09-06
> **joelrstevens said:**
> concernig step 1 which states the following:
**Step 1) Mount your windows partition in Linux**


 	Code:
 	sudo mkdir /Win
sudo mount /dev/sda5 /Win    
ls /Win 
(here /dev/sda5 must be replaced by the device name of your Windows partition. Use "sudo fdisk -l" to determine the device name)

The last command lists all the files in the System directory of your Windows Partition. Look for the files "boot.ini", "NTLDR" and "NTDETECT.COM". If you already have these files, skip Step 2.


ok....... i did the sudo fdisk -l command and got this:


 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       46630   374554451    7  HPFS/NTFS
/dev/sda2   *       46956       48641    13541376    7  HPFS/NTFS
/dev/sda3           46631       46955     2610562+   5  Extended
/dev/sda5           46631       46933     2433816   83  Linux
/dev/sda6           46934       46955      176683+  82  Linux swap / Solaris


How should my code look next?????

Not entirely sure which one houses your system files but if you do
```

sudo mkdir /media/win
sudo mkdir /media/win2
sudo mount /dev/sda1 /media/win
sudo mount /dev/sda2 /media/win2

```
Then check which one is which.

Hope this helps,
Bodsda

---

### Post by joelrstevens on 2009-09-06
my system is in sda 1  what should my code look like now?

---

### Post by Bodsda on 2009-09-06
> **joelrstevens said:**
> my system is in sda 1  what should my code look like now?

Well, follow the instructions with the knowledge that your system files are now located at /media/win (assuming you followed my mounting instructions)

Without knowing which guide you are following I can't help much more then that.

Kind regards,
Bodsda

---

### Post by bumanie on 2009-09-06
Vista does not use ntldr as part of it's booting files, previous versions of windows did (you must have previously had xp or 2000 on your computer and the MBR still has some old boot files left). may be read [this]("http://binaryday.com/2009/02/16/how-to-fix-ntldr-missing-error-in-vista/") Or go to [here ]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")and download a vista repair cd and use it. It works well.

---

### Post by joelrstevens on 2009-09-06
great!!!! what is a good iso burner that works with ubuntu????

---

### Post by coldReactive on 2009-09-06
> **joelrstevens said:**
> great!!!! what is a good iso burner that works with ubuntu????

Brasero is installed by default in Ubuntu. :| Under Sound & Video in the Applications menu.

---

### Post by bumanie on 2009-09-06
Once you download from neosmart, right click on the .iso and choose 'write to disc" - Nothing more.

---

### Post by joelrstevens on 2009-09-06
ok..... isee ubuntu has its own iso burner........what is a good bit torrent program for ubuntu to extract the iso?

---

### Post by coldReactive on 2009-09-06
> **joelrstevens said:**
> ok..... isee ubuntu has its own iso burner........what is a good bit torrent program for ubuntu to extract the iso?

Applications > Internet > Transmission

---

### Post by joelrstevens on 2009-09-06
thanks!!! what is a good torrent file program for ubuntu to extract the iso?

---

### Post by presence1960 on 2009-09-06
before you make any major removals or additions to your current set up we need to know EXACTLY what your setup & boot process looks like. Boot into Ubuntu and do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

If you can't boot into ubuntu then do this:

Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

**P.S. no one even thought of looking at your windows entry in menu.lst. if it is pointing to the wrong partition you can get that type of error. Run the script as that info is included in the output as well as everything else about your setup**

---

