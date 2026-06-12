---
title: "running firefox-3.0 runs firefox2.0"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by PetePete on 2010-01-14
ive tried removing firefox-2.0 and installing/reinstalling firefox3.0

but everytime i load firefox-3.0 from command line, firefox2.0 loads up.

also tried deleting my /home/user/.mozilla folder

any ideas?!

running kubuntu 8.04

tried to locate firefox2,here is results
```

pete@laptop:/usr/bin$ locate firefox-2
/etc/firefox/pref/firefox-2.js
/home/pete/.kde/share/apps/kicker/firefox-2.desktop
/home/pete/.local/share/applications/firefox-2.desktop
/home/pete/Desktop/firefox-2.desktop
/usr/share/app-install/desktop/firefox-2.desktop
/var/cache/apt/archives/firefox-2_2.0.0.21~tb.21.308+nobinonly-0ubuntu0.8.04.1_i386.deb
/var/lib/dpkg/info/firefox-2.list
/var/lib/dpkg/info/firefox-2.postrm
pete@laptop:/usr/bin$ 

```

---

### Post by PetePete on 2010-01-14
there was still a defun version running in memory
killall sorted that

---

### Post by Sef on 2010-01-14
I wonder if you have all the necessary dependencies to run Firefox 3.0.   

They are

> **Software Requirements**

   Please note that Linux distributors may provide packages for your distribution which have different requirements.   
[LIST]
[*]Firefox will not run at all without the following libraries or packages:
[LIST]
[*]GTK+ 2.10 or higher
[*]GLib 2.12 or higher
[*]Pango 1.14 or higher
[*]X.Org 1.0 or higher
[/LIST]
     
[*]For optimal functionality, we recommend the following libraries or packages:
[LIST]
[*]NetworkManager 0.7 or higher
[*]DBus 1.0 or higher
[*]HAL 0.5.8 or higher
[*]GNOME 2.16 or higher
[/LIST]
     
[/LIST]


I would recommend upgrading to a newer version of Ubuntu.

---

