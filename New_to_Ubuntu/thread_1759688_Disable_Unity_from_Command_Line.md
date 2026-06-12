---
title: "Disable Unity from Command Line"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by expatCM on 2011-05-16
An HP Pavilion was running 10.10 and the user decided to upgrade to 11.04.  This seems to have been sort of ok but there is a problem where I am asked for help.

The laptop was set to auto login and a message box appears saying that the  hardware is not suported and Unity cannot run, everything freezes. It needs to hold power off to free up the system.

So I pressed shift on boot to access a terminal and from there edited the gdm.conf to enable the login window.  My idea was to use that window to select the default desktop session and change it to gnome.  The trouble is that whilst the windows appears, the mouse freezes totally and the arrow keys also do not move.

From the command line how do you change the default login desktop manager from Unity back to gdm?

---

### Post by wildmanne39 on 2011-05-16
> **expatCM said:**
> An HP Pavilion was running 10.10 and the user decided to upgrade to 11.04.  This seems to have been sort of ok but there is a problem where I am asked for help.

The laptop was set to auto login and a message box appears saying that the  hardware is not suported and Unity cannot run, everything freezes. It needs to hold power off to free up the system.

So I pressed shift on boot to access a terminal and from there edited the gdm.conf to enable the login window.  My idea was to use that window to select the default desktop session and change it to gnome.  The trouble is that whilst the windows appears, the mouse freezes totally and the arrow keys also do not move.

From the command line how do you change the default login desktop manager from Unity back to gdm?
Hi, try unity --reset and give it about five minutes to run then restart the computer.:D

---

### Post by expatCM on 2011-05-16
thanks for the suggestion .... tried that and terminal reports --

"The program 'unity' is currently not installed.  You can install it by typing: apt-get install unity.

This seems to be a bit strange.   The splash screen is clearly 11.04 

So perhaps I should be rephrasing my request simply to how to set gdm as the default from the command line ....

---

### Post by vanadium on 2011-05-16
Start Ubuntu in Failsafe mode: press Shift to display grub, then select a "recovery" kernel. One of the options you get now is to start ubuntu in failsafe mode. This yields a classic gnome desktop, where you can disable the autologin option in the usual way.

Then reboot: gdm should load, click your user name and change the login session to "Classic gnome". After that, you can re-enable auto login if you wish.

---

### Post by expatCM on 2011-05-16
After reading the message that Unity was not installed I started to wonder what had I been asked to help with.

So I booted to a terminal with networking support and ran 

apt-get update
apt-get update
apt-get dist-update

and was amazed to see a huge number of updates to be installed.

So I installed and then on reboot Unity loaded but it was a bit of a mess,  however ..  this did then let me access the settings from the list of items under the shutdown button.  There I was able to select Ubuntu Classic and .. well happy ending.

Thank you for your comments.

---

