---
title: "what is the name of the app that intrepid uses to configure xorg?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by pluckypigeon on 2009-01-22
Does anyone know what the name of the program that allows xorg.conf to look like this in newer versions of ubuntu?

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 16
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Thanks in advance

---

### Post by Ben Page on 2009-01-22
If I correctly undrstan what are you asking, Its "gedit"

sudo gedit /etc/x11/xorg.conf

---

### Post by donkyhotay on 2009-01-22
Depends how bad your display is messed up, if you have a GUI then use gedit as recommended above. If X won't even start and you're stuck with the CLI then I would recommend nano (unless of course you're already familiar with vi or emacs).

---

### Post by KIAaze on 2009-01-22
[http://www.deesaster.org/progxorg.php](http://www.deesaster.org/progxorg.php) ?

---

### Post by pluckypigeon on 2009-01-22
> **donkyhotay said:**
> Depends how bad your display is messed up, if you have a GUI then use gedit as recommended above. If X won't even start and you're stuck with the CLI then I would recommend nano (unless of course you're already familiar with vi or emacs).

Sorry, I'm probably not making sense.

What I mean is...

In hardy and before you had to configure your xorg.conf where as now you don't.

I was wondering what intrepid has installed that hardy and before doesn't.

---

### Post by donkyhotay on 2009-01-22
Ah, thanks for clarifying. I'm not 100% certain but I think HAL does that now. I know HAL automatically configures alot of other hardware for you (which is why it's my guess) but I'm not certain it does X.

---

### Post by AnRa on 2009-01-22
> **Ben Page said:**
> If I correctly undrstan what are you asking, Its "gedit"

sudo gedit /etc/x11/xorg.conf[You should **never** use normal sudo to start graphical applications as root.](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by philinux on 2009-01-22
> **donkyhotay said:**
> Ah, thanks for clarifying. I'm not 100% certain but I think HAL does that now. I know HAL automatically configures alot of other hardware for you (which is why it's my guess) but I'm not certain it does X.

In Intrepid it's bullet proof x. It's supposed to get it right but it still sometimes fails on some hardware. So xorg.conf may need a tweak in these circumstances. There's xfix from the recovery menu which basically does the old 
 sudo dpkg-reconfigure -phigh xserver-xorg

and theres is also gnome-display-properties for screen res from the preferences menu.

---

### Post by donkyhotay on 2009-01-22
> **AnRa said:**
> [You should **never** use normal sudo to start graphical applications as root.](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

You need root access to edit the xorg.conf file. While many graphical applications can spawn other processes and be a serious liability (nautilus & firefox for example), gedit doesn't do much else besides edit text. I wouldn't recommend writing letters to uncle joe in gedit as root of course but for editing config files (and only that) it's fine.

//edit: nevermind, I just realized you weren't against running gedit with root access, just without gksudo.

---

### Post by donkyhotay on 2009-01-22
> **philinux said:**
> In Intrepid it's bullet proof x. It's supposed to get it right but it still sometimes fails on some hardware. So xorg.conf may need a tweak in these circumstances. There's xfix from the recovery menu which basically does the old 
 sudo dpkg-reconfigure -phigh xserver-xorg

and theres is also gnome-display-properties for screen res from the preferences menu.

I know there is a program that reads your system and determines the best X settings for you (unless you override with xorg.conf). I'm not certain of the name of that particular program and thats what the OP is asking.

---

### Post by philinux on 2009-01-22
> New features in Intrepid
X.Org server 1.5

The latest X.Org is available in Intrepid. This now also brings much better support for hot-pluggable input devices such as tablets, keyboards, or mice. At the same time this will allow the great majority of users to run without an "/etc/xorg.conf" file.


[http://www.ubuntu.com/getubuntu/releasenotes/810#X.Org%20Input%20Devices](http://www.ubuntu.com/getubuntu/releasenotes/810#X.Org%20Input%20Devices)
X.Org Input Devices

The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system).

---

### Post by bodhi.zazen on 2009-01-22
xserver xorg (X) has significantly changed the way xorg.conf is used and xorg.conf is now depreciated.

The good news, many hardwar configurations work out of the box with minimal or no user input.

The bad news, if the auto detection fails, then most of the old tools such as 

dpkg-reconfigure -phigh xserver-xorg, manual edits, and such often fail as well.

It really depends on your hardware. For example, with nvidia cards, you install the nvidia driver and (thank god) gksu nvidia settings still works.

So, can you give us more information ?

what hardware do you have ? videocard and monitor(s)

---

### Post by pluckypigeon on 2009-01-22
> **bodhi.zazen said:**
> 

So, can you give us more information ?

what hardware do you have ? videocard and monitor(s)

I didn't really want to disturb this post with my problem but I'm having a problem with Xorg for Arch.

It does work but badly without a xorg.conf.

The monitor is Iiyama Prolite E430 LCD with
Intel Corporation 82845G/GL[Brookdale-G] Chipset graphics card.

...Which work fine with Intrepid

---

### Post by bodhi.zazen on 2009-01-22
> **pluckypigeon said:**
> I didn't really want to disturb this post with my problem but I'm having a problem with Xorg for Arch.

It does work but badly without a xorg.conf.

The monitor is Iiyama Prolite E430 LCD with
Intel Corporation 82845G/GL[Brookdale-G] Chipset graphics card.

...Which work fine with Intrepid

:lolflag:

I am not familiar with that card, but Intel recently open sourced some of their drivers. Details / instructions are available w/ google search / on the intel site.

I suspect Arch has a more recent version of Xorg and as you know it ia a "rolling release" so it is impossible to downgrade (unless you have the old package or compile with an ArchBuild which may be difficult with Xorg).

---

