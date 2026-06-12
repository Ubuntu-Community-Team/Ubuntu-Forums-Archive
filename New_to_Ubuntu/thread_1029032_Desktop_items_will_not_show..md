---
title: "Desktop items will not show."
date: 2009-01-03
forum: New to Ubuntu
---

### Post by PleaseEnjoyThis on 2009-01-03
I restarted my computer, switching from my windows partition to my ubuntu partition, and when I logged onto ubuntu, the items that were previously on my desktop are now not on my desktop.   They are still in my desktop folder tho.  I even tried dragging something onto the desktop, and the desktop just rejects it.   Also, usually when you click and drag you get that box thingy, which you can then highlight things with, that also is not working.

All help appreciated.  Thank yoU!

---

### Post by zvacet on 2009-01-03
In terminal

```
gconf-editor
```

and then **apps>nautilus>desktop** and see if volumes visible is checked.If that doesn´t help try** apps>nautilus>preferences>check show desktop**

---

### Post by chronographer on 2009-01-03
+1 above method... there is a little known configuration editor which will fix this for you. also holds options for disk insertion default actions etc.

---

### Post by PleaseEnjoyThis on 2009-01-03
Both are checked.   

I dont understand how something like this would just randomly occur.  hmm:/

---

### Post by Michael.Godawski on 2009-01-03
hi,

When you say you have checked the options in the gconf-editor, and they volumes are still not showing up, perhaps it is a graphical issue? Something wrong with the displaying of the desktop background; because you say you cannot create that highlighting box...

Do you use compiz? What is your graphic card?
Try to restart the gnome desktop via terminal:
```
sudo /etc/init.d/gdm restart
```

It a wild guess...

---

### Post by PleaseEnjoyThis on 2009-01-03
i use compiz.  

I have a nvidia.  

When I used your command something went wrong and i was stuck in the shell, i then had to log into root and reboot my computer.  I didn't catch what exactly happened, i could if needed, but i would then have to restart again.

---

### Post by Michael.Godawski on 2009-01-03
Try to disable compiz and restart the machine if necessary.

Can you also post the output of your xorg.conf file:

```
cat /etc/X11/xorg.conf
```

---

### Post by PleaseEnjoyThis on 2009-01-03
How do i turn compiz off?  I turned off all my desktop effects, and i will now restart my computer.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by PleaseEnjoyThis on 2009-01-03
nothing new on restart.

---

### Post by PleaseEnjoyThis on 2009-01-04
Randomly started working once I booted up my computer just now. 

Thanks though for everyone's time!

I hate random glitches like this.

---

