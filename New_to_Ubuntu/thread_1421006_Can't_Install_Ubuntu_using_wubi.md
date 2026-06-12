---
title: "Can't Install Ubuntu using wubi"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by msa34 on 2010-03-03
I have an issue with Ubuntu 9.10.
After installing Ubuntu 9.10 using wubi inside windows 7 and it was working perfectly, but while I was working on Ubuntu the computer freezing and I had to shutdown my PC, but when I tried to start Ubuntu I couldn't and my PC light flashed and freezing. So, I ran windows 7 and deleted Ubuntu manually and installed it again using wubi, but after restarted my computer I didn't see Ubuntu option and windows 7 started directly.
So, I tried to uninstall Ubuntu once again using wubi but I couldn't and got this

[IMG]http://lh4.ggpht.com/_K2fjZlCLW0k/S47xB45-YxI/AAAAAAAACx4/ZaLP1F2rkgI/Capture-4.jpg[/IMG] 

Any suggestion!!

---

### Post by collinp on 2010-03-03
My very general guess is that something was corrupted during the installation of Ubuntu through Wubi. If you could describe more upon how you "manually" removed it, that will help a lot.

---

### Post by lidex on 2010-03-03
Manual uninstall:
> Remove C:\ubuntu and C:\wubildr*

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block.

To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

An easy method of removing this registry key is to paste the following text into a plain editor such as Notepad, close and save the file as something like removeWubiKey.reg (you may wish to go to Folder Options > View and disable the "Hide file extensions for known file types" option to check that the .reg extension has been applied correctly). Then you can perform the rest automatically by opening the file in the normal Windows manner, or choosing the "Merge" option from the right click context menu. Note: The formatting is rather strict, so copy the text exactly for best results. You may need to be logged in as the administrator to delete the key, depending on the version of Windows you are using. User Account Control in Vista may also ask for permission, in the typical fashion.

REGEDIT4

[-HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]

After deleting the registry key, Ubuntu may still appear in the program list. If this is the case, you may be asked if you would like to remove the item from the list.



From this page:
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

Can't boot ubuntu:
> Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into Windows, run chkdsk /r from Windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.

Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. If you do not see those, look for found.000. You need to change the Windows Explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location.

Make sure you did not install on a RAID array or in an encrypted disk. Also make sure you did not install using an Alternate or DVD ISO. 

---

### Post by msa34 on 2010-03-03
> **Hellow said:**
> My very general guess is that something was corrupted during the installation of Ubuntu through Wubi. If you could describe more upon how you "manually" removed it, that will help a lot.

Hi
Actually, I didn't use wubi to remove Ubuntu instead I deleted Ubuntu folder from my drive.

---

### Post by msa34 on 2010-03-03
> **lidex said:**
> Manual uninstall:


From this page:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Can't boot ubuntu:

Works perfectly.:D
You saved me

Here is the solution.
Open regedit
search for wubi
delete everything related to it
uninstall ububtu using wubi
install it again, and done.

Piece of cake.

Thanks a lot.

---

### Post by lidex on 2010-03-03
> **msa34 said:**
> Works perfectly.:D
You saved me

Here is the solution.
Open regedit
search for wubi
delete everything related to it
uninstall ububtu using wubi
install it again, and done.

Piece of cake.

Thanks a lot.

No problemo. If you would be so kind as to mark the thread solved, it would help others with same problem.(Use thread  tools at top of page)

---

