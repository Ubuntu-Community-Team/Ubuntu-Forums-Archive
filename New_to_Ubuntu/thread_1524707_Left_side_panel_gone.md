---
title: "Left side panel gone"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Kvantftw on 2010-07-05
Hi! I recently installed Netbook remix onto my EEE 1201T, and it was going great.

Then one day I shut it down after failing to install my first tar >.> Ya my first time using this btw.

Anyway It seemed fine, I turned it back on and the left side panel that shows all the applications and settings and games is gone.

How do I get this back =((

---

### Post by mikewhatever on 2010-07-05
Are you saying that only the left side of that window is missing and everything to the right of the panel is not?

---

### Post by Kvantftw on 2010-07-05
There never was a right one, I dont think netbook remix has the right panel only the left one and the top which shows the time and stuff.

---

### Post by mikewhatever on 2010-07-05
I never said there was the right panel, however, if you look at a screen shot of the netbook edition, there is stuff to the right. Once again, **not the right panel**, but launcher icons and some folders.

---

### Post by kerry_s on 2010-07-05
> **Kvantftw said:**
> Hi! I recently installed Netbook remix onto my EEE 1201T, and it was going great.

Then one day I shut it down after failing to install my first tar >.> Ya my first time using this btw.

Anyway It seemed fine, I turned it back on and the left side panel that shows all the applications and settings and games is gone.

How do I get this back =((


what did you install?
try pressing-> **alt+f2**
type-> **netbook-launcher**

---

### Post by Kvantftw on 2010-07-05
No those arnt there anymore either =((

pretty much just a picture with the top panel atm, have to alt+f2 to open anything

---

### Post by Kvantftw on 2010-07-05
> **kerry_s said:**
> what did you install?
try pressing-> **alt+f2**
type-> **netbook-launcher**

netbook-launcher didnt work =(

It was World of goo I followed the instructions which it said to

"- unpack (tar -xjpf file)
- if wanted, move somewhere appropriate
- make executable (chmod +x /path/to/WorldOfGoo/WorldOfGoo*)
- run (cd /path/to/WorldOfGoo/ && ./WorldOfGoo)"

Not sure if the two are related but I dont recall changing anything else before hand.

---

### Post by Jakiejake on 2010-07-05
Right click on a panel and click add new panel :D

---

### Post by Kvantftw on 2010-07-05
> **Jakiejake said:**
> Right click on a panel and click add new panel :D

Theres no other panel to right click

---

### Post by cariboo on 2010-07-05
Did you check to make sure you aren't actually starting a gnome session. You can choose your session at the login screen.

---

### Post by Kvantftw on 2010-07-05
Nope, just went through every session that was there, I was on the right one.

Thanks though I learned something new already

---

### Post by Kvantftw on 2010-07-05
Just to be clear.

The screen is just the wallpaper with the black taskbar at the top that has the Wifi, bluetooth, email and date. Nothing else on the screen.

---

### Post by kerry_s on 2010-07-05
the launcher on the desktop is "netbook-launcher".

so use the alt-f2 to launch a terminal, maybe you can get some clues.

press-> **alt+f2**
type-> **gnome-terminal**

in gnome-terminal:
type-> **netbook-launcher**

---

### Post by Kvantftw on 2010-07-05
Says Segmentation Fault

---

### Post by Kvantftw on 2010-07-05
Bump

Is that bad? lol Any fixes or do I need for fresh install or something?

---

### Post by kerry_s on 2010-07-05
press-> **alt+f2**
type-> **gksudo synaptic**
put "netbook" in the quick search 
look for "netbook-launcher", right click it & mark for complete removal
click apply
(important you want to completely remove it, before you install it again, you want any broken settings gone)
now right click & mark it for installation
click apply
log out & back in

in the event that don't work (i'm going out, so just in case)

press-> **alt+f2**
type-> **nautilus**
press-> **ctrl+h**
go into ".config" & delete "netbook-launcher"
log out & back in


good luck

---

### Post by Kvantftw on 2010-07-05
ok I did that but now I get an error

The Panel Encountered a problem while loading "OAFIID:GNOME_GoHome".

Dont delete or Delete are the options

Edit: Tried both options as it pops up everytime, nothing works.

Should I just go ahead and reinstall? I'm not in any hurry though

---

### Post by kerry_s on 2010-07-06
> **Kvantftw said:**
> ok I did that but now I get an error

The Panel Encountered a problem while loading "OAFIID:GNOME_GoHome".

Dont delete or Delete are the options

Edit: Tried both options as it pops up everytime, nothing works.

Should I just go ahead and reinstall? I'm not in any hurry though


so you got your launcher back, but now your panel is acting up?

open **nautilus**
press-> **ctrl+h**
goto-> **.gconf-> apps**
delete the "**panel**" folder
**log out & back in**
you should have a brand new panel just like the first day you installed.

---

