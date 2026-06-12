---
title: "open and Edit a .conf file - Blank page whe opens and will not save"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by adam lacey on 2009-07-21
Hi
 
I have installed xubuntu on to the harddrive of my old computer and I am trying to open xorg.conf file using this code:
 
"sudo mousepad /etc/X11/xorg.conf"
or
"gksudo mousepad /etc/X11/xorg.conf"
 
all I get it a Blank page with a red bar at the top warning me that I may harm my system if I edit it.
 
If I go directly to the file however by double clicking on the /etc/X11/ folders it does open with text in it, obviously I can't edit it as I do not have "sudo" rights. I can not save this file by going to it through the files and I can't even save the blank file using the terminal.
 
This is the case with other .conf files to.
 
I have looked everywhere an I can't work this out.
 
I have only been using Linux for a few days so I don't know much, so please be clear.

---

### Post by doas777 on 2009-07-21
hmmm. don;'t know. what do you get from:
```
gksu mousepad /etc/X11/xorg.conf
```


ahh just realized your using xfce. also do you get the same thing if you use nano instead of mousepad?

---

### Post by jeppewinther on 2009-07-21
Try this instead
```
gksudo gedit /etc/X11/xorg.conf
```

Remember to back it up before fiddling. Like so:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then if you mess it up, you have a known working conf file you can just revert back to.

Happy messing around.

---

### Post by JKyleOKC on 2009-07-21
Try just "gksu mousepad" from a terminal window. When you get the blank screen of mousepad with the red bar, pull down the File menu, use Open, and navigate to /etc/X11/xorg.conf which should get you what you want. After you do this once, you can use the "Open recent" choice to get directly back to the most recent files you have edited.

However note that since 8.04, the *buntu flavors have pretty much been bypassing xorg.conf in favor of autodetection, so making changes to this file may not have the effect you are hoping for. I wish I could tell you how to make it work as well as it used to, but so far have not found the magic potion...

---

### Post by adam lacey on 2009-07-26
Wow I managed to fix it. 
 
All I did was add these lines in below and it worked. I don't understand why though as I am new to all this.
 
> Sudo apt-get update
Sudo apt-get install xorg-driver-fglrx
Sudo depmod -a
 
When I added the second line of code it asked me for the CD I used to install it with in the 1st place but it was not seeing the CD when I put it in all the time. It did so something thought at one point. This process didn't finish and I put in the 3rd line, restarted my computer and it worked.
 
Could someone explain to me what each line I typed means and why this worked so i get a better understanding of Linux please?

---

### Post by Liolikas on 2009-07-26
sudo means do as super user.
apt-get is program used to manage other program installations something like windows CP add/remove programs just much more powerfull. 
update mans update information about latest software.
Typically upgrade is used later for upgrading Ubuntu with latest software and removing old (sudo apt-get upgrade)
install means install software and xorg-driver-fglrx is name of video drivers
depmod -a this is hardest to explain. Lets say it tell to Linux kernel something like: hey I have new drivers prepare to use them.
man depmod - for more technical description.

---

