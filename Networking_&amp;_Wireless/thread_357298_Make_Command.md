---
title: "Make Command"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by FreakShow! on 2007-02-09
Hi,

I was wondering if soemone might be able to help. I have a Gateway 9300 Solo Laptop with a Buffalo Airstation WiFi card. To get it to work I went to get Ndiswrapper via my main PC, but when I try and "make install" the make command is not found.

I have since found that to get this to work I need to download some packages and there lies the problem, to get it installed I need the internet and to use the internet I need to get it installed.

This laptop does not have an ethernet port so what do I do??

Anywhere i can get all the packages I need via my main PC and transfer it via pen drive?

TIA :)

---

### Post by FreakShow! on 2007-02-09
I've been searching more and found this:

[http://www.neowin.net/forum/lofiversion/index.php/t423836.html]("http://www.neowin.net/forum/lofiversion/index.php/t423836.html")

However, I seem to also not have the dkpg command. If that's easier to isntall?

EDIT: Sorry for double post, I'm used to another forums where posts are merged automatically.

---

### Post by Floppyjoe on 2007-02-09
You can install ndiswrapper from the install cd if you go to System/Administration/Synaptic Package Manager. Then click on Edit/Add-CDROM. Then click Reload. Then Search for Ndiswrapper.
I think.

---

### Post by DirtDawg on 2007-02-09
I had a similar problem with my laptop. I put the live/install CD in my cd drive, then went to System>Administration>SoftwareProperties and pressed the "Add CD ROM" button. This allowed the Live CD to act as a repository. From there, I was able to install ndiswrapper without an internet connection. You may even want to see if the package 'build-essential' is on the Live CD "repo", as I'm not sure myself. Build-essential is the package you need for compiling.

HOWEVER, it should be noted that the ndiswrapper version on the CD is very likely not the most up-to-date version out there. This likely means very little, but it could cause some mischief.

Further, you should **definitely** have the dpkg command installed already. Try just typing 'dpkg --help' (without quotes) in the terminal. You should get a list of possible options. If you get something like "command not found", then you have an issue.

Good Luck.

---

