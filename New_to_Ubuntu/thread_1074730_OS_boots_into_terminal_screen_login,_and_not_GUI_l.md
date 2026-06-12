---
title: "OS boots into terminal screen login, and not GUI login, after sorting out my 5.1audio"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Robw017 on 2009-02-19
HI,
Quite new to Ubuntu, using 8.04, the MythUbuntu version, and since I sorted out my audio issues to obtain 5.1 sound, from my Creative Audigy 2 ZS card, I restarted, and it boots up like normal, and selecting Ubuntu from the Windows/Ubuntu choice.
Instead of going to the GUI username login screen, it asks in a terminal like interface. I log in, and then I have to use "startx" to get to a GUI. Previously I had the GUI login and option to log into different environments. 
Any ideas, as of what I did to change this, and how to change it back?

Tried to compelete any installs with the following but return errors

"apt-get install -f"
[I]
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/I]

same with 

"apt-get update && apt-get dist-upgrade"

[I]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/I]


I use an nVidia fx5200, and from what I have read, it seems to be the cause of most of the issues here so worth mentioning that I use it. It is a PCI, as my motherboard also has a standard graphics card.
My hardware is a Dell 8300, with additional Creative Audigy 2 ZS and nVidia fx5200 PCI. Everythign else is pretty standard. the onboard audio and video are plugged up, by dell.

I dont know what to do to be honest.

---

### Post by Patricrawley on 2009-02-19
Put sudo in front of those commands and try again. You don't have root acess with those commands but you are asking it to do something with parts of the system that a regular user does not have access to which is why you need sudo to give you root acess to run these commands.

---

### Post by Robw017 on 2009-02-19
Cheers for that
Tired the sudo, and I am still getting the errors for the dist-upgrade code even with sudo.
First code is fine, executes and doesnt update anything.

---

### Post by pdtpatrick on 2009-02-19
produce the output of this

> cat /etc/inittab or type sudo runlevel

this will tell you what run level you are running on.

Also type 

> sudo apt-get install -f   ....this will fix the error you were getting above. After that then run :

> sudo apt-get update;sudo apt-get -y upgrade   or

> sudo apt-get update;sudo apt-get dist-upgrade

---

### Post by Robw017 on 2009-02-19
"sudo runlevel"

returns

"N 2"

tried all the other update commands, and the only thing outstanding was mplayer. Everthign else was up to date.

Still getting the terminal login screen, and use 'startx' to get to a GUI desktop environment.

Right, I can switch between all the TTY with BASH interfacing using ctrl + alt F*1-6*, but not F7, to GUI. Only way I get a GUI is typing "startx"

For a moment, I removed my display, presuming that it cudnt find my graphics card, but started the GDM again, somwhow.
I am taking commands here and there and sometimes things work, and sometimes, the command returns an error or unable to find or access etc.

"gksudo gedit /etc/X11/xorg.conf"

xorg file is attached.

---

