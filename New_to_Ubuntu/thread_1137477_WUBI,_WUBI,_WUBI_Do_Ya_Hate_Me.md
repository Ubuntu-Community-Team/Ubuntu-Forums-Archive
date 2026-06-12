---
title: "WUBI, WUBI, WUBI Do Ya Hate Me?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by zaivala on 2009-04-25
I have tried to install Jackalope on my computer, and WUBI hangs every time I try to run it... I have downloaded WUBI Installer from the wubi-installer.org site, and I have downloaded Ubuntu from the Ubuntu site and tried to install using WUBI on the disk.  Either way, it just starts feeding me massive amounts of error messages, and I have to use my Three Finger Salute and delete one (sometimes two) Python programs (pyrun.exe and pyl35.exe) to get my machine back.

This machine has correctly installed Heron and Ibex in the past (and more recently, incorrectly installed it - no sound and other problems), but currently does not have either installed, only XP Home.

I'm glad others are getting to report problems with 9.04... I haven't even begun to install it yet.

Machine is HP Pavilion a1020n, 2.5 Gb RAM, over 500 Gb hard disk.

---

### Post by lisati on 2009-04-28
Have a look at [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

---

### Post by bennachie on 2009-04-28
After experiencing just the same series of frustrations, I downloaded a later version of wubi.exe from:

[http://releases.ubuntu.com/jaunty/wubi.exe](http://releases.ubuntu.com/jaunty/wubi.exe)

This seems to be version 129 (rather than version 128, which is embedded in the 9.04 release) and, if you make sure there is a valid Ubuntu ISO in the same folder when you launch Wubi under Windows, it works perfectly (for me at least - YMMV). Pity they could not have got it right in the first place.

I was lulled into a false sense of security - having actually tested the process with the Beta release, I failed to double-check when the Release Candidate was issued.

---

### Post by lisati on 2009-04-28
> **bennachie said:**
> After experiencing just the same series of frustrations, I downloaded a later version of wubi.exe from:

[http://releases.ubuntu.com/jaunty/wubi.exe](http://releases.ubuntu.com/jaunty/wubi.exe)

This seems to be version 129 (rather than version 128, which is embedded in the 9.04 release) and, if you make sure there is a valid Ubuntu ISO in the same folder when you launch Wubi under Windows, it works perfectly (for me at least - YMMV). Pity they could not have got it right in the first place.

I was lulled into a false sense of security - having actually tested the process with the Beta release, I failed to double-check when the Release Candidate was issued.

Thanks for the comments. I ended up bypassing Wubi on the machine I experienced the troubles on and ended up putting Ubuntu into its own partition.

EDIT: I had a look at the Wubi log from one of my failed attempts, looks like the revision I had was 122!!!!

---

### Post by bennachie on 2009-04-28
I seem to recall (but won't guarantee) that 122 was the current version when the beta was released. Whatever, it worked OK then (as did the USB Startup Disk Creator, but that's another story).

While Wubi installation may not be an important mechanism for those of us who are comfortable with Ubuntu, and find it vastly superior to Windows for almost all practical purposes, it can be great for the nervous newcomer. It should, in principle, offer a simple, risk-free way to put their toes into the water, and discover just how nice Ubuntu can be. Finding and reporting  bugs in Wubi is thus a worthwhile activity, albeit sometimes a frustrating one.

---

### Post by lisati on 2009-04-28
> **bennachie said:**
> I seem to recall (but won't guarantee) that 122 was the current version when the beta was released. Whatever, it worked OK then (as did the USB Startup Disk Creator, but that's another story).

While Wubi installation may not be an important mechanism for those of us who are comfortable with Ubuntu, and find it vastly superior to Windows for almost all practical purposes, it can be great for the nervous newcomer. It should, in principle, offer a simple, risk-free way to put their toes into the water, and discover just how nice Ubuntu can be. Finding and reporting  bugs in Wubi is thus a worthwhile activity, albeit sometimes a frustrating one.

I'm pretty comfortable installing Ubuntu into its own partition these days, but can appreciate the value of Wubi for new users - which is the main reasons I've been checking out has been going on with the one of my machines, and why it seems to echo what others have been experiencing. I'm currently taking a break from my tinkering in that area, so my head doesn't explode (or something equally inconvenient)

---

### Post by zaivala on 2009-04-28
I'm really happy for those of you who are able to install Ubuntu in the old-fashioned way with its own partition.  I don't expect you to research me in this forum but... my HP Pavilion a1020n will not do that.  HP has some really intrusive software that, if it detects the MBR has been modified, forces you to reinstall the entire Windows system, which wipes the MBR and all Registry entries.  (I have listened to many users on ways to get around that, and so far have "crashed" my system 5 times.  Enough is enough.)  WUBI is the only way I can get Ubuntu on my system and still have a system... without using ONLY Ubuntu on here, and it's not yet able or stable enough to do everything I need to do or I'd have done that already.

I'll try the WUBI download... but shouldn't Ubuntu be trying to fix this in their distribution?  Why would they want to continue distributing a faulty copy of WUBI?  Unless Shuttleworth has bought large quantities of Microsoft stock...

---

### Post by lisati on 2009-04-30
Update on the problems I experienced (similar to what's described in [https://bugs.launchpad.net/ubuntu/+bug/365881):](https://bugs.launchpad.net/ubuntu/+bug/365881):) I did a fresh install of XP on the affected machine, burned a fresh CD downloaded from Cannonical, and tried the disk. No sign of the errors.

---

### Post by zaivala on 2009-04-30
Right, it is a recognized bug.  I note that nobody has yet reported a fix, and using the next revision of WUBI has not helped many.  I guess I'll just wait until someone says it's fixed.  No beans for me.

---

### Post by zaivala on 2009-11-10
OK, this thread should not be marked "SOLVED", but should be marked "IRRELEVANT".  First, I am no longer dual booting (I have Ubuntu on a separate tower - 2.6 GHz P4MT - from my Windoze - 3.4 GHz P4MT Dual Core).  Second, I have not heard the complaints about WUBI lately, and third, there is a whole new version or two of Ubuntu since this was reported.

Current Status:
HP Pavilion a1020n - Windoze XP Home
Gateway E6100 - Ubuntu Karmic Koala
ASUS Eee PC 901 - Ubuntu Netbook Remix Karmic Koala
ASUS Eee PC 701 - Ubuntu Netbook Remix Karmic Koala
ASUS Eee PC 901 - ASUS/Xandros
ASUS Eee PC 701 - Windoze XP

The last three Eees are being used by homeless or formerly-homeless people around town.  I should be upgrading the other 901 to Ubuntu Netbook Remix as soon as I get access to it, and will likely never again see the 701 with Windoze on it.

Moss

---

