---
title: "Something like program files"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-29
Okay... now, I know that Ubuntu operates completely different than Windows and I know that you remove your programs completely differently. But... sometimes, I forget what programs I've downloaded (and this is easy to do when every program is free).  One of the conveniences of having Program Files is that I could see a list of every program. The downside is that I didn't always know what the program did or how important it was... BUT I at least had a straight forward list of the programs on my computer.

Is there a program that I can download that would list them? Is there something I can type in the terminal? 

Thank you for your time and your help. I can understand if you guys are busy on D-day. 

Peace.

---

### Post by tmx84 on 2010-04-29
Are you looking for something like Synaptic Package Manager?  It's located under System>Admin>Synamptic Package Manager... Once you have it open you can search through your repositories to install programs, or you can click on "Installed" in the left panel and it will list everything you have installed from the repositories, which gives you descriptions of each etc...

---

### Post by Sealbhach on 2010-04-29
You can do that in the Software Center, just select Installed Software, it will everything you have installed from the Package Manager.

Synaptic Package Manager can show you the same information in more detail. 

However, if you installed stuff through other means (not using dpkg) they won't show up there.

.

---

### Post by golanbatrac on 2010-04-29
Cut/paste or type the following into a terminal:

```
dpkg --get-selections | less
```to read the list in the terminal

or

```
dpkg --get-selections > ~/programlist.txt
```to save the output to a file (programlist.txt) in your home directory.

---

### Post by orphanlast on 2010-04-29
Crap... wasted thread. Thanks for posting, guys. Looks like the Ubuntu developers are a few steps ahead of me on this one. I just found a new default program called KPackageKit. When you open it, the window is given a title: "Add  and Remove Software"

It's at APPLICATIONS > SYSTEM TOOLS > KPACKAGEKIT.

It's just like program files on steroids. It's more user friendly. Thanks guys.


-------------------------
EDIT:

Actually, I had to reinstall Ubuntu 10.04. Kpackagekit is not a default program. But I'm sure going to put that sucker back on. That thing is handy.

---

### Post by arpanaut on 2010-04-29
Applications> Ubuntu Software Center> Installed Software.

OR

System> Administration> Synaptic Package Manager> Installed Packages

---

### Post by adam814 on 2010-04-29
Well, the executables are usually stored in either /bin, /sbin, /usr/bin, or /usr/local/bin.  Of course they don't have the same layout as the "Program Files" folder in Windows.

There are some ways to track something down though.  For example I have the openssh-client package installed on my laptop.  If I forgot the command for the ssh client (even though it's just ssh...) I would do this:

```
dpkg --list | grep ssh
```
This would show any installed packages that have "ssh" in the name or description.  From there let's say I've recognized openssh-client as the package it's in.  I would do this to find the command:
```
apt-file list openssh-client
```You might need to install apt-file first.

This lists every file in that package, including the one I needed (/usr/bin/ssh).

Hope that helps a little.

---

