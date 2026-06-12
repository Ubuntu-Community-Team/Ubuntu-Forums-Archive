---
title: "Why so many versions"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by monkerz on 2010-06-01
I am a newbie. I have been a Windows user since windows 3.1 ....

Last year I got fed up and tried Ubuntu. Well I think the change was too much and I went back to windows.
Well its another year again and I am still so sick of Windows. So this time I will give Ubuntu a harder try. But I am so confused on where to start and why I cant understand why and what I personally am running. I see Gnome, GDE, KDE, Ubuntu and so many other things out there.  If someone can answer my questions below. Thank you for your patience and help....

1 - I have ububtu 10.04 . When I look for things to add like screensavers and change login look, what do I look for. When I follow the instructions, my screens are not the same as the instructions. Like this:

[http://www.simplehelp.net/2009/05/21/how-to-change-the-ubuntu-login-screen/](http://www.simplehelp.net/2009/05/21/how-to-change-the-ubuntu-login-screen/)

Mine says login screen . The sample shows it saying login window. Things like this make it so hard for me to learn and find things.

2 - Do I need to defrag and clean disk like windows?

Thanks for any help anyone can offer. Again I am mostly confused on what I am running and what I need to look for when adding things to my pc. Thanks

---

### Post by Ozymandias_117 on 2010-06-01
> **monkerz said:**
> I am a newbie. I have been a Windows user since windows 3.1 ....

Last year I got fed up and tried Ubuntu. Well I think the change was too much and I went back to windows.
Well its another year again and I am still so sick of Windows. So this time I will give Ubuntu a harder try. But I am so confused on where to start and why I cant understand why and what I personally am running. I see Gnome, GDE, KDE, Ubuntu and so many other things out there.  If someone can answer my questions below. Thank you for your patience and help....

1 - I have ububtu 10.04 . When I look for things to add like screensavers and change login look, what do I look for. When I follow the instructions, my screens are not the same as the instructions. Like this:

[http://www.simplehelp.net/2009/05/21/how-to-change-the-ubuntu-login-screen/](http://www.simplehelp.net/2009/05/21/how-to-change-the-ubuntu-login-screen/)

Mine says login screen . The sample shows it saying login window. Things like this make it so hard for me to learn and find things.

2 - Do I need to defrag and clean disk like windows?

Thanks for any help anyone can offer. Again I am mostly confused on what I am running and what I need to look for when adding things to my pc. Thanks

1. That's the old GDM - LOTS of people hate that they change it. It's now complicated to change your login background >.<

2. defrag, No. Clean Disk - Well, you will probably want to clear your browsers cache every once in a while, and probably run this in a terminal occasionally so you don't have useless things installed: ```
sudo apt-get autoremove && sudo apt-get autoclean
```

---

### Post by inameiname on 2010-06-01
Gnome, KDE, and etc are merely desktop environments within any Linux operating system. Ubuntu, (as well as Redhat, OpenSuse, Fedora, Debian, etc...) are what are called distributions, which are essentially entire operating systems which share one main thing, they use the same kernel, Linux, which is essentially the brains of the operating systems. And each one of the distributions implements their own code and their own design, some preferring to use Gnome, others KDE, and etc. as their desktop environments. Since we are in the Ubuntu Forums, I will tell you that Ubuntu uses the Gnome environment, however if you find you don't like it and want to try say KDE, the Ubuntu creators have made a version of Ubuntu called Kubuntu which uses it instead of Gnome. Personally, I'm fine with Gnome, and as it seems to be the most popular type, seeing as Ubuntu is the most popular Linux distribution and it uses Gnome, for a beginner it's cool.

One thing about Ubuntu and Linux in general is the increase in ability to tweak nearly everything, much more so than Windows. And for a basic user, especially a new one, it can indeed be overwhelming.

1 - As for this question, there are a number of ways to add screensavers and change the look of the login screen. Really you just need to read up on a few things which may help you. But as[ Ozymandias_117]("http://ubuntuforums.org/member.php?u=805682"), that procedure is outdated to help change it.

2 - You do not have to defrag Ubuntu or Linux like you do with Windows. It's because of how it formats the hard drive (Ext4 instead of NTFS). However, in a few cases it could get a tad fragmented based on how much is copied and pasted, but NOWHERE nearly like Windows. Thus, you have nothing really to worry about. And to keep it clean while running it, I use Bleachbit. It'll do all that [Ozymandias_117]("http://ubuntuforums.org/member.php?u=805682") said, and much more.

I would write more to help you, but I actually wrote a fair bit in this link which may help you to get started as to what might be good to install, what to tweak to better help you, and even a very good link for an Ubuntu user guide:

[http://ubuntuforums.org/showthread.php?t=1497823](http://ubuntuforums.org/showthread.php?t=1497823)

Hope that helps some.

---

### Post by marshmallow1304 on 2010-06-01
Ubuntu, Kubuntu, Xubuntu, and now Lubuntu are all basically Ubuntu but with different [desktop environments]("http://en.wikipedia.org/wiki/Desktop_environment") and default programs.
Ubuntu - [GNOME]("http://en.wikipedia.org/wiki/GNOME")
Kubuntu - [KDE]("http://en.wikipedia.org/wiki/KDE")
Xubuntu - [XFCE]("http://en.wikipedia.org/wiki/XFCE")
Lubuntu - [LXDE]("http://en.wikipedia.org/wiki/LXDE")
The desktop environment you use is a question of preference and perhaps hardware specifications as some DEs are more demanding of resources than others.  Generally, KDE > GNOME > XFCE > LXDE in terms of resources used.  There are other DEs as well, but these are the ones chosen to have official Ubuntu releases.


There are a lot of outdated howtos floating around.  There is a "Computer Janitor" utility, but you'll need to be cautious to avoid removing something unintentionally.

---

### Post by Matt__ on 2010-06-01
for a nice easy mode graphical way to tweak Ubuntu 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

click the download now button/open with package manager.
It has options to let you change your login screen, add desktop icons like in windows, clean up your system, install software and lots more.

---

### Post by monkerz on 2010-06-01
Thanks for all your fast replies. I really want to learn this and stay away from Windows. The only bad thing is I have Photoshop and Illustrator that I use on a daily basis. Is there a way to run that software on Linux?

Also thanks for the link. I will start to read up on the Ubuntu user guide link you gave me.

---

### Post by inameiname on 2010-06-01
Yeah, sure. Sorry I should've put that link also on this thread to make it easy to get to:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

As for your question, this link gives you what Windows programs seem to work well under Wine (which is a way to run many Windows Applications through Linux):

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Maybe it'll have those you want listed as compatible. Otherwise, maybe there are Linux versions of them. And if not, perhaps similar Linux applications exist, idk. Not ones I use to know for sure I'm afraid.

UPDATE:

Here are the links to those two programs, and it seems that some versions of those two apps do work under Wine in Linux well enough:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=20](http://appdb.winehq.org/objectManager.php?sClass=application&iId=20)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)

---

### Post by 4Orbs on 2010-06-01
There is no reason to abandon Win when you can set up a dual-boot and maybe even a separate shared partition. That will give you all the freedom you need to become acquainted with Linux while still using the Windows apps you are familiar with. At some point in the future you can erase MS when you find suitable Linux substitutes for those Windows applications. No need to rush into it blindly.

---

### Post by admiralspark on 2010-06-01
As 4Orbs said, there's no reason to wipe one and replace it with the other--dual boot instead. 
Also, an interesting article to read that will explain the positions of many people in the Linux community: [Read This]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by inameiname on 2010-06-01
I agree. For a beginner, it's best to go with Dual-Boot. For now. Hopefully, or should I say ideally (hehe), you'll use Ubuntu more and more, and find equivalents you want in time which would make your Windows partition pointless to have anymore. Best to make the transition as easy as possible, and on your terms of what you want to try and what you don't want to give up.

---

### Post by waynefoutz on 2010-06-01
> **inameiname said:**
> I agree. For a beginner, it's best to go with Dual-Boot. For now. Hopefully, or should I say ideally (hehe), you'll use Ubuntu more and more, and find equivalents you want in time which would make your Windows partition pointless to have anymore. Best to make the transition as easy as possible, and on your terms of what you want to try and what you don't want to give up.

I've been using Ubuntu since version 6.10. I STILL to this day keep a 20 gig partition with  Windows XP installed on it, though I rarely use it, except for the occasional odd game I can't get going with WINE. There is no shame in dual booting.

---

### Post by inameiname on 2010-06-01
Indeed. It's been a year for me now, and I still have a Windows image I throw onto my laptop on extremely rare occasions as it's still the only way I can use my scanner for those few times I need to.

---

### Post by 3rdalbum on 2010-06-02
Don't follow instructions online unless they actually specify that it's for the version of Ubuntu that you are using. The date on that HOWTO is May 2009; the latest version of Ubuntu at that time was Ubuntu 9.04, and there have been two versions of Ubuntu since then.

If you follow a HOWTO that is for an obsolete version of Ubuntu, you might actually screw things up. So don't do it!

---

