---
title: "New user questions"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by yeh on 2010-11-28
Sorry, I'm new to ubuntu and there's an awful lot to learn, so starting with the most important question...

Where's the file location for the application menu? Like there's a windows folder in which you can edit and determine what stuff goes into the start menu (or you can just drag the shortcut into the start menu). You can't drag anything onto the ubuntu netbook applications menu; you can't left click and determine shortcuts. It is, in my humble opinion, good-looking but not very useful if I can't edit it, put stuff in it, take stuff off it, etc.

What's the format for text files in ubuntu? Running a .txt file in ubuntu shows that it isn't the native text file format (I can open it, but it always says that it is an executable text file when it obviously isn't).

What's the format for executable files in ubuntu? .exe is the format for windows applications. I know its not .deb because .deb is just used to install the program; its not the format of the program itself.

Thx for your answers.

---

### Post by Megaptera on 2010-11-28
There are mixed views about the Netbook Edition & Unity - that I think you are referring to. You can select Desktop Session just as you log on - look towards bottom right of screen. Personally I prefer the Gnome desktop on my laptop.

If you want to run Windows progs (.exe) under Ubuntu you need to run them through Wine:
[http://psychocats.net/ubuntu/wine](http://psychocats.net/ubuntu/wine)

To edit what runs at startup, go to Control Centre > Startup Applications.

---

### Post by kaldor on 2010-11-28
Even though I've been on Linux for years, I still might be wrong about this since I rarely encounter it...

I think that .bin (binary) files are the equivelent of executables on Linux.

---

### Post by chaanakya_chiraag on 2010-11-28
Usually, the files for the menu items are located in /usr/share/applications for global menu items and /home/$USER/.local/share/applications for user-specific menu items.

txt files are marked as executable if you transfer them from Windows because Windows doesn't have the same kind of control system Linux does.

---

### Post by chaanakya_chiraag on 2010-11-28
> **kaldor said:**
> Even though I've been on Linux for years, I still might be wrong about this since I rarely encounter it...

I think that .bin (binary) files are the equivelent of executables on Linux.

Actually, for the equivalent of exe files, you should look toward deb and rpm files.

---

### Post by kaldor on 2010-11-28
> **chaanakya_chiraag said:**
> Actually, for the equivalent of exe files, you should look toward deb and rpm files.

No. debs and rpms are package installers. executables can do much more than just install things.

deb/rpm are more akin to MSI files.

---

### Post by ajgreeny on 2010-11-28
There isn't really an equivalent of the Windows .exe executable file, or not in a simple way.  There are certainly .bin files, and .run files, but there are also many files with no file-type suffix at all, but which are executables, and as you have found there are lots of .txt files which are executable, along with .sh files which are probably the nearest to Windows .bat files, but not quite the same thing.

To be honest, you will be better served if you forget all about the Windows ways, and think again about the linux file system afresh; lots of things are done in a totally different way, and by trying to equate everything with Windows you may do nothing to help.  In fact you may just confuse yourself even more.

---

### Post by dFlyer on 2010-11-28
If I remember correctly any file under linux can be executable. It all depends on its property settings. Extensions are not required for an executable file.

---

### Post by madjr on 2010-11-28
> **yeh said:**
> Sorry, I'm new to ubuntu and there's an awful lot to learn, so starting with the most important question...

Where's the file location for the application menu? Like there's a windows folder in which you can edit and determine what stuff goes into the start menu (or you can just drag the shortcut into the start menu). You can't drag anything onto the ubuntu netbook applications menu; you can't left click and determine shortcuts. It is, in my humble opinion, good-looking but not very useful if I can't edit it, put stuff in it, take stuff off it, etc.

What's the format for text files in ubuntu? Running a .txt file in ubuntu shows that it isn't the native text file format (I can open it, but it always says that it is an executable text file when it obviously isn't).

What's the format for executable files in ubuntu? .exe is the format for windows applications. I know its not .deb because .deb is just used to install the program; its not the format of the program itself.

Thx for your answers.

which netbook edition are you using? 10.04 or 10.10?

they have different interfaces.

You can also log in to normal gnome desktop on the user login screen. Just choose ubuntu desktop, instead of ubuntu netbook

---

### Post by yeh on 2010-11-28
Thx everyone. I think all my questions have been answered. I'm using ubuntu 10.10 netbook btw. One follow up though: I asked where the location was for the application menu because I wanted to create shortcuts for my chrome web apps and pin those shortcuts to the unity dock (I can't pin the web apps themselves apparently). If I couldn't have pinned it, I would have used launchy to index a folder containing the shortcuts.

Only problem is that in my /home/$user/.local/share/applications, the web apps don't look like web apps at all. If I double click on gmail, for instance, it gives an "Untrusted Application Launcher" error. I have to click it from the application gray screen on my unity dock to be able to launch the Gmail web app. Where's the location of the real shortcuts for the web app which I can run by double-clicking?

Thx again.

---

### Post by madjr on 2010-11-29
what are you using to create these web apps shortcuts?

with nautilus file browser, you can create custom launchers or shorcuts inside your home folder.

you can also create "web apps shortcuts" with chromium/ google chrome.

personally i prefer to install **speed dial** extension for my browsers (firefox or chrome)

---

### Post by chaanakya_chiraag on 2010-11-29
That error appears because you are trying to run a .desktop file which does not have executable permissions.  All you need to do is right-click on the file, click Properties, go to Permissions, and click Execute.  Or, to make this less tedious, type these commands into a Terminal:
```

cd .local/share/applications
chmod +x *.desktop

```

---

### Post by chaanakya_chiraag on 2010-11-29
Oh, and you can also create App Shortcuts for Firefox using my handy Appify script
[http://ubuntuforums.org/showthread.php?t=1275363](http://ubuntuforums.org/showthread.php?t=1275363)

---

