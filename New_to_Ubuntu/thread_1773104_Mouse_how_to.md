---
title: "Mouse how to"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by oldcity11 on 2011-06-01
Just installed Lubuntu 10.04 on my old laptop. The install went just fine. The problem at the moment is there is no way that I could find to set the mouse to a pointer.  It currently is looking somewhat like a product bar code.
 
Somewhere I found a reference to these items, think it said something about peppermint. sudo apt install comixcursors
sudo update-alternatives --config x-cursor-theme
 
How would these be installed on my Lubuntu.

---

### Post by seawolf167 on 2011-06-01
To change back to a default pointer, you can adjust it inside the current theme. See [here ]("https://help.ubuntu.com/community/UbuntuEyeCandy#Mouse%20Cursor%20Themes")for a how-to.

---

### Post by oldcity11 on 2011-06-01
Re above suggestion.  It is not applicable to LUBUNTU 10.04.
While Lubuntu has a mouse and keyboard tab there is no tab
to change pointer.
I'll return to my initial request. How to:
**
sudo apt install comixcursors
sudo update-alternatives --config x-cursor-theme
**
How would these be installed on my Lubuntu.

again thanks

---

### Post by oldcity11 on 2011-06-06
What worked for me.

1. Be sure Universe is enabled in sources.list.

2. sudo apt-get update

3. sudo apt-get install comixcursors

4. sudo update-alternatives --config x-cursor-theme

A listing of cursor descriptions will be presented, enter
your numeric choice.

Re boot your computer for choice to take effect.

---

