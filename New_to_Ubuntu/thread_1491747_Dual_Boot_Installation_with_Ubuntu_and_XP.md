---
title: "Dual Boot Installation with Ubuntu and XP"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by bhappyharsha on 2010-05-24
Hi,
 
I have a computer with Windows XP SP3 operating system. 160 GB Hard drive in two partitions. C drive (Windows 50 GB) and D Drive (Empty 100 GB).
I have downloaded and burnt the Ubuntu 10.4 version. Please let me know the step by step instructions to install Ubuntu on my D Drive including any pre-conditions that have to be met like disconnecting the internet etc. 
I am an absolute novice to linux operating systems.
 
Regards,
Sri Harsha.

---

### Post by oldfred on 2010-05-24
Unless you want wubi which is an install inside the windows NTFS partition as an extended test, kinda like the liveCD, you will have to delete the D: partition as linux uses different formats than windows. 

There are many dual boot instructions on the web. Windows Vista & 7 need to have partitions resized using the windows tools but if you know you do not want D: you can delete it and use the install to largest empty space choice. Different versions of Ubuntu do not vary much either. Since 9.10 new installs use grub2 which is a newer boot loader than the old grub legacy boot loader.
Otherwise just about any dual boot instructions you review will be almost the same as you see with the newest version of Lucid 10.04.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Herman has lots of examples and if anything too much info for a beginner. 
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

