---
title: "Flash Problem"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by ThrashInvasion on 2009-09-11
Hi guys,im new in ubuntu,and this forum.
i experience some problems with flash player.i have downloaded the latest player(10)
as a .deb packageand installed it.when  i run synaptic package manager i can see that the 10.0.32.. version is intalled.But in flash site i see this msg ''you have 9.0.999.0 version''.also when i visit a site with live radio stream it says ''To view the content of this page, you must install the Adobe Flash Player v10.0 The version you have is 9.0.999''
.what is wrong?i have tried to reinstall it but,the problem exists...

---

### Post by gwenn on 2009-09-11
Open a terminal and copy-paste:
sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
That's all.

---

### Post by ThrashInvasion on 2009-09-11
still...I copied the command in the text editor and closed firefox.after the install it says i still have 9.0.999.0..

---

### Post by Liolikas on 2009-09-11
Ubuntu version?

---

### Post by redbob on 2009-09-11
go to /usr/lib/mozilla/plugins, delete all flash-like files and redo the installation.

---

### Post by kansasnoob on 2009-09-11
> **ThrashInvasion said:**
> Hi guys,im new in ubuntu,and this forum.
i experience some problems with flash player.i have downloaded the latest player(10)
as a .deb packageand installed it.when  i run synaptic package manager i can see that the 10.0.32.. version is intalled.But in flash site i see this msg ''you have 9.0.999.0 version''.also when i visit a site with live radio stream it says ''To view the content of this page, you must install the Adobe Flash Player v10.0 The version you have is 9.0.999''
.what is wrong?i have tried to reinstall it but,the problem exists...

No one has asked you what version of Ubuntu you're running? Or which version of Firefox?

---

### Post by SunnyRabbiera on 2009-09-11
Try adobe's website?

---

### Post by ThrashInvasion on 2009-09-12
i have ubuntu 9.04 jaunty
My Firefox version is 3.5.3

---

### Post by ThrashInvasion on 2009-09-12
ok,heres something i think might be the problem.
when i installed ubuntu the version of firefox was 3.0.14.
So I downloaded the latest version and extracted the folder in the home folder.From Then i run firefox from the shortcut with the ''firefox/firefox' command.

when i run firefox from the internet tab it loads,expect that is the 3.0.14 version.
i have checked and the version of flash is also 9.0.999.

Then i run the latest firefox version and i always see this msg:
**You should [update Adobe Flash Player]("http://get.adobe.com/flashplayer/") right now.**

             Firefox is up to date, but your current version of Flash Player can cause security and stability issues.  Please [install the free update]("http://get.adobe.com/flashplayer/") as soon as possible.

---

