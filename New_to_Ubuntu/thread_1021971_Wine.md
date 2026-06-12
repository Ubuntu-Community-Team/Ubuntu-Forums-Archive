---
title: "Wine"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by simbits on 2008-12-26
I can't seem to get Wine to work.
Installed correctly, the Notepad works fine, but I can't get it to install anything.
I had Ubuntu 8.10, and wine worked fine. Installed a program through it and it worked smoothly.

Had Ubuntu taken off by mistake, and put the same version on, same wine on, but it will not install this program.
Last time, a friend installed wined and everything else for me, when I first got Ubuntu. Now, I don't know how to get it to work. He told me I have to change the options? Or set it up right, but nothing I do seems to work. I just get this message when I try to install that file.

It's the same exact file as before. Idk why it's talking about zip files.

```
[/home/christine/Desktop/ScratchInstaller1.3.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/christine/Desktop/ScratchInstaller1.3.exe or
          /home/christine/Desktop/ScratchInstaller1.3.exe.zip, and cannot find /home/christine/Desktop/ScratchInstaller1.3.exe.ZIP, period.

```

"All aboard the failboat" ;)

---

### Post by tibellus on 2008-12-26
Have you tried going through Nautilus to that file, right click on it and use open with "Wine Windows Program Loader"? It seems that it might be mistaken with a zip file. I got some sort of similar error when I installed the alpha version of Adobe Air. All the .air packages were considered zip files. You could look at the MIME settings and see if .exe is using the right program for opening.

---

### Post by Kellemora on 2008-12-26
HI Simbits

Unzip the file into a new folder on your desktop.

Move the folder into your .wine Programs Directory

Find the install.exe or setup.exe file and run that in wine.

Wine tends to try and unzip things that are not zipped due to various file extensions it encounters.

TTUL
Gary

---

### Post by LowSky on 2008-12-26
first start up wine config

then close it, then go to where the file is save on your computer, right click on it and choose run with Wine

should work

also generally speaking files do not have two periods in the file name (at least with Windows files), that could be the issue)
ScratchInstaller1**_._**3**_._**exe

those **_._** could be the issue
should look more like
ScratchInstaller1-3.exe
ScratchInstaller1_3.exe
ScratchInstaller.exe

---

