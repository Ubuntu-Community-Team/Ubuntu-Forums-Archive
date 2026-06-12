---
title: "dvd::rip will not launch"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by Nickjpost on 2010-11-18
I recently installed dvd::rip on ubuntu 10.04. It worked once and now, when I try to launch it, it does nothing. I uninstalled the software then reinstalled it, but it does the same thing. I tried to launch it from the command line and this is the output I recieved:
 
[EMAIL="nickjpost@nickjpost:~$"]nickjpost@nickjpost:~$[/EMAIL] dvdrip
can't write /home/nickjpost/.dvdrip/tool_version_cache at /usr/share/perl5/Video/DVDRip/Depend.pm line 413.
Compilation failed in require at (eval 13) line 3.
    ...propagated at /usr/share/perl/5.10/base.pm line 93.
BEGIN failed--compilation aborted at /usr/share/perl5/Video/DVDRip.pm line 16.
Compilation failed in require at /usr/bin/dvdrip line 96.
 
 
Any ideas as to what happened? Each time I reinstall it I get this exact message.
I've tried installing through package manager as well as via the command line.

---

### Post by LowSky on 2010-11-18
sounds like the package is bad from whatever mirror you are getting

try installing the deb directly
[http://packages.ubuntu.com/maverick/all/dvdrip/download](http://packages.ubuntu.com/maverick/all/dvdrip/download)


see this link if you need to fix dependencies.
[http://packages.ubuntu.com/maverick/dvdrip](http://packages.ubuntu.com/maverick/dvdrip)

---

### Post by Nickjpost on 2010-11-18
Thank you , LowSky! I'll give it a shot and post my results.

---

### Post by Nickjpost on 2010-11-18
Found that I only get that error I previously posted when I tried to launch from the command line as a regular user. When I launch it as root, then it starts up.....weird, but I'll take it

---

