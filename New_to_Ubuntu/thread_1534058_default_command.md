---
title: "default command"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by mrfoochie on 2010-07-18
howdy folks, just off the the top of your heads, anyone remember the code that resets everything to the default settings? muchas

---

### Post by owners4life5 on 2010-07-18
try this

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

did that work?
this applies to the gnome desktop

---

### Post by mrfoochie on 2010-07-19
yeah, it reset every thing... thanks... i was hoping to correct a problem i've been dealing with ever since i upgraded to 10.04... my windows have no control buttons on them... they also cannot be moved around via click and drag... i often have to shut my computer down with my power button because there is no other way to shut a given window... also if there is an open window under other windows, when clicked it does not rise to the top...

---

### Post by owners4life5 on 2010-07-19
it.s apparent you know how to use a terminal... do you have compiz installed?

---

### Post by mrfoochie on 2010-07-19
dunno, can you hip as to how to check?

---

### Post by owners4life5 on 2010-07-19
well, compiz is just a window manager, like metacity, which is the default for ubuntu.

you would know if you have compiz installed.

goto the terminal
```
sudo apt-get install compiz
```

once it is done, let me know... and we might be able to fix the button problem

---

### Post by mrfoochie on 2010-07-19
i checked in the synaptic package manager and it seems to be installed...

---

### Post by owners4life5 on 2010-07-19
okay... go to the main menu, and system tools

is there an icon that says 'compiz fusion icon'?

---

### Post by mrfoochie on 2010-07-19
under system preferences there is a compiz-config manager... poked around it a bit... it was a tad baffling... no fusion though... sorry this is taking so long... i can't minimize or anything and the browser covers up my top panel so i have to shut down fire fox every time you have me check on something...

---

### Post by owners4life5 on 2010-07-19
it.s okay, i.m in no hurry (:

just go to your terminal, type in
```
sudo apt-get install compiz
```

is THAT specific package already installed? if not, install it, then let me know.

---

### Post by darolu on 2010-07-19
You may want to install these too:
```
sudo apt-get install compiz-fusion-plugins-extra compizconfig-settings-manager
```

---

### Post by mrfoochie on 2010-07-19
yeah, the latest version of compiz is installed according to the terminal...

---

### Post by owners4life5 on 2010-07-19
> **darolu said:**
> You may want to install these too:
```
sudo apt-get install compiz-fusion-plugins-extra compizconfig-settings-manager
```

yes, try that suggestion also, and then see if 'compiz fusion icon' is listed under the top-left menu, then under system tools. if there is, click on it. there should be that same icon in the top right of your screen, on your top panel. if this works correctly, we.ll take it from there

---

### Post by mrfoochie on 2010-07-19
everything is installed and the latest version but i cannot find this fusion icon... i may be daft... i looked under applications> system tools... here i found only the configuration editor and ubuntu tweak, which i've had no success with... and i also looked under system> preferences, and system> administration... no dice...

---

### Post by Mike_IronFist on 2010-07-19
> **mrfoochie said:**
> everything is installed and the latest version but i cannot find this fusion icon... i may be daft... i looked under applications> system tools... here i found only the configuration editor and ubuntu tweak, which i've had no success with... and i also looked under system> preferences, and system> administration... no dice...
You need the program fusion-icon, which is its own package. You can find fusion-icon in Synaptic, Ubuntu Software Center, or you can install it via terminal by typing:
```
sudo apt-get install fusion-icon
```
Afterwards, it should be available under "Applications -> System Tools".

---

### Post by owners4life5 on 2010-07-19
go with mike iron fist

---

### Post by mrfoochie on 2010-07-19
lovely, lovely, i got the icon... now what... i pressed it and it seemed to do, well, nothing...

---

### Post by owners4life5 on 2010-07-19
did it show in the top right tray?

---

### Post by mrfoochie on 2010-07-19
nice! i right clicked on the icon and chose choose editor... i picked compiz and viola! right as rain... thanks fellas for your time and effort... if you are ever in new orleans i'd love to buy you a cup of coffee or some thing stronger if you prefer...

---

### Post by mrfoochie on 2010-07-19
actually i chose select window manager> compiz... maybe it turned off metacity which i've only been able to do temporarily at best with tweak...

---

### Post by owners4life5 on 2010-07-19
haha good job! that was the next step but you got it yourself...... so good job!! haha and i.m 14, i prefer unsweet tea (:

---

### Post by mrfoochie on 2010-07-19
14? holey moley kiddo... thanks for all the help... stick with the tea... doesn't stain your teeth like coffee and doesn't cause headaches like alcohol..

---

### Post by owners4life5 on 2010-07-19
haha you bet.... glad to help

---

