---
title: "Update to Open Office 3.1"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-09-27
I just performed a fresh install of Intrepid Ibex, and I'm trying to update Open Office.  I've put in the source codes and the key, but this time it won't update.  Does anyone know if there are issues with this?

---

### Post by wilee-nilee on 2009-09-27
> **hifly1231 said:**
> I just performed a fresh install of Intrepid Ibex, and I'm trying to update Open Office.  I've put in the source codes and the key, but this time it won't update.  Does anyone know if there are issues with this?

What source code and keys, OO 3.1 on Intrepid will probably only be available from OO in a targz, although I think they offer debs for later OS. You might try installing Ubuntu Tweak and see if if OO 3.1 is in it, OO 3.1 installed on my computers with no problems in jaunty using Ubuntu Tweak.

---

### Post by Amstell on 2009-09-28
What were the Software Sources?

What happens when you update your sources?  any errors?:  

sudo apt-get update

---

### Post by jimwhitend on 2009-09-28
> **wilee-nilee said:**
>  . . . You might try installing Ubuntu Tweak and see if if OO 3.1 is in it, OO 3.1 installed on my computers with no problems in jaunty using Ubuntu Tweak.

The problem I have had with getting OOo 3.1 is that the PUB_KEY for the repository won't install. In fact I can't get any PUB_KEYs to install from keyserver.ubuntu.com. 

But I wonder what Ubuntu Tweak is. Where do I get it and how did it help you install OOo 3.1? Thanks.
-JimW

---

### Post by wilee-nilee on 2009-09-28
Ubuntu Tweak is a installing program for us non geeks which can make your life easier. It will install 3rd party programs and keys some programs have to be installed from it's add remove link after the refresh in 3rd party. I have a suspicion that OO 3.1 wont be in the intrepid version but you never know. Here is the launchpad PPA link. even though I can install this stuff and add keys I still use it regularly in that it will clear your cache and not needed stuff check it out.  [https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa](https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa)  I just found this link [http://matt.bottrell.com.au/archives/350-OpenOffice-3.1-for-Ubuntu.html](http://matt.bottrell.com.au/archives/350-OpenOffice-3.1-for-Ubuntu.html)

---

### Post by Hagar Delest on 2009-09-28
Or try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by hifly1231 on 2009-10-03
> **Amstell said:**
> What were the Software Sources?

What happens when you update your sources?  any errors?:  

sudo apt-get update

This is the source code that I've used in the past that seemingly no longer works:

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) intrepid main

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF

This update worked fine about a month ago.  Now Software Sources reloads, then nothing.

---

### Post by wilee-nilee on 2009-10-03
If your PPA link is associated with the scribblers PPA for open office; Jaunty is the only dist on there now.
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
Go straight to Sun get the deb package and install.
[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

---

