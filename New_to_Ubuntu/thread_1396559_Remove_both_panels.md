---
title: "Remove both panels"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by bobin on 2010-02-02
can't remove second panel. Want to replace it by cairo dock

---

### Post by NightwishFan on 2010-02-02
The Gnome desktop always requires at least one panel.

---

### Post by lotharmat on 2010-02-02
Hide it?

---

### Post by nothingspecial on 2010-02-02
Not recommended, but  

```
sudo mv /usr/bin/gnome-panel ~/.panel
```

That will move the binary to a hidden file in your home folder called .panel.

If you ever want it back ```
sudo mv ~/.panel /usr/bin/gnome-panel
```

You will lose the alt-F2 run functionality.

Do it at your own risk.

Alternatively use openbox or something else that doesn`t "require" a panel.

---

### Post by bobin on 2010-02-02
whats openbox

---

### Post by nothingspecial on 2010-02-02
A different desktop environment.

```
sudo apt-get install openbox
```

then logout and when you log back in, change the session to openbox at the bottom of the login screen.

It takes a bit of configuring to get it how you want it but worth it in my opinion. If you don`t like it or can`t be bothered simply logout and change the session back to gnome and maybe have another go when you have more time.

---

### Post by ayenack on 2010-02-02
Been awhile but this should do it. Make a note of the command you remove in gconf-editor. And you do this at your own risk.

1, Open a terminal and type.

```
gconf-editor
```

2, Click on **apps** in the drop down menu, then **Gnome**, **sessions**, and finally **required sessions**.

3, Find gnome-panel, right click it and chose edit and make it empty.

4, Save.

5, Press ctrl+alt+delete

This should remove panels. if not reboot. If you wish to restart panels type in gnome-panel.

Can I just say you'll need some other way of controlling your apps something like AWN.

EDIT:- BTW. You can just completely hide the panels like so. Open gconf-editor as above. Then...

 gconf-editor > apps > panel > toplevels > top_panel_screen0 > auto_hide_size > 0

This for me is a more elegant solution. You'll still have your panels but they won't intrude on your desktop until you want them to.

---

