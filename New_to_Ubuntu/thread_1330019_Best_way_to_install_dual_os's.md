---
title: "Best way to install dual os's"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by techforay on 2009-11-18
I have a desktop computer with a G: drive (windows installed) and I tried to install ubuntu "inside windows" but selected my H: drive which has more space.  I was thinking that when I reboot I should get a choice of which system to launch.  I do not it just boots windows.  I have other posts in this forum but I am trying to load ubuntu on several devices.

---

### Post by Procuro on 2009-11-18
I'm pretty sure that if you try to install Ubuntu 9.04 or earlier within Windows Vista/7, the boot loader won't work, so you won't see those options. Try putting the ubuntu iso and wubi.exe in the same folder and then try to install it. Doing it this way is less buggy (in my experience) and doesn't require you to burn it or mount it to a cd drive.

If you get the same results, you may just have to install Ubuntu in the same drive as windows, especially if you are using a usb drive. GOod luck

---

### Post by garvinrick4 on 2009-11-18
Now in WUBI the installation is a default question on installation. Just put your
CD in the tray, answer yes to WUBI give them the desired disc size for WUBI folder 
and your password click install and 12 minutes later you are installed.

Your UBuntu folder will be right next to Users in C: drive.

In Ubuntu the /host is where your windows files will be just go host/users/login name.
and drag and drop what you want to Ubuntu.

To get Linux to Windows have to copy to external drive then put in Windows.

Have a uninstall in ubuntu folder in Windows or use Add-remove programs to uninstall
if you get goofed up. Will not harm Windows installation it is like an App in Windows.

WUBI will take care of grub it attaches to Windows dos4grub and puts windows first and select ubuntu with up and down arrows and enter default 10 seconds to make up your mind or boots to Windows.

Best way to learn how to use Linux. is WUBI.  Google a lot for problems and answers
read these Forums and ask questions.

---

### Post by garvinrick4 on 2009-11-18
Here is some guides. Remember now in 9.04 and 9.10 WUBI is an option on your downloaded .iso file that you have BURNED to a CD.

Here are a few sites to look into. Good luck.  If you choose WUBI I can help quite a bit.
Other installs you are better off with someone who is experienced and knows his way
around grub2 in 9.10 and grub legacy in 9.04.  Have a good time with Linux.


[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

[Illustrated Dual Boot Site]("http://members.iinet.net.au/%7Eherman546/index.html") 

[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

