---
title: "I've messed up my panels &amp; can't get them back to how they were :("
date: 2009-01-26
forum: New to Ubuntu
---

### Post by oddparticle on 2009-01-26
Pretty much as it says in the title. I accidentally removed some of the things on my top panel whilst trying to remove the ugly rectangular divider, and I can't get them back. I seem to have lost the icon for rhythmbox that previously appeared on the top panel when I was listening to music and showed the artist & title when the track changed, and also the internet connection icon thing has gone. Basically everything to the left of the date on the top panel. Neither of the things I lost seem to be in the 'add to panel' list. Is there any way I can reset the panel to its default arrangement or something?

---

### Post by theozzlives on 2009-01-26
I'm pretty sure you just lost your notification area, just right click on the panel and go to add to panel, then select it from the list.

---

### Post by oddparticle on 2009-01-26
Yep, that seems to be it. Thanks :D

---

### Post by ubuntu27 on 2009-01-26
Like theozzlives says, you deleted the "Notification Area"

[LIST=1]
[*]Right click on a panel
[*]Click on "Add to Panel"
[*]Choose **Notification Area**
[*]Click on Add.
[*]Close.
[/LIST]

---

### Post by metallicamike on 2009-01-26
> **ubuntu27 said:**
> Like theozzlives says, you deleted the "Notification Area"

[LIST=1]
[*]Right click on a panel
[*]Click on "Add to Panel"
[*]Choose **Notification Area**
[*]Click on Add.
[*]Close.
[/LIST]

I don't know if you saw but theozzlives beat you to it. ;):p:lolflag:

---

### Post by ubuntu27 on 2009-01-27
> **metallicamike said:**
> I don't know if you saw but theozzlives beat you to it. ;):p:lolflag:

Yes, I saw the he beat me for 30 seconds ><;

---

### Post by cdtech on 2009-01-27
**Just a bit of advice for thought:**

I reset my panel and could not figure how to get it back to the way I had it. Luckily I had backed up my configuration for the panel. The config file is located in the directory:
```
~/.gconf/apps/panel
```
Back it up if you plan on doing anything to the panel configuration.

###################################################################

**[SIZE="3"]Here is a method for restoring your panel to default:[/SIZE]**

Press ALT+F2 and in the run dialog box, type "gnome-terminal" then click on Run.

When the Terminal window opens, enter the command:
```
sudo apt-get install gconf2
gconftool-2 --recursive-unset /apps/panel
```
Then enter:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```
This will retore to its original state.

Hope this helps ya.........

---

