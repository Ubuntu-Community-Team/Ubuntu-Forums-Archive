---
title: "No buttons.. only my wallpaper"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Green_Grenade on 2011-03-08
So, like the title says... I only have my Wallpaper. Theres no menu bar.. NOTHING! Just the wallpaper.
no mouse.. nothing. BUT! CTRL ALT delete works.. my mouse only shows up in that window.. and its a X ..

Any ideas?!

Thx!

---

### Post by cap10Ibraim on 2011-03-08
if this happen occasionally try Ctrl+alt+f1 then go back to ctrl+alt+f7 
see if it's refreshed

---

### Post by mmsmc on 2011-03-08
what did you do before this occured

---

### Post by Green_Grenade on 2011-03-09
OK! I did the ctrl alt f1 and then f7 thing.. i have a mouse now. and its the X still..

I lent my comp to my sister.. its a netbook.. and i think she didnt like the Netbook Ubuntu setup so she tried to change it to.. the regular.. or whatever.. and then yea.. got it back like this..

---

### Post by cap10Ibraim on 2011-03-09
so it's unity ?

---

### Post by Green_Grenade on 2011-03-09
I have no idea. Sorry.

---

### Post by Green_Grenade on 2011-03-09
It says.. 

Ubuntu 10.04.1 LTS 

When i hit Ctrl Alt f1, if that helps.

---

### Post by MibunoOokami on 2011-03-09
> **Green_Grenade said:**
> So, like the title says... I only have my Wallpaper. Theres no menu bar.. NOTHING! Just the wallpaper.
no mouse.. nothing. BUT! CTRL ALT delete works.. my mouse only shows up in that window.. and its a X ..

Any ideas?!

Thx!

Well now that's interesting because I just finished installing 10.10 last evening, then when I suspended my PC it actually restarted and all I got was the wallpaper and 1 desktop icon.
I thought perhaps it was my fault because I **completely** uninstalled empathy, evolution and gwibber or whatever it's called. I doubt your sister would have done the same thing so I will watch this thread with much anticipation. I was thinking to re-install all the packages.

Sorry I am unable to offer you any solutions to this problem.

---

### Post by maqtanim on 2011-03-09
Press **Alt+F2**. A **Run Application** windows will be opened. Type the follwoing command in the text field.```
**gnome-terminal**
``` The terminal should be opened. Now type the following command in the terminal. 
```
**killall gnome-panel** 
```
And press Enter.

Let us know what happens.

---

### Post by MibunoOokami on 2011-03-09
> **maqtanim said:**
> Press **Alt+F2**. A **Run Application** windows will be opened. 

I tried pressing alt+f2 but nothing happened. I tried ctrl+alt+f2 and got taken to a black screen like command prompt where I had to login before doing anything.

> **maqtanim said:**
> Type the following command in the text field.```
**gnome-terminal**
``` The terminal should be opened. Now type the following command in the terminal. 
  

Unfortunately when I entered this code, I got a failure message.

```
failed to parse argument cannot open display
```

Doesn't sound too promising. I hope Green_Grenade has better luck. 

Sorry if I'm taking over this thread.

---

### Post by fabricator4 on 2011-03-09
> **MibunoOokami said:**
> I tried pressing alt+f2 but nothing happened. I tried ctrl+alt+f2 and got taken to a black screen like command prompt where I had to login before doing anything.

Unfortunately when I entered this code, I got a failure message.

```
failed to parse argument cannot open display
```


The black screen where you log in is a console.  It's the same as a terminal, just not windowed on the desktop.

Try the killall command and see if it works.

Chris.

---

### Post by Green_Grenade on 2011-03-10
Hey Fab.. I tried the ctrl alt f2, logged in as me password and all that.. typed in the killall gnome-panel and got
gnome-panel: no process found

---

### Post by 741Baus on 2011-03-10
Hi Green_Grenade try this ctl+alt+t will open a terminal Then run this code 
```
sudo chmod +x /usr/bin/gnome-panel
sudo reboot 
```
 
When you get to your desktop you wont have any panels ctl+alt+t 
```
killall gnome-panel
```
will reinstate your panels hope this helps

---

### Post by Green_Grenade on 2011-03-10
OK... ctrl alt t does nothing..

---

### Post by fabricator4 on 2011-03-11
> **Green_Grenade said:**
> OK... ctrl alt t does nothing..

Just go to the console: <ctrl><alt><F2> as you did before.  Log in and then try the commands that 741Baus gave you.

Chris.

---

### Post by Green_Grenade on 2011-03-11
K..

ctrl alt f1
asks me to log in -> I log in
type in sudo chmod +x /usr/bin/gnome-panel
press enter
asks for my password -> type password
press enter
then it just goes back to the flashing underscore
type in sudo reboot
comp reboots
grub loads
hit Ubuntu 10.04.1
loads up and only shows me my wallpaper
No mouse
press ctrl alt t
Nothing happens.
press ctrl alt f1 
log in
password
type in killall gnome-panel
press enter
gnome-panel: no process found

.. in a nutshell.. LOL!

---

