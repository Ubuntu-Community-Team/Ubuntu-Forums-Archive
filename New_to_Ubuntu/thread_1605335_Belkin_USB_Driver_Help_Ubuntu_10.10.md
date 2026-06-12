---
title: "Belkin USB Driver Help Ubuntu 10.10"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by DirtyPC on 2010-10-25
Belkin Ubuntu Driver

Hi first things first, this is the first ever time i've used ubuntu and i come from XP. I dont know nothing about anything and i am probably the biggest nooby user there is, so you'll have to be really clear and specific.
I have a belkin usb wireless adapter F6D4050, and its not recognised and i dont know how to get it work on ubuntu 10.10
I'm talking to you on windows as i dual boot and i cant connect my pc any other way besides this usb adapter!

any help!!!

---

### Post by Verbeck on 2010-10-25
hi there,
ndiswrapper is a program that can use windows drivers for linux. you can install it from the software center. after installation, you can find it under the system>administration menu, labelled "Windows Wireless Drivers"

if the driver file is in .exe format you can use windows or wine to extract the .inf file within. that's the file you'll need to load up in ndiswrapper

EDIT 1 : just noticed that you cant access the internet from ubuntu, so to install ndiswrapper, download the following from windows and open them in ubuntu

[http://packages.ubuntu.com/maverick/ndiswrapper-common](http://packages.ubuntu.com/maverick/ndiswrapper-common)
[http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9](http://packages.ubuntu.com/maverick/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/maverick/ndisgtk](http://packages.ubuntu.com/maverick/ndisgtk)


EDIT 2 : (if you're using another ubuntu just replace marverick with lucid,karmic)


EDIT 3 :as seen below, OP seemed to have solved the issue, however for future reference

[http://ubuntuforums.org/showpost.php?p=9460212&postcount=2](http://ubuntuforums.org/showpost.php?p=9460212&postcount=2)

---

### Post by DirtyPC on 2010-10-25
hi thanks, but I found a forum here that requires me to copy and paste some stuff into the terminal, and it now works like a charm! i must admit i am now going full ubuntu and not dual booting. Its fantastic! especially the visuals, i also heard the the intergrated ATI HD4200 card had loads of problems, but it worked out the box for me, very happy!

---

### Post by MooPi on 2010-10-25
How about we look for a native option first. The OP should look to the networking and Wireless section for help. Lots of folks willing and able to help with about every adapter.

[http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by DirtyPC on 2010-10-25
what i would like some help on is how to get nicer themes, like somthing similar to the mac toolbar + how to get more desktop effects,
 :)

---

### Post by Verbeck on 2010-10-25
> **harrylucas1 said:**
> what i would like some help on is how to get  nicer themes, like somthing similar to the mac toolbar + how to get  more desktop effects,
 :smile:

to get more effects than the default, install **ccsm** (the advanced one)and **compiz-fusion-plugins-extra**

then open settings>preferences>compizconfig Settings manager

for themes:
[http://gnome-look.org/index.php?xcontentmode=100](http://gnome-look.org/index.php?xcontentmode=100)

---

### Post by DirtyPC on 2010-10-25
> **Verbeck said:**
> to get more effects than the default, install **ccsm** (the advanced one)and **compiz-fusion-plugins-extra**

then open settings>preferences>compizconfig Settings manager

for themes:
[http://gnome-look.org/index.php?xcontentmode=100](http://gnome-look.org/index.php?xcontentmode=100)


hi thanks for that, on synaptic package manager all i can see is the simple one...

---

### Post by Verbeck on 2010-10-25
in synaptic the name is **Compiz configuration settings manager**
in the ubuntu software center, its **Advanced Desktop effects settings**
.....

---

### Post by DirtyPC on 2010-10-25
is there anyway to get a toolbar like a mac osx? i cant find it on there :/

---

### Post by Verbeck on 2010-10-25
if you mean the dock, there's **awn**, **cairo dock**, and [B]docky
[/B]
else,
[http://gnome-look.org/content/show.php/Macbuntu?content=129021](http://gnome-look.org/content/show.php/Macbuntu?content=129021)

---

### Post by DirtyPC on 2010-10-25
when i installed that theme, nothing changed.

---

