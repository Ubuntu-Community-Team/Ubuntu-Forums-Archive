---
title: "[SOLVED] No icons No ability to right click"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by ozwaldca on 2008-12-17
HI there

I am new to Ubuntu and Linux in general.

I am trying to install 8.10 (Intrepid) on an older Dell GX260 with an Intel 845G video card i have 768MB ram.

I go through the install and it seems to work fine. I proceed to do the reboot and all i get is a brown screen with no background picture or any icons.  I am unable to right click anywhere although the mouse appears to be working.

I have switched monitors thinking it was a resolution issue.  No success. I even booted into failsafe terminal mode and ran the xrandr command. it was set to the right resolution and the right refesh rate. Even booting into failsafe GNOME mode still does not produce any icons or usable desktop

What else can i try? i would love to get this working.

Cheers

---

### Post by xjcannonx on 2008-12-17
I am not an expert but I would imagine that it is something with the video card, maybe someone else can help??

---

### Post by ozwaldca on 2008-12-17
YEa that was my thoughts as well but i was able to log in to a failsafe terminal sessions and check the resolution refresh rate all looks good.

I looked at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel") and it says that it is supported... Intel 845G

cheers

---

### Post by fooman on 2008-12-17
have you tried the "xfix" option in recovery mode?

if not,  give that a shot.

---

### Post by redandgreen on 2008-12-17
Are your panels working? Is it just the desktop? When I got compiz working, the desktop ended up like that, because you have to tell nautilus - the file manager - not to manage it anymore. It basically involves going into gconf-editor (in the terminal) and then apps->nautilus->preferences. Have a look and see if 'show desktop' is ticked?

---

### Post by ozwaldca on 2008-12-17
Thanks for the ideas i will try them ASAP.

One thing i did notice is that when i start a failsafe terminal session, and run vi /etc/X11/xorg.conf  all the fields are blank.

I have tried running sudo apt-get install ubuntu-desktop as well but it says that is is already installed.

Cheers

---

### Post by ozwaldca on 2008-12-17
> **redandgreen said:**
> Are your panels working? Is it just the desktop? When I got compiz working, the desktop ended up like that, because you have to tell nautilus - the file manager - not to manage it anymore. It basically involves going into gconf-editor (in the terminal) and then apps->nautilus->preferences. Have a look and see if 'show desktop' is ticked?

I get the login screen which tells me that gnome is working, but after i log in all i see is the brown background.  no picture or anything.

---

### Post by ozwaldca on 2008-12-17
> **ozwaldca said:**
> I get the login screen which tells me that gnome is working, but after i log in all i see is the brown background.  no picture or anything.

I was able to start the gconf-editor and show desktop IS checked.

the fact that i can get to that menu screen proves that gnome is installed correctly no?

---

### Post by ozwaldca on 2008-12-18
SOLVED!!!

Here is the fix!

[http://ubuntuforums.org/showthread.php?t=990228](http://ubuntuforums.org/showthread.php?t=990228)
[http://ubuntuforums.org/showthread.php?t=990228]("http://ubuntuforums.org/showthread.php?t=990228")

---

### Post by ozwaldca on 2008-12-18
> **ozwaldca said:**
> HI there

I am new to Ubuntu and Linux in general.

I am trying to install 8.10 (Intrepid) on an older Dell GX260 with an Intel 845G video card i have 768MB ram.

I go through the install and it seems to work fine. I proceed to do the reboot and all i get is a brown screen with no background picture or any icons.  I am unable to right click anywhere although the mouse appears to be working.

I have switched monitors thinking it was a resolution issue.  No success. I even booted into failsafe terminal mode and ran the xrandr command. it was set to the right resolution and the right refesh rate. Even booting into failsafe GNOME mode still does not produce any icons or usable desktop

What else can i try? i would love to get this working.

Cheers

This is the line that fixed it for me:

The 845 video is not really supported in 8.10 and compiz does the special effects, which 845 can't handle.

---

