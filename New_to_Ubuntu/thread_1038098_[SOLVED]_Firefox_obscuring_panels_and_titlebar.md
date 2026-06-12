---
title: "[SOLVED] Firefox obscuring panels and titlebar"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Timzor on 2009-01-12
After installing Ubuntu and using Firefox without any problems for a few days, Firefox began taking up the entire screen for some reason.  The Firefox window is now obscuring both top and bottom panels of my desktop, and the titlebar is not visible.

Here is a small screenshot of what I am looking at.  [http://img.photobucket.com/albums/v221/IronMagus/Screenshot-1.png](http://img.photobucket.com/albums/v221/IronMagus/Screenshot-1.png)

I do not recall making any changes that would have caused this.  I have restarted firefox and rebooted multiple times, and tried reinstalling Firefox from the synaptic package manager without any results.  Can anyone help?

---

### Post by rocknrolf77 on 2009-01-12
Are you running compiz? Did you run it before it happened? Your window decorator seems to have gone. 

If you have a nvidia card you can try this :

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Then restart the Xserver with ctrl-alt-backspace
And log in again and see if it works :)

---

### Post by wolfen69 on 2009-01-12
from [here]("https://help.ubuntu.com/community/Metacity"): 

"To change the order of the buttons on window title bars, launch Applications -> System Tools -> Configuration Editor. Navigate to /apps/metacity/general in the tree and find the "button_layout" key. The default is "menu:minimize,maximize,close". Commas separate items, and the colon marks the division between the left and right corners of the title bar. "

---

### Post by Timzor on 2009-01-12
> **rocknrolf77 said:**
> Are you running compiz? Did you run it before it happened? Your window decorator seems to have gone. 

If you have a nvidia card you can try this :

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Then restart the Xserver with ctrl-alt-backspace
And log in again and see if it works :)

I'm sorry, I don't know what compiz is.  I'm not sure if I have a nvidia card or not.  I am an absolute beginner.  Should I try pasting that code into the terminal?

---

### Post by Timzor on 2009-01-12
> **wolfen69 said:**
> from [here]("https://help.ubuntu.com/community/Metacity"): 

"To change the order of the buttons on window title bars, launch Applications -> System Tools -> Configuration Editor. Navigate to /apps/metacity/general in the tree and find the "button_layout" key. The default is "menu:minimize,maximize,close". Commas separate items, and the colon marks the division between the left and right corners of the title bar. "

I'm not sure why you posted that.  Do I need to change the order of my buttons for some reason?

---

### Post by drs305 on 2009-01-12
If you are using compiz, enable the 'Window Decoration' plugin. System > Preferences > CompizConfiguration Settings Manager. Window Decoration (or in terminal: *ccsm*).

If you don't have this option on your menu, install the manager:
```

sudo apt-get install ccsm

```

A firefox 'bug' of similar nature can be solved by hitting F11 twice to maximize and then reset the size to less than full screen. Adjust the borders and it shouldn't happen again.

---

### Post by Timzor on 2009-01-12
> **drs305 said:**
> If you are using compiz, enable the 'Window Decoration' plugin. System > Preferences > CompizConfiguration Settings Manager. Window Decoration (or in terminal: *ccsm*).

If you don't have this option on your menu, install the manager:
```

sudo apt-get install ccsm

```

A firefox 'bug' of similar nature can be solved by hitting F11 twice to maximize and then reset the size to less than full screen. Adjust the borders and it shouldn't happen again.

Okay, I tried your second suggestion first since it seemed simpler, and it worked!  Thank you for your help.

---

