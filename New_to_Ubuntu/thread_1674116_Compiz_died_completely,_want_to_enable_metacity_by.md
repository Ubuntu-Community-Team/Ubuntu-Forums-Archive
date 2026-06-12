---
title: "Compiz died completely, want to enable metacity by default"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by willyclaes on 2011-01-23
My question is this: how do I enable metacity so it starts by default?   

Whenever I boot I don't have window title bars. I uninstalled compiz because I couldn't enable ANY desktop effects. This started after I installed cairo dock. I uninstalled cairo (through ubuntu software installer) but I still couldn't enable compiz desktop effects. I searched the forums with no help. Whenever I boot into Ubuntu I start metacity in the terminal (for some reason alt+f2 doesn't respond, but after I enabled metacity with the terminal alt+f2 works again, so I guess the problems are related). I tried it with gconf-editor without success. 

Does it have something to do with conflicting packages? I noticed in the package manager there are still some compiz packages left.   It's getting really frustrating. SO PLEASE HELP.

---

### Post by rvchari on 2011-01-23
try to remove all the cairo dock related files hidden in ur home directory (.config, .local > share etc...) if u were using compiz then start compiz fusion icon , right click it and reload window manager...
before you do this u can select window manager from there....
choose metacity and reload window manager.

if compiz fusion icon isnt there, install it thru software center

---

### Post by willyclaes on 2011-01-25
Thanks for your reply!!!

I did all that, and when i reboot I get two errors that KDE window decorator stopped working. So the window manager is still not working by default.  I have to start compiz fusion and then reload window manager. Any ideas?

---

### Post by kellemes on 2011-01-25
Install compizconfig-settings-manager
and run it from terminal, or F2-dialog..
ccsm
Use the icon in your systemtray to configure it al..

---

### Post by willyclaes on 2011-01-28
When I start up I get two of these these crash messages:

Application: KDE Window Decorator (kde4-window-decorator), signal: Segmentation fault

And Kellemes: I just deinstalled compiz settings manager becaue it didn't respnd at any changes I would make. I couldn't enable desktop effects. I could enable advanced desktop effects in the simple settings manager but there weren't any effects, no wobbly windows etc.. Transparacy is still working. Metacity is fancy enough for me so that is why I want metacity to be enbled by default. Is reinstalling compiz settings manager the only way to do so? Or does metacity use packages from compiz?

Also the f2 dialog does not work until I launched metacity through the terminal.

---

### Post by coffeecat on 2011-01-28
Metacity and KDE Window Decorator?? Are you using gnome or KDE?

---

### Post by migrate from windows on 2011-01-28
When i had this issue I tyoed 
metacity --replace 
in the terminal 
and restarted ...metacity was enabled!!!

---

### Post by willyclaes on 2011-01-29
> **coffeecat said:**
> Metacity and KDE Window Decorator?? Are you using gnome or KDE?

I'm using gnome.

---

### Post by lidex on 2011-01-29
Use gconf-editor to set values in desktop/gnome/applications/window_manager and also desktop/session/required_components

---

### Post by willyclaes on 2011-01-29
Thanks linex!
That did the trick!

I followed instructions on this forum to edit gconf but it only mentioned desktop/gnome/applications/window_manager and not desktop/gnome/session/required_component. 
After I edited the last one and rebooted metacity finally loaded on start up!

---

### Post by tekkidd on 2011-01-30
First, try removing the compiz folder from your home directory 
```
rm -r .compiz
```after doing this you should be able to enable desktop effects. 

Also, to get ALT+F2 to work first make sure that CCSM is installed then in the CCSM window, check the "Gnome Compatability" and that should enable ALT+F2 with comiz

Also if you want to just enable metacity on start by default then goto System>Prefrences>Startup Applications
their add a new entry and for the command enter this 
metacity --replace

---

