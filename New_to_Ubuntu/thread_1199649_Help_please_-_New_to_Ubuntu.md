---
title: "Help please - New to Ubuntu"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Jedimaster007 on 2009-06-29
Hi,

I'm new to Ubuntu and have just installed Ubuntu 9.04 on my trusty laptop. I have been 'tweaking' various settings (as per various blogs and posts) and somehow have managed to get an error message:

Red 'no-entry' sign top right taskbar. When highlighted says: 

> An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.The error message was:'Error: Opening the cache (E:Type 'sudo' is not known on line 52 in source list /etc/apt/ sources.list, E:The list of sources could not be read.)'This usually means that your installed packages have unmet dependencies


I had been trying to install Google Chrome on Ubuntu (through a blog on the subject):
[http://ubuntuguide.net/install-google-chrome-web-browser-in-ubuntu](http://ubuntuguide.net/install-google-chrome-web-browser-in-ubuntu)  and I reckon I stuffed up trying to get it to work.

Any help would be appreciated. Thanks

---

### Post by VCoolio on 2009-06-29
Reading the error message it seems there is a wrong line in the file that lists your repositories. So open it in gedit with root permissions:
```
gksudo gedit /etc/apt/sources.list
```
scroll to line 52 and remove sudo if it is on that line. Check the other lines to see what it should look like. Or post your sources.list here if you're not sure what to do.

Edit: I read the howto following your link. Is it possible you added the key in sources.list? Did you paste the line "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5" there? That's not good, you should have entered that in a terminal, not in the file.

Edit2: the howto tells you to "sudo gedit" but opening graphical apps with root permissions should be done with gksudo, not sudo. So with gedit, nautilus etc use gksudo. Read [here]("http://www.psychocats.net/ubuntu/graphicalsudo") why.

---

### Post by techstop on 2009-06-29
> **VCoolio said:**
> Reading the error message it seems there is a wrong line in the file that lists your repositories. So open it in gedit with root permissions:
```
gksudo gedit /etc/apt/sources.list
```
scroll to line 52 and remove sudo if it is on that line. Check the other lines to see what it should look like. Or post your sources.list here if you're not sure what to do.

Edit: I read the howto following your link. Is it possible you added the key in sources.list? Did you paste the line "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5" there? That's not good, you should have entered that in a terminal, not in the file.

It seems the whole tutorial is poorly written. The very first instruction;

> First,edit the source.list file and add following to the end of the file:

sudo gedit /etc/apt/sources.list

Will get the unwary into strife.

---

### Post by VCoolio on 2009-06-29
Hm, you're right. So, jedimaster, undo anything you did in sources.list and get the .deb for chrome [here]("http://dev.chromium.org/getting-involved/dev-channel"). Download and click.

---

### Post by Jedimaster007 on 2009-06-29
Cheers guys -You're right 

I had pasted 'sudo' code on lines 52, 53 & 54 (in sources). Deleted and everything seems back to normal.

Good way of learning eh lol

---

### Post by Jedimaster007 on 2009-06-29
> **VCoolio said:**
> Hm, you're right. So, jedimaster, undo anything you did in sources.list and get the .deb for chrome [here]("http://dev.chromium.org/getting-involved/dev-channel"). Download and click.

And once again thanks for the link. That was a much easier way of installing it eh.:)

---

