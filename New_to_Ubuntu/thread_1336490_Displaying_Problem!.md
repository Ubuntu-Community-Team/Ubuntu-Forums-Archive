---
title: "Displaying Problem!"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Tambooosh on 2009-11-24
Hey people, how are you all! I'm a newby in using Ubuntu.. I've just downloaded the last version of the system Ubuntu 9.10 from the official site and I've faced a few problems I hope they can be solved here..:D


1. I have an (Acer) monitor (LCD) but when I installed the system I could not re-monitor my screen to fit more than 800*600 or 640*480 so anyone knows how to change the display setting or is it just not supported by the system?:popcorn: I'm using Mercury Motherboard with injected Video Card nVidia..


Thanks

---

### Post by infestor on 2009-11-24
try installing nvidia-settings

```
sudo apt-get install nvidia-settings
```

---

### Post by Buuntu on 2009-11-24
Have you installed the proprietary drivers listed in System > Administration > Hardware Drivers?  If not, do so and restart - then let me know what happens.

---

### Post by Tambooosh on 2009-11-25
This What I've got..

---

### Post by Buuntu on 2009-11-25
Try running:
```
sudo apt-get update && sudo apt-get upgrade
```
and then checking again for proprietary drivers

---

### Post by Tambooosh on 2009-11-26
I did:
sudo apt-get update && sudo apt-get upgrade

and downloaded alot of files from the Internet, now when I go to the Hardware Drivers I got new thing:

---

### Post by Buuntu on 2009-11-26
Good, now activate the recommended version and restart.

---

### Post by Tambooosh on 2009-11-28
In fact I did activated the recommended version and downloaded some files from the internet and after restarting the computer the LOGIN screen was changed to resolution of 1024*742 but after writing in the password and logging in to the desktop the screen blinked and a message of "Input not Supported" showed up in a blank screen of the monitor, now I'm not capable of entering the desktop and I'm using Vista 'two systems'

I use Windows Vista on this monitor and it works perfectly.. :(
(Acer "AL 1717")

Any more aids?!

---

### Post by Buuntu on 2009-11-28
Darn.  Login to recovery mode and enter the root shell.  From there type: 
```
rm /etc/X11/xorg.conf
```
This will remove your xorg file, which isn't required and could have faulty settings.  If that doesn't work you might try removing the glx-185 version of nvidia and installing the 173 version.

Best of luck

---

### Post by Tambooosh on 2009-12-09
Thanks for your helping dear, I did what you said but
I'm not able to remove the file because of permission thing which I did not understand, though! I logged in as the main user to the system but it keeps refusing to remove the upper file because of permissions..
could you please give me a hand!
sorry for the questions BUT I'm newby in this field!
plus: how can I remove the former driver "glx-185" in order to install the 173 version..

Thanks alot!!

---

### Post by lotharmat on 2009-12-09
try 
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by ukripper on 2009-12-09
> **Tambooosh said:**
> logging in to the desktop the screen blinked and a message of "Input not Supported" showed up in a blank screen of the monitor, now I'm not capable of entering the desktop and I'm using Vista 'two systems'



do not remove your xorg.conf
you are getting this error because your horizontal and vertical refresh rates are not right for your detected monitor.

Press ctrl+alt+F1 at login screen and then put your username and password.
 Then, can you post output of this command:
```
nano /etc/X11/xorg.conf
```

---

### Post by Tambooosh on 2009-12-10
Well, I did just like you've said, and posted nano /etc/x11/xorg.conf
but a command prompt is showing up (GENU NANO) and I'm not sure of what I have to write in..
please more help guys! :(

---

### Post by DCrook on 2009-12-10
Hi:


I too just installed Ubuntu on an Acer Aspire 7720, it runs great except when I run games like anagramarama, the games consume my entire cpu resources. I was not sure if it is a display issue like the on in this thread or if it is a different issue,  I have duel processors, and a decent vid card,  any help would be appreciated

---

### Post by ukripper on 2009-12-11
> **Tambooosh said:**
> Well, I did just like you've said, and posted nano /etc/x11/xorg.conf
but a command prompt is showing up (GENU NANO) and I'm not sure of what I have to write in..
please more help guys! :(

it is capital "X" in X11 not small:
```
nano /etc/X11/xorg.conf
```

---

### Post by Tambooosh on 2009-12-12
Section "Screen"
             Identifier "Default Screen"
             DefaultDepth "24"
 
End Section
Section "Module"
             Load "glx"
End Section
Section "Device"
             Identifier "Defualt Device"
 
              
              Driver "nvidia"
              Option "NoLogo"                "True"
End Section
 
 
That is the outpot that I got...:popcorn: tough I did not understand a thing... NEXT?:(

---

### Post by Tambooosh on 2010-01-17
Hello people!
I'm still suffering with this problem! anyone, please, can get it solved?!

I appreciate it please!...

---

### Post by weichimaster on 2010-01-17
> **Tambooosh said:**
> Hello people!
I'm still suffering with this problem! anyone, please, can get it solved?!

I appreciate it please!...

I think a similar problem is discussed in this thread:

[http://ubuntuforums.org/showthread.php?t=1349553](http://ubuntuforums.org/showthread.php?t=1349553)

Try, at a terminal, trying the steps 2 to 4 in the first post.

---

### Post by weichimaster on 2010-01-17
**deleted**

---

