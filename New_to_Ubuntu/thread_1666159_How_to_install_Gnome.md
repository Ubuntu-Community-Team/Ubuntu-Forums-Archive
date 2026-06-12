---
title: "How to install Gnome"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Eternal_Light on 2011-01-13
Well hello.
 I am a Kubuntu 10.10 user and I was wondering if there was a way to install the gnome desktop inside my Kubuntu so I can access either KDE or Gnome from my login screen. My eye had caught someone, somewhere, some time ago that it was as simple as: "sudo apt-get install gnome   or   gnome*" or something similar but when I run these commands I get errors for broken packages or packet dependencies that cannot be satisfied.

So could you please tell me if it is possible for me to have Gnome and KDE in the same Installation? 

If I succeed in installing Gnome in my Kubuntu how far will i be from the original Ubuntu experience? What differences would there be?

Thank you in advance.
Dimitris.

---

### Post by mikewhatever on 2011-01-13
Try this:
```
sudo apt-get install ubuntu-desktop
```

or for the pure gnome

```
sudo apt-get install gnome-desktop-environment
```

---

### Post by Eternal_Light on 2011-01-13
I got prompted to select between gdm and kdm as a window/graphics manager or something. Said that X can't run them simultaneously so I picked kdm. Do you know the repercussions of this ?

---

### Post by Thras0 on 2011-01-13
from what i can tell gdm si for Gnome and kdm is for Kde :P

hope this **[COLOR="Red"][link]("http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/")[/COLOR]** helps.

also you may want to check this **[COLOR="red"][link]("http://ubuntuforums.org/showthread.php?t=447264")[/COLOR]** too. it explains what they are.

---

### Post by hansolo4949 on 2011-01-13
Yes, you should run sudo apt-get install ubuntu-desktop.

That WILL install some other applications that you might not want, so be careful with that:).

You should be careful with mucking around with the different desktop enviroments, because if you chose the wrong thing as the "default" you might mess something up.

if you want to remove it, just put in sudo apt-get remove ubuntu-desktop.

hansolo4949

---

### Post by Eternal_Light on 2011-01-13
thank you very much guys. I am experimenting with that stuff right now.

---

### Post by mikewhatever on 2011-01-13
> **Eternal_Light said:**
> I got prompted to select between gdm and kdm as a window/graphics manager or something. Said that X can't run them simultaneously so I picked kdm. Do you know the repercussions of this ?

None! With KDM the login window will be the familiar one you've been using.

---

### Post by Eternal_Light on 2011-01-13
well actually there was a problem. After rebooting I got just a white blinking cursor so i had to Ctrl+Alt+F1.

Doing sudo service kdm start it told me that kdm is already running but the F7 gave me the white cursor so i had to 
sudo service kdm stop
sudo service gdm start
and logged in with gnome. Don't know how to return to KDE. kdm seems unresponsive.


EDIT: Okay false alarm. For some weird reason after a second reboot kdm managed to launch normally.

---

