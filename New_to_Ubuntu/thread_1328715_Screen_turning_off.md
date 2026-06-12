---
title: "Screen turning off"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by douglasja on 2009-11-16
My screen keeps turning off.

In my power management preferences I have set it to never put my display to sleep and I have the screen-saver deactivated.

But still after a few minutes of idleness the screen goes off. How do I amend this?

---

### Post by sisco311 on 2009-11-16
Open a terminal (Applications -> Accessories - Terminal)

and post the output of the following commands:
```
xset q
```
and 
```
cat /etc/X11/xorg.conf
```

---

### Post by skatinjj on 2009-11-16
Hope ou don't mind, I have the same issue.

output of xset q
```

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 2400
  DPMS is Enabled
  Monitor is On

```

and apparenntly I have no xorg.conf file on my system

---

### Post by sisco311 on 2009-11-16
> **skatinjj said:**
> Hope ou don't mind, I have the same issue.

output of xset q
```

DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 2400
  DPMS is Enabled
  Monitor is On

```

and apparenntly I have no xorg.conf file on my system

you can disable it, by setting the Standby, Suspend and Off time to 0:
```
xset dpms 0 0 0
```

or by disabling DPMS:
```
xset -dpms
```

[s]To make the settings permanent, create an xorg.conf file:
```
gksu gedit /etc/X11/xorg.conf
```
with the following content:
```
Section &#8220;ServerFlags&#8221;
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Log out and log back in, run *xset q*, the output should look like this:
```

DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```
[/s]
If for some reason you can not log in after creating the xorg.conf file, switch to virtual terminal (Ctrl+Alt+F1), log in and remove the file:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Switch back to the GUI (Ctrl+Alt+F7) and log in.

Or you can try Caffein: [http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page]("http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page")

---

### Post by skatinjj on 2009-11-16
alright thanks, i will try that.
  been using ubuntu for sometime and im just now trying to figure out all the different config files and how they work

---

### Post by douglasja on 2009-11-16
Okay then, question.

Why is all this necessary? Why isn't it doing what it is told from the menu?

---

### Post by skatinjj on 2009-11-16
unfortunately, I got dumped to tty and couldn't get to a gui after reboot.

Thanks for the help.

---

### Post by sisco311 on 2009-11-16
> **skatinjj said:**
> unfortunately, I got dumped to tty and couldn't get to a gui after reboot.

Thanks for the help.

After removing xorg.conf you should be able to boot in the GUI.
```
sudo rm /etc/X11/xorg.conf
```

---------------------------------------------------------------

You can add *xset dpms 0 0 0* to the startup applications, or use Caffein, both are workarounds, but they should work.

----------------------------------------------------------------

EDIT: I've found a minimal xorg.conf file which should work. I've edited my previous post.

---

### Post by cenzorrll on 2009-11-16
have you tried changing the screensaver properties?

much easier than messing with xorg.conf

Edit: oops, didn't read you're whole post. although i would double check to make sure anyway, i thought i had turned mine off and hadn't.

---

### Post by douglasja on 2009-11-16
> have you tried changing the screensaver properties?I have it deactivated.

This does seem like a real big fuss to get something done that should be real basic.

Checked and checked again, deactivated.

---

### Post by sisco311 on 2009-11-16
> **douglasja said:**
> I have it deactivated.

This does seem like a real big fuss to get something done that should be real basic.

You can add *xset -dpms* to the startup applications, that should disable the power saving feature.

---

### Post by skatinjj on 2009-11-16
> **sisco311 said:**
> you can disable it, by setting the Standby, Suspend and Off time to 0:
```
xset dpms 0 0 0
```

or by disabling DPMS:
```
xset -dpms
```

To make the settings permanent, create an xorg.conf file:
```
gksu gedit /etc/X11/xorg.conf
```
with the following content:
```
Section “ServerFlags”
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Log out and log back in, run *xset q*, the output should look like this:
```

DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

If for some reason you can not log in after creating the xorg.conf file, switch to virtual terminal (Ctrl+Alt+F1), log in and remove the file:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Switch back to the GUI (Ctrl+Alt+F7) and log in.

Or you can try Caffein: [http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page]("http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page")

I will try the program, none of that worked unfortunately.  I going to keep looking into this.

---

### Post by sisco311 on 2009-11-16
OKAY, i think I figured it out, the xorg.conf is a dead end.

Go to: System -> Preferences -> Startup Applications -> Add button

```
name:    no dpms
command: xset -dpms
comment: disable dpms
```

-> Add button
```
name:    no screensaver
command: xset s off
comment: disable screensaver
```

---

### Post by skatinjj on 2009-11-16
Found out that my screen saver was set to blank screen after 5 minutes so I disable it in system > preferences > screensaver

---

### Post by sisco311 on 2009-11-16
> **skatinjj said:**
> Found out that my screen saver was set to blank screen after 5 minutes so I disable it in system > preferences > screensaver

d'oh! still, if you don't disable dpms, then your monitor will go on standby mode after 20 minutes (1200 seconds) of inactivity.

---

### Post by skatinjj on 2009-11-16
Right. I wrote a bash script to run on startup to disable dpms for me.

I'll post the script and what to do in a few minutes for everyone, just a little busy with C++ right now.

---

### Post by skatinjj on 2009-11-16
This is what I did to run a script for disabling dpms at startup.

I created a document called dpms.sh with gedit and typed:
```

#!/bin/bash
xset -dpms
xset s off

```
then saved.  Gave the file permission to execute:
```

chmod a+x /where/file/is/saved/dpms.sh 
(to give everyone permission to execute)

or

chmod 700 /where/file/is/saved/dpms.sh 
(to give permission to read, write, and execute)

```
Then added the program to startup apps:
Go to system > Preferences > Startup Applications

Click add

Put in a title for the menu item you are creating

In the command field put:
```

cd /where/i/saved/script && ./dpms.sh

```

Click save and you are done.

---

### Post by douglasja on 2009-11-17
Really all this to stop the screen turning off when there is a menu that claims to do it?

---

### Post by sisco311 on 2009-11-17
> **douglasja said:**
> Really all this to stop the screen turning off when there is a menu that claims to do it?

Yes you have to run a command(*xset -dpms*) at startup to disable the X server's power saving feature. 

I agree we you, it should be disabled by default because Ubuntu uses gnome-screensaver.

---

