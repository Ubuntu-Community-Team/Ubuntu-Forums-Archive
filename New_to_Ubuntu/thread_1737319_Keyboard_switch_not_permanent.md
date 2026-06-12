---
title: "Keyboard switch not permanent"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by Settler on 2011-04-23
Hi all,

I would like to add a language for my keyboard apart from english. I have found an answer for this through this forum but I goes away when I reboot.

Does anyone know how can I fix this permanently?

P.S. Same with my screen resolution and refresh rate. (If anyone know this too I'd be please to have the answer)

Thank you in advance

---

### Post by Settler on 2011-04-23
As in my title...

I use

setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,gr

for switching between english and greek, it works perfectly until I restart the machine...when only english is my option?

any advice for making it work permanently?

thank you in advance

---

### Post by mörgæs on 2011-04-23
[http://ubuntuforums.org/showthread.php?t=1455877](http://ubuntuforums.org/showthread.php?t=1455877)

Please don't create multiple threads on the same topic.

---

### Post by Settler on 2011-04-23
I have checked these posts but it isn't working...

I have my bash file with the command inside... It work when I log-out/in but not when I restart...

---

### Post by cavalier911 on 2011-04-23
Add this to _/etc/X11/xorg.conf _:
Section "InputDevice"
       Identifier  "Keyboard0"
       Driver      "kbd"
      Option      "XkbLayout" "us,gr"
      Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection

---

### Post by Settler on 2011-04-24
I have created the file copied and pasted the above content to xorg.conf but even with this after the reboot of my machine only english is the option...

---

### Post by Settler on 2011-04-24
Latest addition...

If I reboot and open the LXTerminal... my languages increase to 2 (English, Greek)...

Any other way in order to avoid opening LXTerminal each time I restart the machine?

---

### Post by cavalier911 on 2011-04-24
```
sudo nano /usr/lib/X11/xorg.conf.d/05-evdev.conf
```
**Change**:
Section "InputClass"
Identifier "evdev keyboard catchall"
MatchIsKeyboard "on"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
EndSection
**to**
Section "InputClass"
Identifier "evdev keyboard catchall"
MatchIsKeyboard "on"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
[B]Option "XkbLayout" "us,gr"
Option "XKbOptions" "grp:alt_shift_toggle"[/B]
EndSection

---

### Post by Settler on 2011-04-24
It brings me up an error: "No such file or directory"

And it doesn't let me create the folder "xorg.conf.d"

Any idea?

---

### Post by cavalier911 on 2011-04-25
My previous instructions tested as working on Lubuntu 10.04 Lucid.
I don't run Lubuntu 10.10 and found location of evdev.conf by searching maverick package contents at [http://packages.ubuntu.com](http://packages.ubuntu.com)

Lubuntu 10.10 Maverick Meerkat :
/usr/share/X11/xorg.conf.d/10-evdev.conf

---

### Post by Settler on 2011-04-26
There is no such thing in my installation... Any idea of how could I create it?

---

### Post by cavalier911 on 2011-04-27
Not only do you need the -evdev.conf but it has to have the correct prefix number and be in the right location.
-evdev.conf is installed by a package in every release of **L**ubuntu.
Reinstalling the **correct** package will provide the file with the correct name and put it in the proper location.
I need the info below to tell you the correct package to reinstall.
Open lxterminal,run each command in the code box and paste the complete output in your reply.
The first command will output your version of Lubuntu.
The second command will output the name of the package on your system that provides evdev.conf 

```
lsb_release -a
```
```
dpkg -S  *evdev.conf
```

---

### Post by Settler on 2011-04-28
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick


xserver-xorg-core: /usr/share/X11/xorg.conf.d/10-evdev.conf

---

### Post by cavalier911 on 2011-04-28
> **Settler said:**
> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick


xserver-xorg-core: /usr/share/X11/xorg.conf.d/10-evdev.conf

_ Reinstall xserver-xorg-core which provides 10-evdev.conf _:
Connected to internet.
Open lxterminal.
```
sudo apt-get -y --reinstall install xserver-xorg-core
```_Open/Edit/Save 10-evdev.conf  in leafpad_:

```
sudo leafpad /usr/share/X11/xorg.conf.d/10-evdev.conf
```[B]

Change[/B]:
Section "InputClass"
Identifier "evdev keyboard catchall"
MatchIsKeyboard "on"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
EndSection
**to**
Section "InputClass"
Identifier "evdev keyboard catchall"
MatchIsKeyboard "on"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
[B]Option "XkbLayout" "us,gr"
Option "XKbOptions" "grp:alt_shift_toggle"[/B]
EndSection

---

