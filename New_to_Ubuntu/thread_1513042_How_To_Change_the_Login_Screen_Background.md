---
title: "How To Change the Login Screen Background"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by ramjet_1953 on 2010-06-18
[CENTER][B]Change Login Screen Background
in Ubuntu 10.04 LTS[/B][/CENTER]

At the graphical login screen you need to change to the TTY login screen. To do this enter ```
CNTL+ALT+F1
```

Login with your usual login name and password.

Enter the following two commands:
```
export DISPLAY=:0.0
```
```
sudo -u gdm gnome-control-center
``` (you will be prompted for your password).

Return to the graphical login screen. To do this enter ```
CNTL+ALT+F7
```
The graphical login screen will appear, superimposed by the gnome-control-center.

Choose [COLOR="Blue"]Appearance>Background[/COLOR]
Choose the background you wish and then close.

Your login screen will now have the background you have chosen.

If  the standard backgrounds are not to your liking, just place the image of your choice into the directory [COLOR="Red"]/usr/share/backgrounds[/COLOR] 

To do this open a root file browser by typing into a terminal ```
gksu nautilis
```

You will be prompted for your password.

Once the root file browser opens, just copy the image of your choice to [COLOR="Red"]/usr/share/backgrounds[/COLOR]

Enjoy!! :p

---

### Post by jtarin on 2010-06-18
Good commandline practice and hints on screen switching. 
Optionally you can install ubuntu-tweak and accomplish this, as well as change your host picture among other many ubuntu tweaks.

---

### Post by kerry_s on 2010-06-18
i just do this:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

---

### Post by jtarin on 2010-06-19
> **kerry_s said:**
> i just do this:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```
Really? Could you walk me through that so I can change my login screen so easily? Is it possible your thinking of the desktop background? Maybe I'm the one that is confused.:-k

---

### Post by kerry_s on 2010-06-19
> **jtarin said:**
> Really? Could you walk me through that so I can change my login screen so easily? Is it possible your thinking of the desktop background? Maybe I'm the one that is confused.:-k

it's just like changing the desktop, but what ever you change there happens on the login. you can do the theme, background, mouse, fonts.

if accessibility gets turned on you can turn it back off in
preferences-> keyboard

i only changed my mouse pointer & the background, to match what i'm using on the desktop.

---

### Post by jtarin on 2010-06-19
> **kerry_s said:**
> it's just like changing the desktop, but what ever you change there happens on the login. you can do the theme, background, mouse, fonts.

if accessibility gets turned on you can turn it back off in
preferences-> keyboard

i only changed my mouse pointer & the background, to match what i'm using on the desktop.
I gotcha now.....I was understanding that you could do both simultaneously. Such is not the case though.Good to know.

---

### Post by philinux on 2010-06-19
There's is a gui for this if anyone interested.

[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

---

### Post by warfacegod on 2010-06-19
> **philinux said:**
> There's is a gui for this if anyone interested.

[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

Great tool. I use it in 9.10. Unfortunately the last time I used it in Lucid (several weeks ago) it was still refusing to see any images that were added to the backgrounds folder.

With some minor work, this will be an excellent tool. I'd like to see it install by default in future releases replacing the current "Login Screen Settings", sorry thing that it has become.

---

### Post by blackaardvark on 2010-06-25
> **philinux said:**
> There's is a gui for this if anyone interested.

[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

Just tried this, and it's not working on Lucid as far as I can see.  This is pretty frustrating, I thought it would be pretty simple changing the log-in screen, but apparently not!

Can someone please shed some light on why this is so stonkingly difficult compared to other releases?

---

### Post by warfacegod on 2010-06-25
It's partly due to the images locations being hard coded. That's what I have read anyway.

If gdm2 didn't work for you, try Ubuntu Tweak. You can change the background with that.

---

### Post by JP121 on 2010-06-26
> **kerry_s said:**
> i just do this:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

This worked wonderfully for me.

---

