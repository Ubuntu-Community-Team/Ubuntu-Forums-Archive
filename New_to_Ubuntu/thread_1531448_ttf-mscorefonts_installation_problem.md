---
title: "ttf-mscorefonts installation problem"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by pzico on 2010-07-15
Hi,

I can't install ttf-mscorefonts because always the package manager never finds Andale32.exe from given path. Looking for forums I found out I can install the package manually, but even those ttf-mscorefonts have dependencies to outside leading to the same problem. How can I install ttf-mscorefonts? Is there a full deb package somewhere including all the necessary parts without trying to load things from non-existing URLs from Internet while installing?

-pz

---

### Post by garvinrick4 on 2010-07-15
Just install 

```
sudo apt-get install ubuntu-restricted-extras
```It will also give you anything else you might have missed that are needed.
Your core microsoft fonts, java,  flash all codecs for music or video players and more.
If it is already installed will just pass on it. So know problems and you get your fonts.

---

### Post by pzico on 2010-07-15
```
sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
```

It's already installed :(

```
sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ttf-mscorefonts-installer
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
Need to get 0B/36.7kB of archives.
After this operation, 201kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package ttf-mscorefonts-installer.
(Reading database ... 288335 files and directories currently installed.)
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.2_all.deb) ...
Processing triggers for fontconfig ...
Setting up ttf-mscorefonts-installer (3.2) ...

--2010-07-15 09:23:55--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-07-15 09:24:16--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-07-15 09:24:37--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-07-15 09:24:58--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

```

---

### Post by garvinrick4 on 2010-07-15
ON the front page of Software Sources did your check multiverse. That is the repository you need.  rick@rick-laptop:~$ aptitude show ttf-mscorefonts-installer Package: ttf-mscorefonts-installer State: installed Automatically installed: no Version: 3.2 Priority: optional Section: multiverse/x11 Maintainer: Ubuntu Developers  Uncompressed Size: 201k Depends: wget, cabextract, xfonts-utils, defoma, debconf (>= 0.5) | debconf-2.0 Recommends: ttf-liberation, x-ttcidfont-conf Conflicts: msttcorefonts (< 2.6) Replaces: msttcorefonts (< 2.6) Provides: msttcorefonts Description: Installer for Microsoft TrueType core fonts  This package allows for easy installation of the Microsoft True Type Core Fonts  for the Web including:      Andale Mono   Arial Black   Arial (Bold, Italic, Bold Italic)   Comic Sans MS (Bold)   Courier New (Bold, Italic, Bold Italic)   Georgia (Bold, Italic, Bold Italic)   Impact   Times New Roman (Bold, Italic, Bold Italic)   Trebuchet (Bold, Italic, Bold Italic)   Verdana (Bold, Italic, Bold Italic)   Webdings    You will need an Internet connection to download these fonts if you don't  already have them.     NOTE: the package ttf-liberation contains free variants of the Times, Arial and  Courier fonts. It's better to use those instead unless you specifically need  one of the other fonts from this package.  rick@rick-laptop:~$  I do not believe you want a dos package andale.exe

---

### Post by garvinrick4 on 2010-07-15
sudo apt-get install ttf-mscorefonts-installer Reading package lists... Done Building dependency tree        Reading state information... Done The following NEW packages will be installed:   ttf-mscorefonts-installer 0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded. Need to get 0B/36.7kB of archives. After this operation, 201kB of additional disk space will be used. Preconfiguring packages ... Selecting previously deselected package ttf-mscorefonts-installer. (Reading database ... 288335 files and directories currently installed.) Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.2_all.deb) ... Processing triggers for fontconfig ... Setting up ttf-mscorefonts-installer (3.2) ...  Looks like it installed.Code:   aptitude show ttf-mscorefonts-installer

---

### Post by garvinrick4 on 2010-07-15
```
sorry I was using a Alpha 10.10 and was acting a bit flacky.
Here is what your fonts look like anyway in easier to read format.

rick@rick-laptop:~$ aptitude show ttf-mscorefonts-installer
Package: ttf-mscorefonts-installer
State: installed
Automatically installed: no
Version: 3.2
Priority: optional
Section: multiverse/x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 201k
Depends: wget, cabextract, xfonts-utils, defoma, debconf (>= 0.5) | debconf-2.0
Recommends: ttf-liberation, x-ttcidfont-conf
Conflicts: msttcorefonts (< 2.6)
Replaces: msttcorefonts (< 2.6)
Provides: msttcorefonts
Description: Installer for Microsoft TrueType core fonts
 This package allows for easy installation of the Microsoft True Type Core Fonts
 for the Web including: 
 
  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings
 
 You will need an Internet connection to download these fonts if you don't
 already have them. 
 
 NOTE: the package ttf-liberation contains free variants of the Times, Arial and
 Courier fonts. It's better to use those instead unless you specifically need
 one of the other fonts from this package.

rick@rick-laptop:~$ 

```

---

### Post by -kg- on 2010-07-15
> **garvinrick4 said:**
> sudo apt-get install ttf-mscorefonts-installer Reading package lists... Done Building dependency tree        Reading state information... Done The following NEW packages will be installed:   ttf-mscorefonts-installer 0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded. Need to get 0B/36.7kB of archives. After this operation, 201kB of additional disk space will be used. Preconfiguring packages ... Selecting previously deselected package ttf-mscorefonts-installer. (Reading database ... 288335 files and directories currently installed.) Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.2_all.deb) ... Processing triggers for fontconfig ... Setting up ttf-mscorefonts-installer (3.2) ...  [COLOR="Red"]Looks like it installed.[/COLOR]Code:   aptitude show ttf-mscorefonts-installer

Yes, it does, but this confuses the hell out of me.  Why would it install the .deb packages, and then immediately try to download a DOS executable file (which I would *think* would fail to install even if it *was* downloaded)?

Something in that just doesn't make sense, especially since it was done through "apt-get."  I pulled up Synaptics on my computer and it shows "ttf-mscorefonts-installer" as already installed, probably through "ubuntu-restricted-extras", which is one of the first things I install after every new installation.

---

### Post by pzico on 2010-07-15
Yes, multiverse is enabled. I'm not particularly interested in those M$ fonts, but some other packages have dependencies to those. For example wine.

I just don't get it that if I have unreachable URLs, why there is no such package containing those files within, because broken or unreachable or non IPV6 proxy or whatever problems reaching externals things can break package installation.

---

### Post by sarim on 2010-07-15
i also suffered from the problem since i started using ubuntu.
You can to 2 things,

1) In synaptic, mark wine for install. then search ttf-mscorefonts then unmark it for install. 
then click Apply. It will install wine without ttf-mscorefonts, so no hazard.

2) problem is that the sourceforge server is down. You need to use a mirror that is not down. try to manually download a file from sourceforge. then try the mirrors and find out which mirror is working for you.
then findout the ip address of that mirror.
Like for me iweb.dl.sourceforge.net is working good. so in terminal i run,
```
dig iweb.dl.sourceforge.net
```
then i found the ip is 216.34.181.96

then i manually edited the hosts file and defined the download server of sourceforge as 216.34.181.96. ( in my case nchc.dl.sourceforge.net)

then when any program want to connect to down sourceforge server it goes to your given ip and that is a running and good sourceforge server. :)

---

### Post by pzico on 2010-07-15
Thanks Sarim, that works well! :)

I also found another way just a moment ago (dunno if this will break anything.

```
$ cat /etc/default/linux-restricted-modules-common
DISABLED_MODULES="ttf-mscorefonts-installer"
```

---

### Post by y3kready on 2012-01-02
Thanks Sarim, this problem where the sourceforge server was down or not resolving caused havoc with my ubuntu-restricted-extras installation. Your solution to include the correct IP address in the /etc/hosts file worked well.

On further analysis I realized the root of the problem was my DNS server configuration. Once that got sorted the installation completed without any errors.

---

### Post by oldos2er on 2012-01-02
Closed, necromancy.

---

