---
title: "Kdevelop and Quanta Plus in Gnome"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by linux4life88 on 2009-02-25
I was wondering if running KDE based applications like Kdevelop and Quanta Plus are alright to run under Gnome. I'm using Ubuntu 8.10. Will I run into any problems? Should I instead run Kubuntu in a virtual machine? I've tried to run only Gnome based applications in Ubuntu but there are not always equivalents that work well. Like Kdevelop which from what I've found is the best Linux alternative for Visual Studio and Quanta Plus which is the best Dreamweaver alternative for Linux.

---

### Post by KhaaL on 2009-02-25
No need for kubuntu in a vvirtual machine, you can run KDE apps in gnome just fine. I actually run both amarok and skype which are KDE apps and they run fine. That thing that will happen is that more libraries will be loaded (which is not a big deal if you have 512 MB or 1 GB or more RAM). also, they might not "blend" into your desktop theme, but I belive there are workarounds for that.

---

### Post by anewguy on 2009-02-25
No problems - I run several KDE applications, including Quanta Plus, all within Gnome.  Parts of KDE are installed but that is no problem - you can have KDE completely installed along with Gnome with no problems and even switch desktop managers at logon.  I have had no problems, but I suppose there may be an app or two out there somewhere that may not be as cooperative, but I wouldn't know why.  A couple of years ago I also was running Skype in Gnome with no problems, including an external USB "switch box" that automatically switched between the regular phone line and using Skype all with my regular cordless phone.

I wouldn't be concerned and just go ahead.

Dave ;)

---

### Post by linux4life88 on 2009-02-25
Thanks for all the help, that is just great. I have 2gb of ram so no problem with loading extra libraries. Also, anewguy can you explain more about how to install KDE along side of Gnome. I've never knew that you could do this. I was wondering if there is something special I had to do and how it would exactly work. Are there any sites out there that explain more about how to do this.

---

### Post by OffAxis on 2009-02-25
```
sudo apt-get install kubuntu-desktop
```

will install the k desktop along with all of it's applications. Although if you want the latest and greatest from kde you'll need to follow the instructions here:
[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

Once installed you just choose it from the 'Session Type' at the login screen.

---

### Post by anewguy on 2009-02-25
sudo apt-get install kde will install kde.  To use it, when the logon screen is open (be it power on or if you just log off) there is a clickable word "Options" in the lower left.  From there you can select your session - gnome or kde.

Dave ;)

---

### Post by sinisterstuf on 2010-10-01
I'm using Quanta in GNOME but I get an error message every time it starts. Certain things like Cervisia (which are also installed) don't work, I get the following message:
[I]The **CVS Management (cervisia)** plugin could not be loaded.
Possible reasons are:
- **CVS Management (cervisia)** is not installed;
- the file kde3/libcervisiapart.la is not installed or is not reachable.[/I]

What have I done wrong?

---

### Post by LeeM on 2011-03-15
> **sinisterstuf said:**
> I'm using Quanta in GNOME but I get an error message every time it starts. Certain things like Cervisia (which are also installed) don't work, I get the following message:
[I]The **CVS Management (cervisia)** plugin could not be loaded.
Possible reasons are:
- **CVS Management (cervisia)** is not installed;
- the file kde3/libcervisiapart.la is not installed or is not reachable.[/I]

What have I done wrong?

This question has come up before. The problem is that Quanta+ is a KDE3 app. Cervisia is KDE4. There is a (long) workaround given in
[http://ubuntuforums.org/showthread.php?t=1003635](http://ubuntuforums.org/showthread.php?t=1003635)

---

