---
title: "Wine and MS Money?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by torbengb on 2009-09-06
Hi, I'm new to Linux & Ubuntu. I'm trying to get away from Windows and I've read that Wine can run (some) Windows applications. I want to run Microsoft Money 2004 inside Wine but haven't made it run yet -- I suspect that Money requires Internet Explorer, and IEs4Linux isn't installed yet, I fail to do that. Your help is much appreciated!

--> Is IEs4linux likely the culprit, or should I try something else?
--> How can I install IEs4linux? See below what I've done so far.

So far: 
[LIST=1]
[*]My Ubuntu (Wubi 9.04) has Wine 1.0.1 installed. I've managed to mount my NTFS drive (where the setup files are) and installed Money. I can navigate to [FONT="Courier New"]/home/torben/.wine/dosdevices/c:/Program Files/Microsoft Money/System[/FONT] but when I start the program (msmoney.exe) then Money fails: "MS Money has encountered a problem and needs to close."
[*]I found MS Money 2004 [on the WINE compatibility list]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2728") and noted that there are steps needed (install ies4linux) before installing Money.
[*]On following the steps, I get this error:
[FONT="Courier New"]$ ./ies4linux
[COLOR="Red"]IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).
You need to install cabextract first! 
Download it here: [http://www.kyz.uklinux.net/cabextract.php](http://www.kyz.uklinux.net/cabextract.php)[/COLOR][/FONT]
[*]Unfortunately, uklinux.net seems down and I don't find cabextract in Ubuntu's "Add/remove..." either.
[/LIST]

---

### Post by hockeytux on 2009-09-06
Other than running MS Money in Wine or VirtualBox you could try using Linux equivalents of MS Money, like jGnash, GNU Cash or KMyMoney. That way you wont have to keep Windows programs that obviously only run in an emulator e.g.

---

### Post by Ms_Angel_D on 2009-09-06
+1 to kmymoney

---

### Post by misterfixit on 2009-09-06
If your system is using KDE install kmymoney and try it; if your system is using GNU install gnucash;  both offer the functions of MS Money without the "ET Call Home" problems requiring IE.

---

### Post by dearingj on 2009-09-06
I suggest you take a look at this page on Wine's web site: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2728](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2728)

That page appears to provide instructions on installing Money 2004 and IEs4Linux. Note that you'll need Wine 1.1.27 or later; the version in Ubuntu 9.04 is 1.0.1, you can get the latest version of Wine following these instructions: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Ms_Angel_D on 2009-09-06
> **misterfixit said:**
> If your system is using KDE install kmymoney and try it; if your system is using GNU install gnucash;  both offer the functions of MS Money without the "ET Call Home" problems requiring IE.

You can run either app regardless of whether your using KDE or Gnome.

---

### Post by bapoumba on 2009-09-06
I moved from MS Money to [grisbi]("http://http://www.grisbi.org/index.en.html") when I switched to Linux (and that was a long time ago :)). It's in the repos and the latest builds are in a ppa. You may not find all the features you are used to though.

---

### Post by blazemore on 2009-09-06
You're trying to run it from your Windows partition, right?

Well you'll have to install it again under Wine, since it's looking for files and registry entries which simply aren't there!

---

### Post by torbengb on 2009-09-06
> **blazemore said:**
> You're trying to run it from your Windows partition, right? No no, I'm using Wine to start the setup in order to install it anew inside Ubuntu.

*Dearingj* pointed out that Money only works with Wine 1.1.27 which is what I had missed. I'll try now to install that newer version and then try Money again.

I appreciate the number of suggestions to get away from Money -- I looked up all the suggestions and I will try out several of them. I still need to get into Money until I've settled on a Linux application, though.

**SOLVED:** *Got it working just fine -- after following the [WineHQ instructions **exactly**]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2728")*

---

