---
title: "Debian repositories"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by jonaskn on 2009-01-10
Hi
I have an old iBook  g3 on which I resently installed Debian. I would like to install firefox 3, sun-java6-jre and flash(preferably adobe), I would prefer to install the programs using apt-get or synaptic, so that I have automatic opdates. My problem is that I cannot find any repositories containing this software.


Jonas

---

### Post by handydan918 on 2009-01-10
Debian has a little disagreement with Mozilla. Debian doesn't package firefox because of trademark issues, but they have Iceweasel, which is FF code, without the branding. 
IOW, Iceweasel is firefox, without the name "Forefox".

---

### Post by avtolle on 2009-01-10
> **jonaskn said:**
> Hi
I have an old iBook  g3 on which I resently installed Debian. I would like to install firefox 3, sun-java6-jre and flash(preferably adobe), I would prefer to install the programs using apt-get or synaptic, so that I have automatic opdates. My problem is that I cannot find any repositories containing this software.


Jonas
You will not find adobe flash in any ppc repository, as such does not exist in modern form. We ppc users are orphaned by adobe. There is gnash, an open-source flash-type application, which you can try, but be aware you won't be pleased in general.

---

### Post by wolfen69 on 2009-01-10
[Install firefox in debian]("http://www.deviceguru.com/adding-real-firefox-to-debian-lenny/")
unless you are using debian etch. then go [here]("http://forums.debian.net/viewtopic.php?t=29144").

---

### Post by avtolle on 2009-01-10
The OP might want to go to [http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328) (the Apple Users sub-forum) for additional information and assistance.

---

### Post by cwsnyder on 2009-01-10
Debian, by choice, does not support any of the proprietary standards, only Free Open Source Software as certified by GNU or similar licensing.  Thus, you Java, Flash, MP3 music, and commercial DVD files are not supported in any Debian repository.  If you add them, you are on your own to maintain the packages.

If you wish all of those, you are better off with either Ubuntu or Linux Mint.  Ubuntu doesn't include those packages by default, but do maintain repositories with them available, while Linux Mint installs them as part of the installation process and maintains the repositories from upstream sources, just like the FOSS sources.

---

### Post by avtolle on 2009-01-10
> **cwsnyder said:**
> Debian, by choice, does not support any of the proprietary standards, only Free Open Source Software as certified by GNU or similar licensing.  Thus, you Java, Flash, MP3 music, and commercial DVD files are not supported in any Debian repository.  If you add them, you are on your own to maintain the packages.

If you wish all of those, you are better off with either Ubuntu or Linux Mint.  Ubuntu doesn't include those packages by default, but do maintain repositories with them available, while Linux Mint installs them as part of the installation process and maintains the repositories from upstream sources, just like the FOSS sources.
The OP won't be able to use Mint, as he has a ppc machine. I'd suggest Ubuntu or some derivative for his ppc computer, but that won't get him entirely where he wants to be on the iBook G3 currently in issue.

---

### Post by cwsnyder on 2009-01-10
You are correct, Mint won't work.  As a matter of fact, Ubuntu won't work, either for PPC based systems, only Intel & AMD processor systems.  CRUX PPC is an alternative [http://www.ppcnux.com/?q=crux-ppc-in-version-2.4](http://www.ppcnux.com/?q=crux-ppc-in-version-2.4)  Running Ubuntu on a PPC is discussed here: [http://www.itwire.com/content/view/21406/1141/](http://www.itwire.com/content/view/21406/1141/)  There is also a web page for support of Power PC Linux users at [http://penguinppc.org/](http://penguinppc.org/) that I found through Google.

Looks like many of the Power PC versions are 2006 based or older.  Debian Etch is at least newer, and with Gnash, should at least show SOME flash.

PPC GNU/Linux versions listed include:
    *  CRUX PPC
    * Debian Linux
    * Gentoo Linux
    * Mandrakelinux
    * Yellow Dog Linux
    * ROCK Linux
    * Red Hat Enterprise Linux
    * SUSE LINUX Enterprise Server
Ubuntu 8.04 Sun Java JRE packages for PPC are available here:
[https://launchpad.net/ubuntu/hardy/powerpc/sun-java6-jre](https://launchpad.net/ubuntu/hardy/powerpc/sun-java6-jre)
I have no knowledge if they would work on Debian.

---

