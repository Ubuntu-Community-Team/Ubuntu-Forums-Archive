---
title: "[SOLVED] 1s time user, how do I restore factory default settings?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by jburrell on 2008-12-27
I got this Sylvania G Book Meso with Ubuntu 8.04 installed and everything works great.  I am impressed with the speed and the ease in which Ubuntu operates.  

My problem is this: My wife is Italian so when I bought this the first thing we did when we turned it on was to change the language of the computer to ITALIAN and the keyboard to ITALY.  

The keyboard change has thrown everything off as there are numerous keys that are not in the same place as they are on a US keyboard layout.  I have gone into the settings and tried to change the keyboard back to USA layout but nothing seems to fix the problem.  We cannot use this pc for email now because the 'at' symbol cannot be found anywhere on the keyboard.

I want to take this pc back to the factory default settings like I just got it out of the box.  Is there a way to do that?

Any help is greatly appreciated as I've tried everything.

---

### Post by damis648 on 2008-12-27
You did try System>Preferences>Keyboard and changing the keyboard to 'Generic 105-key (Intl) PC' and the layout to 'USA'?

---

### Post by w4ett on 2008-12-27
look here: [https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

the actual command to use is:
```
sudo dpkg-reconfigure localeconf
```

---

### Post by damis648 on 2008-12-27
And to issue that, open a terminal (Applications>Accessories>Terminal) and paste it in.

---

### Post by jburrell on 2008-12-27
Yes, I tried that.  At this time the keyboard identified is the generic 105key intl and the layout is Italy.  I added the USA layout but that does not change anything. When I add the USA layout then there are two layouts (Italy and USA) on the menu.  While it is possible to remove the USA layout it is not possible to remove the Italy layout.  It seems the Italy layout is somehow embedded in the computer settings somewhere and it now is the default baseline setting.  Could this be because the first time we turned on the computer and it asked us which language and keyboard to use we selected Italy?  For this I just want to take the computer back to its factory settings.

---

### Post by damis648 on 2008-12-27
> **jburrell said:**
> Yes, I tried that.  At this time the keyboard identified is the generic 105key intl and the layout is Italy.  I added the USA layout but that does not change anything. When I add the USA layout then there are two layouts (Italy and USA) on the menu.  While it is possible to remove the USA layout it is not possible to remove the Italy layout.  It seems the Italy layout is somehow embedded in the computer settings somewhere and it now is the default baseline setting.  Could this be because the first time we turned on the computer and it asked us which language and keyboard to use we selected Italy?  For this I just want to take the computer back to its factory settings.

Open a terminal (Applications>Accessories>Terminal) and enter in:
```
sudo dpkg-reconfigure localeconf
```

---

### Post by jburrell on 2008-12-27
I learned how to do this and went to the terminal and entered the appropriate command.  The following text is what the terminal came back with 'Il pacchetto `console-data' non è installato e non è disponibile alcuna informazione.
Usa dpkg --info (= dpkg-deb --info) per esaminare i file archivio,
e dpkg --contents (= dpkg-deb --contents) per mostrarne il contenuto.
/usr/sbin/dpkg-reconfigure: console-data non è installato
anna@anna:~$ sudo dpkg-reconfigure localeconf
Il pacchetto `localeconf' non è installato e non è disponibile alcuna informazione.
Usa dpkg --info (= dpkg-deb --info) per esaminare i file archivio,
e dpkg --contents (= dpkg-deb --contents) per mostrarne il contenuto.
/usr/sbin/dpkg-reconfigure: localeconf non è installato

What this says is tht that the package was not installed because they are not available and there is no further information.  It then tells me to run a command to examine the file archive and show its contents.  Do I need to download something, some type of language package perhaps?

Thank you for your patience...

---

### Post by unutbu on 2008-12-27
Sorry, I don't know how to solve you problem, but this might help others recognize your problem more easily:
[http://ubuntuforums.org/showpost.php?p=6404851&postcount=16](http://ubuntuforums.org/showpost.php?p=6404851&postcount=16)

Edit: Please post the output of ```


cat /etc/X11/xorg.conf
xprop -root | grep XKB

```

too. The keyboard section would suffice, but if in doubt, you can post the whole thing.

There is a low-level way to change the keyboard layout. This is what I'm thinking you might try:
[http://ubuntuforums.org/showthread.php?t=898912](http://ubuntuforums.org/showthread.php?t=898912)
If you'd like to try it but would like some help, post the above commands and we can work from there.

---

### Post by w4ett on 2008-12-27
Here is the translation:

> USA dpkg --info (= dpkg-deb --info) in order to examine the rows the archives,
 and dpkg --contents (= dpkg-deb --contents) in order to show of the content.
/usr/sbin/dpkg-reconfigure: consul-giving is not installed
 anna@anna: ~$ sudo dpkg-reconfigure localeconf
 the package &#8220;localeconf&#8221; is not installed and some information is not available.
USA dpkg --info (= dpkg-deb --info) in order to examine the rows the archives,
 and dpkg --contents (= dpkg-deb --contents) in order to show of the content.
/usr/sbin/dpkg-reconfigure: localeconf it is not installed

Not perfect...this is a machine translation...but this says that localconf is not installed, so naturally it cannot be reconfigured.

---

### Post by mkvnmtr on 2008-12-27
When you go to Keyboard preferences you should see under Layouts USA and your Italian. You should be able to set one for default. It really won't matter which. Then when you right click on the panel at the top or bottom you should see an add to panel. Click on that and you should be able to find Keyboard indicator. Click on that and add it to your panel. Then you should be able to change keybords at will. I do this whih spanish and english with no problems. If you search for language support in the package manager you can install a lot of support for the two languages.

---

### Post by jburrell on 2008-12-28
> **unutbu said:**
> Sorry, I don't know how to solve you problem, but this might help others recognize your problem more easily:
[http://ubuntuforums.org/showpost.php?p=6404851&postcount=16](http://ubuntuforums.org/showpost.php?p=6404851&postcount=16)

Edit: Please post the output of ```


cat /etc/X11/xorg.conf
xprop -root | grep XKB

```

too. The keyboard section would suffice, but if in doubt, you can post the whole thing.

There is a low-level way to change the keyboard layout. This is what I'm thinking you might try:
[http://ubuntuforums.org/showthread.php?t=898912](http://ubuntuforums.org/showthread.php?t=898912)
If you'd like to try it but would like some help, post the above commands and we can work from there.
I first accomplished all the normal steps all have recommended through going into the keyboard and selecting the layouts, etc.  I have now run the command and the output is pasted directly below my text.  I feel that I am getting closer to a solution as I see 'IT' as a keyboard layout in the output report below:
anna@anna:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection
anna@anna:~$ xprop -root | grep XKB

Do I somehow need to edit the above string?

---

### Post by unutbu on 2008-12-28
At the terminal, type
```

gksu gedit /etc/X11/xorg.conf
```

Change 
```

Option "XkbLayout" "it"
```

to
```

Option "XkbLayout" "us"
```

Save and exit. Logout and log back in to make X re-read the xorg.conf file and make the change active. 

Gnome might throw up a window saying that it notices a conflict between what it remembers to be your X settings, and what it reads in xorg.conf. It asks you which set of settings (Gnome's or X's) you wish to use. Tell it you want X's settings.

---

### Post by jburrell on 2008-12-29
I accomplished the steps above and it worked like a charm!  I am now back to the normal US 105 keyboard layout.  Thank you to all who contributed, I appreciate it.  Just out of curiousity is it a "bug" that the GUI interface didn't work to change the keyboard back to the US layout?  

I must start a new thread now as I would like to change the language of the machine back from Italian to English.  

Once again, thank you to all!

---

### Post by jburrell on 2008-12-29
How do I mark this as "complete?" 
Thanks

---

