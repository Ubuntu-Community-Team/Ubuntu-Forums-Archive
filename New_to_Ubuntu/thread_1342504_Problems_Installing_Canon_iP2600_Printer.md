---
title: "Problems Installing Canon iP2600 Printer"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-11-30
I am having some problems installing my Canon iP2600 printer.
Following the advise and instructions in [http://swiss.ubuntuforums.org/showthread.php?t=775368]("http://swiss.ubuntuforums.org/showthread.php?t=775368") (the 5th response, by "naildeca"), the drivers are from [http://support-asia.canon-asia.com/E...os%3d%3dLinux&]("http://support-asia.canon-asia.com/E...os%3d%3dLinux&")
Following the advise, the printer is on (and connected) and I first tried to install the common package first.
But something has gone wrong. it has "failed to completely install all dependencies." Here it is in detail:
```
Selecting previously deselected package cnijfilter-common.
(Reading database ... 140211 files and directories currently installed)
Unpacking cnijfilter-common (from .../cnijfilter-common 2.901_i386.deb) ...
dpkg dependency problems prevent configuration of cnijfilter-common:cnijfilter-common depends on libcupsys2 (>= 1.2.1); however: Package libcupsys2 not installed
dpgk: error processing cnijfilter-common (-- install); dependency problems - leaving unconfigured
Errors were encountered while processing:
cnijfilter-common
```
(Note: I could not copy and paste from the gdebi-gtk window, so I had to retype it. There may/may not be some typographic errors in it.)

It's advise (in another window) is to do "sudo apt-get install -f" in Terminal, which I did.

Then, I tried to get this "libcupsys2" with: ```
sudo apt-get install libcupsys2
```
Unfortunately, the results was this:```
jutumang@jutumang-laptop:~$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcupsys2 is a virtual package provided by:
  libcups2 1.4.1-5ubuntu2.1
You should explicitly select one to install.
E: Package libcupsys2 has no installation candidate
```
And it had no effect when I retried installing the common package.

How do I get this installed, so I can finally install the common package?

Thanks for your time,
RedStarYellowSun

---

### Post by cariboo on 2009-12-03
The the error message suggested, install libcups2 1.4.1-5ubuntu2.1.

---

