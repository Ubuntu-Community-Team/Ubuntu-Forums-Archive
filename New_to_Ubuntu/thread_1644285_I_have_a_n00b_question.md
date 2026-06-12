---
title: "I have a n00b question"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-13
So I am fairly new to ubuntu and I am not sure why every file downloaded is not a .deb file.  There are rpm, tar, ect.  How come everything isnt a deb, it seems easier on the end user. 

From my understanding a .deb file is similar to a windows exe file, correct?

---

### Post by Perfect Storm on 2010-12-13
More like a .msi file. But in many cases you don't need to download .deb files - Most software and stuff you can find in Ubuntu Software Center or Synaptic Package Manager.

rpms are used by distros like Fedora and Suse.
tar.gz is like zip files, they can contain everything - Most likely  the source codes - when we're talking about open source applications or libs. The Source codes you can use to compile the application to fit exactly your needs or change the applications or behavior.

---

### Post by rockerphil on 2010-12-13
ok, here's a quick break down. .deb files are for Debian based distros, and you're right about .deb files being similar to .exe files, with the exception that .exe files are simply a program, where as .deb files are packages that install a particular program. .rpm files are for RedHat based distros such as Fedora or SUsE, and do essentially the same thing as .deb packages in Debian based distros. .tar files are a throw back to tape archiving, and typically carry the source code of a program that needs to be compiled before it can run. since you use Ubuntu i'd suggest looking in the Ubuntu Software Center for the majority of your program needs before looking for a program to download from the web, most of the programs you'll need or want will be in the repositories. hope this helps, and feel free to ask for any more clarification or any other questions for that matter.

Phil

---

### Post by NightwishFan on 2010-12-13
Sort of. I would say installers packaged in ".bin" files are more along the lines of the user experience for Windows executables. ".deb" means "Debian Package", which generally are only compatible with Debian based systems. It is specifically designed to integrate with a system wide add/remove called "Package Management".

-1 for slowness. :)

---

