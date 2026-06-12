---
title: "Trying To Install Gloobus-Preview...Dependency Issue =["
date: 2009-05-18
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-05-18
I'm trying to install [Gloobus-Preview 0.03.2](http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947) on Linux Mint x64 "Felicia" (A Ubuntu 8.10 based distribution) but I'm getting the following dependency Issue :? 

```
carl@mint-desktop ~/Desktop $ sudo dpkg -i gloobus-preview_0.03.2_amd64.deb
[sudo] password for carl: 
Selecting previously deselected package gloobus-preview.
(Reading database ... 130009 files and directories currently installed.)
Unpacking gloobus-preview (from gloobus-preview_0.03.2_amd64.deb) ...
dpkg: dependency problems prevent configuration of gloobus-preview:
 gloobus-preview depends on libpoppler-glib4 (>= 0.10.5); however:
  Package libpoppler-glib4 is not installed.
 gloobus-preview depends on libgstreamer-plugins-base0.10-0 (>= 0.10.22); however:
  Version of libgstreamer-plugins-base0.10-0 on system is 0.10.21-3ubuntu0.1.
dpkg: error processing gloobus-preview (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gloobus-preview

```

What do I need to do?

---

### Post by ptn107 on 2009-05-18
gloobus-preview_0.03.2_amd64.deb depends on two other packages that must be installed first:

libpoppler-glib4 (>= 0.10.5)
libgstreamer-plugins-base0.10-0 (>= 0.10.22)

Unfortunately, these newer versions are only available if your running Ubuntu 9.04 (or Linux Mint 7 [which isn't released yet]) and by the looks of it your running Linux Mint 6.  You have two choices now: 1) Upgrade/Install Ubuntu 9.04 or Linux Mint 7 (when it's released), or 2) Attempt to grab just these needed files from the Ubuntu 9.04 repository (which may or may not work).

If you opt for solution #1 and are installing Ubuntu, read the [_release notes_]("http://www.ubuntu.com/getubuntu/releasenotes/904") first before you [_upgrade_]("http://www.ubuntu.com/getubuntu/upgrading") or clean install.

If you want to try solution #2, open a terminal (Applications -> Accessories -> Terminal), copy/paste the following and run as one command:

```
sudo touch /etc/apt/sources.list.d/jaunty.list && echo 'deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted' | sudo tee -a /etc/apt/sources.list.d/jaunty.list && sudo aptitude update && sudo aptitude install libpoppler-glib4 libgstreamer-plugins-base0.10-0 -y && sudo rm /etc/apt/sources.list.d/jaunty.list && sudo aptitude update
```

---

### Post by kamitsukai on 2009-05-18
Thanks! =]

---

### Post by kamitsukai on 2009-05-18
> **kamitsukai said:**
> Thanks! =]

OK Scrap that:)

It's borked my install...

I now get almost to the GDM I can see and move the cursor but it's constantly loading...how can I remove what I've installed and restore everything??

---

### Post by kamitsukai on 2009-05-18
Ok I got into the root shell, is it? by pressing ctrl + Alt + F1 and then I did

```
sudo aptitude remove libpoppler-glib4
```

and

```
sudo aptitude remove libgstreamer-plugins-base0.10-0
```

and then

```
sudo aptitude install libgstreamer-plugins-base0.10-0
```

But still no joy =[

---

### Post by kamitsukai on 2009-05-18
Anybody? please... =[

---

### Post by kamitsukai on 2009-05-19
I reinstalled in the end =]

---

