---
title: "cannot get past login after fresh install"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by claskow on 2010-08-06
Good you morning tech heads, completely new Ubuntu user here. I did the desktop download from this site and burned the image to Cd and had a sucessful install. However i cannot get past the login screen to experience all that Ubuntu or Linux (if that is correct) has to offer. There are some posts here describing what to do and i have tried them to no avail. I am not that familiar with the terms but i see no option for the "GRUB" or "GRM" (if that is correct). i tried reinstalling, still nothing. I did see some info about a graphics card issue but mine seems to be compatible. i did check the disc for errors, i totally formatted the hard drive, nothing seems to work and i ahve been trying for two days. Please help.

---

### Post by utilitytrack on 2010-08-06
One tech head speak you: recall the login and password that you specified during install the system and simply type it into login screen. Note: you will not see the password during input. Also: what version of Ubuntu you downloaded and installed?

---

### Post by sandyd on 2010-08-06
> **claskow said:**
> Good you morning tech heads, completely new Ubuntu user here. I did the desktop download from this site and burned the image to Cd and had a sucessful install. However i cannot get past the login screen to experience all that Ubuntu or Linux (if that is correct) has to offer. There are some posts here describing what to do and i have tried them to no avail. I am not that familiar with the terms but i see no option for the "GRUB" or "GRM" (if that is correct). i tried reinstalling, still nothing. I did see some info about a graphics card issue but mine seems to be compatible. i did check the disc for errors, i totally formatted the hard drive, nothing seems to work and i ahve been trying for two days. Please help.

you login with the username and password you set while installing ubuntu

---

### Post by claskow on 2010-08-06
[COLOR=black][FONT=Verdana]Thank you both for the replies. i know this seems like a simple thing but i can't get it to work at all. The login doesn't say Authentication Failed. It looks like it wants to log me in but does not. It goes to an infinite loop type thing that I have seen some people talk about. It looks like it wants to let me in but the screen goes black and back to the login screen. I seem to have no other option for anything else. Standing by.[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by utilitytrack on 2010-08-06
Hmm. It's strange. Try install other Ubuntu: Kubuntu or Xubuntu (I strong recommend last), it's will be more simple way.

---

### Post by ranch hand on 2010-08-06
You have not told us the version you are using so I will assume 10.04 (information is a good thing in a post).

If you have more than one OS on your box you should be seeing the menu.  There is an option for "recovery mode".  I would boot to that.

First use the option "dpkg fix broken packages".  This will probably will not help but it could and is easy.  When that finishes you will be directed back to the recovery menu.

Go with the first option "return to normal boot".  This should give you a text login.  Enter user name.  Enter password.  You will get another prompt after that.  Type;
```

startx

```
This should get you to the desktop.

The fix broken packages option should have updated the system but I would go to synaptic (System>Administration>Synaptic Package Manager) hit the refresh button, click (lower left on screen) on the status button and see if there are any upgradeable packages.

10.04 still has some problems and is upgraded often.  Your problem may be solved with an upgrade.

The boot manager is a problem for a few folks but I do not think that this is your problem.  See shat the stuff above does and reboot and see if it works.  If not get back in through recovery and past back here.

---

### Post by claskow on 2010-08-06
[COLOR=black][FONT=Verdana]sorry 'bout that, it is 10.04. and I had the drive formatted with Windows but I erased everything and started on a fresh drive. I see no menus at all during boot up so I don't see where I could enter and commands. I have tried hitting escape similar to F8 safe mode and I sorta see something helpful but it goes by so fast I can't make it out but it looks like it would be helpful. I have no way of accessing the recovery mode. I just finished downloading Xubuntu and will give it a try. I would still like to know why the original didn't work.[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by Elmer Fudd on 2010-08-06
At the login page there should be a panel on the bottom with a 'sessions' selection. It will not be visible until you select a user and the password dialog is visible. Select "xterm" and proceed with the instructions from rich-hand.

Let us know

Just realized that his instructions depend on you being in recovery mode so.. I think (corrections appreciated)
from the terminal that you shoud be in...
sudo apt-get check
sudo apt-get update
sudo apt-get upgrade

startx

---

### Post by ranch hand on 2010-08-06
If you only have one OS on your box you will not see a menu.  You need to press the shift key to get to it.

This will be the same on Xubuntu or any other distro using grub2 (great bootloader).

---

### Post by Elmer Fudd on 2010-08-06
> **ranch hand said:**
> If you only have one OS on your box you will not see a menu.  You need to press the shift key to get to it.

This will be the same on Xubuntu or any other distro using grub2 (great bootloader).

With one OS you won't get a Grub or Burg menu.
You should still be able to select a "session" from the login screen. That's how you pick between desktops like "Gnome Safe mode" or any other desktop that you have installed. My 10.04 was an upgrade but I believe that in addition to Gnome Safe Mode, that xterm is one of the defaults available.

---

### Post by ranch hand on 2010-08-06
Yes xterm should be there.

It is nice, however, to be able to get to the recovery menu as it is good for many things.  If, for example, the problem here is with the GDM login nothing there may work correctly.  Recovery by passes those problems along with any problems that may have roots in the boot manager (plymouth).

---

### Post by utilitytrack on 2010-08-06
We filled him the answers :))

---

