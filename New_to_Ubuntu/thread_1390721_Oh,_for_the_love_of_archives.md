---
title: "Oh, for the love of archives"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by boycow on 2010-01-25
Whenever I go to open .exe or rar files I get this:

Archive:  /home/boycow/Downloads/InstallRarZilla.exe
[/home/boycow/Downloads/InstallRarZilla.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/boycow/Downloads/InstallRarZilla.exe or
          /home/boycow/Downloads/InstallRarZilla.exe.zip, and cannot find /home/boycow/Downloads/InstallRarZilla.exe.ZIP, period.

Look, I know I'm gonna get made fun of but I have no idea what this means.  If my computer is a car, about the only maintenance I know is changing the oil or gaskets and junk.  I would like to learn though, so any help is greatly appreciated.
  I can't extract or anything...this sucks:(

---

### Post by tigerking615 on 2010-01-26
Does that happen to all files of those types, or just a couple?

You can break a .rar file into parts so that each part is smaller and easier to download, and they can be extracted together. Although I've never had that problem before, I'd guess that your error sounds like you've only got one piece of the archive.

As for the .exe files, you don't install things with .exe's in Ubuntu (unless you're using Wine). 

Check out this page on Installing Software. I have it bookmarked ^^
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by cbabbage on 2010-01-26
.exe are Windows executable files. They don't work on a Linux system, except possibly through wine.
For the .rar files you will need to download a tool called unrar, if it isn't already installed. The simplest way to download it is to go System > Administration > Synaptic Package Manager. It will ask you for your password. When it opens, go to the search button and type in unrar. It will find the package for you, you will need to mark it for installation and hit the Apply button.
Synaptic will install it for you.
Once its installed, you use it by opening a terminal, then changing directory to the one containing the rar files. Then use the command
unrar yourfile.rar

Any problems get back to me.

---

### Post by louieb on 2010-01-26
The file InstallRarZilla.exe is not an achive - from its website looks like some kind of windows application install file. Might get it to install and run it using wine.

 If you need to use rar file archives -  1st you will need to install packages **rar and unrar.**

---

### Post by boycow on 2010-01-26
Thanks guys.  So I was basically trying to fit a bill clinton shaped polygon into a narrow slit under a door, gotcha.  Went to package manager, got unrar, everything works fine.

---

