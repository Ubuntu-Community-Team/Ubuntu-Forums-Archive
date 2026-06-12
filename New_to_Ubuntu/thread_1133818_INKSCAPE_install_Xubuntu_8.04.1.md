---
title: "INKSCAPE install Xubuntu 8.04.1"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by SnaveDogg on 2009-04-23
I am a newb so be nice....I installed xubuntu last night on an old junker HP Pavilion. All went well with that. Now I'm trying to install a version of inkscape, a vector graphics application.
#1, I do not know where to find a download that will work, and 
#2 installing new software/applications is foreign to me on this OS.

Can anyone help me with this? This computer is for my 7 year old daughter to play on, and she loves graphics. I installed inkscape on my Windows machine, and it is great. I tried using the same .exe setup file that I used on the Windows machine to get it installed on the Xubuntu machine. Apparently, that is something new I'm gonna have to learn. I found that you can't just double click it and have it start up the install process. I tried right clicking and "install" but that didn't work either.

Then I found something online with a .gz on the end, and I couldn't get that to work either. It involved adding a couple of lines to an existing file in the etc/apt folder. I added the lines, but it wouldn't allow me to save it.

ANYWAY....

I just want to get inkscape, and have no idea how.

Thanks in advance.

---

### Post by Sir Jasper on 2009-04-23
Hi,

Clear your desktop using the minmise button (top right of this screen).

Right click to see a menu. Click on system (near the bottom). Then click

Synaptic Package Manager. Enter your password and press Return.

Click on Search and in the dropdown box type inkscape and click the button.

When Inkscape shews click the empty box and hit any "apply" button(s).

It will install automatically.

When it is escape and bring up the menu again (with a clear screen) and try looking under Graphics.

Let us know how it goes.

My regards

---

### Post by RichardLinx on 2009-04-23
Hello SnaveDogg! I'm surprised you haven't received an answer yet as the solution to your problem is very simple. :) Ubuntu and Windows are two vey different operating systems. Trying to run an .exe file on Ubuntu is like trying to play an XBOX game on a playstation - It won't work. Instead of ".exe" Ubuntu uses a ".deb" file format (or "package" if you prefer)

To install Inkscape you just double click on the .deb package and click "Install".

I found an Inkscape .deb file for you: [http://ubuntuforums.org/showthread.php?t=352561](http://ubuntuforums.org/showthread.php?t=352561)

Just right click and select "save file as" and you'll have it. 
The .tar.gz was the INkscape file as well but It hadn't yet be compiled, it's possible it will work if you just right click > extract file.

Usually the latest Ubuntu software is uploaded as a .deb to this site: [http://www.getdeb.net/browse.php](http://www.getdeb.net/browse.php)

I'll also reccomend Tux Paint to you since your daughter is seven and will probably have some fun with it: [http://www.tuxpaint.org/](http://www.tuxpaint.org/)

And last reccomendation: "CrunchBang Linux" It's an unofficial Ubuntu derivative that is even lighter on resources then Xubuntu, if you find Xubuntu to be a bit sluggish with your machine.

If you need any more help feel free to ask. :)

---

### Post by RichardLinx on 2009-04-23
> **Sir Jasper said:**
> Hi,

Clear your desktop using the minmise button (top right of this screen).

Right click to see a menu. Click on system (near the bottom). Then click

Synaptic Package Manager. Enter your password and press Return.

Click on Search and in the dropdown box type inkscape and click the button.

When Inkscape shews click the empty box and hit any "apply" button(s).

It will install automatically.

When it is escape and bring up the menu again (with a clear screen) and try looking under Graphics.

Let us know how it goes.

My regards
Doh! Of all things I forgot to mention synaptic.

Alternatively you can type into the terminal:
```
sudo apt-get install inkscape
```

---

### Post by SnaveDogg on 2009-04-23
Thanks for all the help...big-time thanks!!


by the way, how do you get to the terminal into which I can type code?

---

### Post by RichardLinx on 2009-04-23
Your on Xubuntu so I'm not 100% sure it will be the same as Ubuntu. For me it's in Applications > Accessories > "Terminal". Though I have it set as shortcut "Alt + Enter" since I use it frequently. ;)

---

### Post by Sir Jasper on 2009-04-23
Hi again,

A final thought - if, after shutdown (quit from the menu), your daughter wants to reopen where she left off then click the Save Session box.

My regards

---

### Post by Claritux on 2009-04-23
I think we should mention add/remove programs. You can simply go to Applications->System->Add/Remove... Make sure that the dropdown menu at top shows "All available applications", and search for Inkscape. Doubleclick on it to mark it and choose "Apply changes". Type in your password, hit enter and you're done!

---

### Post by SnaveDogg on 2009-04-23
I tried the add/remove option. Inkscape was not there.
I haven't got this machine on an internet connection right now, so I may have to at least temporarily make a connection so as to quickly get the configuration right.

I installed in this machine a while back, a PCI USB card. Right now, Xubuntu isn't talking to it. It is talking to the motherboard based USB connector though, but it is the old/slow version. When I connect to the internet, will I be able to get drivers for that piece of hardware via "update" or am I going to have to do some more extensive driver-searches to get that hardware talking to the OS?

---

### Post by RichardLinx on 2009-04-23
> **SnaveDogg said:**
> I tried the add/remove option. Inkscape was not there.
I haven't got this machine on an internet connection right now, so I may have to at least temporarily make a connection so as to quickly get the configuration right.

I installed in this machine a while back, a PCI USB card. Right now, Xubuntu isn't talking to it. It is talking to the motherboard based USB connector though, but it is the old/slow version. When I connect to the internet, will I be able to get drivers for that piece of hardware via "update" or am I going to have to do some more extensive driver-searches to get that hardware talking to the OS?

It's quite possible that an update will fix the issue, though it's not guaranteed. If you're running Xubuntu on the machine and it hasn't been updated I would advise it, the reason the USB port isn't working could be because of a bug that wasn't notice until after release. It's likely that if you update a kernel patch will fix the issue.

It's unlikely but you may be able to enable the driver by going to System > Administration > Hardware Drivers. (Again, I'm unsure if it's the same on Xubuntu as it is on Ubuntu).

---

### Post by SnaveDogg on 2009-04-23
> **RichardLinx said:**
> It's quite possible that an update will fix the issue, though it's not guaranteed. If you're running Xubuntu on the machine and it hasn't been updated I would advise it, the reason the USB port isn't working could be because of a bug that wasn't notice until after release. It's likely that if you update a kernel patch will fix the issue.

It's unlikely but you may be able to enable the driver by going to System > Administration > Hardware Drivers. (Again, I'm unsure if it's the same on Xubuntu as it is on Ubuntu).


well, now I'm having Massive problems trying to connect to the internet....I am beginning to HATE Xubuntu..
so far nothing but trouble...this has gone on for 3 days...still have a frustrated litle girl who just wants her computer to work.

---

