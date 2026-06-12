---
title: "How can I remove emove ALL panels? (using AWN instead)"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-11-09
As the title reads, I would like to remove all panels, I am using AWN instead.

Edit: I'm using Ubuntu 9.10.

---

### Post by ajgreeny on 2009-11-09
Try ```
sudo apt-get remove gnome-panel
```It will take several other things with it, including the gnome-applets and ubuntu-desktop, but if you don't like what happens you can always get them back again.

---

### Post by Paqman on 2009-11-09
There's a setting in your gconf that you'll have to modify to allow you to get rid of the last panel.

1. press Alt + F2
2. type gconf-editor
3. click Run
4. in the Configuration Editor look for panel under desktop > gnome > session > required_components
5. right-click panel and select Edit Key..
6. delete gnome-panel
7. click OK

Log out then log in again and you should be good to go.

---

### Post by ubuntuforums on 2009-11-09
Thank you both for responding and trying to help. Paqman, that worked perfectly. :)

---

### Post by Belizeian on 2010-01-05
Didn't work for me with 9.10 panlel just want go away

---

### Post by Devport on 2010-01-05
This was discussed in another thread already. As far as I remember my favorite solution was something like

sudo chmod -x /usr/bin/gnome-panel

Well it reverts on updates, but its easily revertible as well.

---

### Post by sploopidy on 2010-07-10
There is a much easier way to do this. I found this in a different thread, credit to nothingspecial:

```
sudo mv /usr/bin/gnome-panel ~/.panel_backup
```

You might want to have a look at gnome-do before you do this because you will  loose Alt-F1 and Alt-F2

If you decide you don`t like it:

```
sudo mv ~/.panel_backup /usr/bin/gnome-panel
```

---

