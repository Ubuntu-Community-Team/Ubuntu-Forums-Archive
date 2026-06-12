---
title: "new to ubuntu"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by mr_sausage on 2010-12-03
hey, new to ubuntu.
used mac and windows os in various forms for years.
but have decided to give ubuntu a go, as heard its different and quick.
am using netbook edition, and found it a bit alien.
so trying to get my head around some of the Ubuntu specifics.
Don't like the Unity thing much.
Like big icons and big full desktop launcer,
but don't like the sidebar launcer that flashes on and off when mouse rolls over.
find that very upsetting.
especially when browsing.
so have decided to download desktop instead.
as this surely more suitable.
Plan to set up a ripped down pc specifically for email and web browsing,
so may install netbook on that one, but will likely to tailor it by getting rid off all unessential software,
and only include email/internet/basic office apps for document viewing.
plus as many security apps as possible in order to make the platform as robust as possible.
Anyway, thanks to the developers for the software. You guys are hero's. for sure.
and very very clever indeed!
Thanks
:-)

---

### Post by fooman on 2010-12-03
the normal desktop version (gnome) should already be installed along with your netbook interface....you just have to choose it at the login screen.

when you are at the login screen,  click once on your user name,  then look at the bottom of the screen.  click the up/down arrows next to "ubuntu netbook edition" and some choices will pop up....choose "ubuntu desktop edition"

hope that helps.

---

### Post by Bölvaður on 2010-12-03
As fooman mentioned you should go get GNOME (or ubuntu) desktop from the synaptic package manager. And he said how you can choose between going to the netbook desktop or ubuntu/gnome.

> **mr_sausage said:**
> 
plus as many security apps as possible in order to make the platform as robust as possible.
try to have as few as you can if you want to have it robust ^^ few is more :P
None is best, think most of us have nothing.

---

### Post by mr_sausage on 2010-12-03
hey,
thanks very much for all help.
:-)

---

### Post by uRock on 2010-12-03
Hello and welcome to the forums. 

If you do a lot of file sharing via email or what have you, then you may want to consider installing clamav. To install Clam AV, just go in your menu to Ubuntu Software Center and enter clamav in the search field to install it.

I use the built in firewall. To do this open a terminal via Applications> Accessories> Terminal in the menu, then copy and paste this command which will set the built in firewall to block incoming connections. This will not effect any of your usability.```
sudo ufw enable
```

If you need to be able to open ports to share a printer or share folder, then install GUFW via Ubuntu Software Center and it will allow you to set rules for different ports and protocols.

---

### Post by jplo on 2010-12-03
If you find that you cannot access Ubuntu Desktop Edition (not unity netbook) try using the Synaptic package Manager (as mentioned by [Bölvaður]("http://ubuntuforums.org/member.php?u=338535")) by clicking applications (grey icon with a Pencil and Set Square at bottom of unity) and searching for 'synaptic' in the search box. 

Open 'Synaptic Package Manager' from the list, and then there is another search box on it's toolbar (underneath the menu bar), search for ubuntu-desktop, right click on the 'ubuntu-desktop' package in the list, and then click 'Install this package'. Now click 'Apply Changes' on the toolbar and Synaptic will download and install any missing packages (Software for Ubuntu comes in debian **packages** (*.deb files)). Then you can access Ubuntu Desktop from the login screen as mentioned in the previous comment by [fooman]("http://ubuntuforums.org/member.php?u=229348").

Hope this helps!:KS

SIMPLER METHOD
You can also do the installation through the Ubuntu Software Centre, which is an icon that looks like a shopping bag with a globe in it. the search bar is at the top-right, search 'ubuntu-desktop' and 'The Ubuntu desktop system' should come top of the list (ensure that you are scrolled up to the top and have clicked 'Show x technical items', which can be found at the bottom of the software centre.

---

### Post by uRock on 2010-12-03
Or open a terminal and run **sudo apt-get install ubuntu-desktop**, which will install the ubuntu-desktop package.

---

### Post by jplo on 2010-12-03
> **uRock said:**
> Or open a terminal and run **sudo apt-get install ubuntu-desktop**, which will install the ubuntu-desktop package.

Fair enough.

---

