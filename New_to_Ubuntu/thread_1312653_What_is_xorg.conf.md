---
title: "What is xorg.conf?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by AlexOslo on 2009-11-03
I wondered what xorg.conf was (as referred to here):
[COLOR="DarkRed"]
 Re: Can't Detect Screen Resolution
You could try putting
Code:
                HorizSync       30-50
                VertRefresh     50-75
In the Monitor section of your xorg.conf.[/COLOR]
[http://ubuntuforums.org/showthread.php?t=1270707](http://ubuntuforums.org/showthread.php?t=1270707)

Alex

---

### Post by The Funkbomb on 2009-11-03
xorg.conf is the xorg configuration file.

You can edit this file by going into terminal and typing:

```
sudo gedit /etc/X11/xorg.conf
```

It will then ask for your password.

Once you enter your password, gedit will open and you'll be able to edit the configuration file.

---

### Post by Ampi on 2009-11-03
It's a configuration file: /etc/X11/xorg.conf

You can use it to change configurations for for example you screenr resolution. Sometimes Ubuntu doesn't automatically 'choose' the correct resolution and you can add this resolution to the xorg.conf file. 

Hope this helps a little..

---

### Post by anaconda on 2009-11-03
More clearly it is the configuration file for x-window manager. 

And now it is (almost) obsolete. You only need to edit it if you have problems with. screen/mouse/keyboard etc..

The autodetection is supposed to work very well now...

---

### Post by AlexOslo on 2009-11-04
> **The Funkbomb said:**
> xorg.conf is the xorg configuration file.

You can edit this file by going into terminal and typing:

```
sudo gedit /etc/X11/xorg.conf
```

It will then ask for your password.

Once you enter your password, gedit will open and you'll be able to edit the configuration file.

Helpful! I got into xorg.conf (which it seems I could also access by typing the location "/etc/X11" in Nautilus).

What can I do to access the "Monitor section" - as mentioned here (as I need to configure its resolution which wasn't autodetected, returning the message "unknown" for that parameter)?

[COLOR="DarkRed"]putting
Code:
HorizSync 30-50
VertRefresh 50-75
In the Monitor section of your xorg.conf.
[/COLOR]http://ubuntuforums.org/showthread.php?t=1270707

---

### Post by cariboo on 2009-11-04
If you accessed /etc/X11/xorg.conf from nautilus, you won't be able to do anything, as you aren't root. TO edit the file you need to open it as root to be able to save it, to do this press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
```

enter your password when asked. 

Add a section that looks like this to the file:

```
Section "Monitor"
Identifier     "Monitor0
HorizSync       30.0 - 59.9
VertRefresh     50.0 - 75.0
EndSection
```

Before adding the Horizontal and vertical refresh rates, check what they are on the Manufacturers web site, do you the rates in the above example without confirming what the rates are.

---

### Post by AlexOslo on 2009-11-07
> **cariboo907 said:**
> If you accessed /etc/X11/xorg.conf from nautilus, you won't be able to do anything, as you aren't root. TO edit the file you need to open it as root to be able to save it, to do this press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
```

enter your password when asked. 

Add a section that looks like this to the file:

```
Section "Monitor"
Identifier     "Monitor0
HorizSync       30.0 - 59.9
VertRefresh     50.0 - 75.0
EndSection
```

Before adding the Horizontal and vertical refresh rates, check what they are on the Manufacturers web site, do you the rates in the above example without confirming what the rates are.

Thanks, cariboo907!
Since, this has happened:
[COLOR="Red"]Graphic user interface (GUI) disappeared upon login - only get login text-prompt[/COLOR] 
[http://ubuntuforums.org/showthread.php?t=1314192](http://ubuntuforums.org/showthread.php?t=1314192)

At the text-prompt
```
[username]@[username]-desktop:~$
```
I tried 
```
sudo gksu gedit /etc/X11/xorg.conf
```
entered the password, and got
```
(gksu:1591): Gtk-WARNING **: cannot open display:

```

---

### Post by dunbrokin on 2009-12-12
I have the same problem....I am stuck at gtk warning cannot open display....how did you get around that?

---

### Post by AlexOslo on 2009-12-12
> **dunbrokin said:**
> I have the same problem....I am stuck at gtk warning cannot open display....how did you get around that?

I found no fix on this. Here's a related thread:
[http://ubuntuforums.org/showthread.php?t=1314192](http://ubuntuforums.org/showthread.php?t=1314192)

---

### Post by nadazero on 2009-12-13
You need to use non-graphical applications to edit the file because your graphical system is not running.
First go to your home folder and copy /etc/X11/xorg.conf as a safeguard in case something goes wrong:
[LIST]
[*]cd ~
[*]cp /etc/X11/xorg.conf xorg.conf.backup
[/LIST]
then
[LIST]
[*]sudo nano /etc/X11/xorg.conf
[/LIST]
make the changes,
and save the file:
[LIST]
[*]ctrl+o
[*]enter
[/LIST]
and exit nano:
[LIST]
[*]ctrl+x
[/LIST]

> **AlexOslo said:**
> Thanks, cariboo907!
Since, this has happened:
[COLOR="Red"]Graphic user interface (GUI) disappeared upon login - only get login text-prompt[/COLOR] 
[http://ubuntuforums.org/showthread.php?t=1314192](http://ubuntuforums.org/showthread.php?t=1314192)

At the text-prompt
```
[username]@[username]-desktop:~$
```
I tried 
```
sudo gksu gedit /etc/X11/xorg.conf
```
entered the password, and got
```
(gksu:1591): Gtk-WARNING **: cannot open display:

```

---

### Post by dunbrokin on 2009-12-13
Thanks that is how I did it in the end.

---

