---
title: "Deleted both panels"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by Knepp on 2009-09-25
I accidently deleted Both the top and bottom panes in Ubuntu and I can't find out how to fix this. I can only run firefox and terminal which i have on my desktop. Can anyone help me out quick? thx!

---

### Post by nothingspecial on 2009-09-25
Try running ```
gnome-panel
```

---

### Post by Knepp on 2009-09-25
This is what a get "Cannot register the panel shell: there is already one running."
from that command

---

### Post by ~sHyLoCk~ on 2009-09-25
Open gconf-editor and search for panels, I remember that's how I used to delete/restore Gnome panels.

---

### Post by nothingspecial on 2009-09-25
```
killall gnome-panel && gnome-panel
```

---

### Post by credobyte on 2009-09-25
I would like to know, how you did it .. I haven't had any luck with removing both panels, without removing the executable 8-[

---

### Post by nothingspecial on 2009-09-25
> **credobyte said:**
> I would like to know, how you did it .. I haven't had any luck with removing both panels, without removing the executable 8-[

That`s how I do it.

---

### Post by mcduck on 2009-09-25
> **credobyte said:**
> I would like to know, how you did it .. I haven't had any luck with removing both panels, without removing the executable 8-[

Gnome-panel can be disabled in gconf-editor, under desktop/gnome/session/required_components.

The reason why you can't simply kill it is exactly the same, it's defined as a required component of Gnome so it will psaen back if it's killed or it crashes. But just remove it from that gconf key and it won't start any more, no need to mess with your system files.. :)

---

### Post by credobyte on 2009-09-25
> **mcduck said:**
> Gnome-panel can be disabled in gconf-editor, under desktop/gnome/required_components.

The reason why you can't simply kill it is exactly the same, it's defined as a required component of Gnome so it will psaen back if it's killed or it crashes. But just remove it from that gconf key and it won't start any more, no need to mess with your system files.. :)

Didn't worked for me ( spent like 2 days just on trying to disable both panels ).

---

### Post by mcduck on 2009-09-25
> **credobyte said:**
> Didn't worked for me ( spent like 2 days just on trying to disable both panels ).

What do you mean "didn't work"? Did you remove "panel" from the required_components -key, log out and back again and the panel still started? In that case you must have added a command to start the Gnome-panel somewhere else, since that gconf key is what normally autostarts it.

I just disabled the panel and enabled it again that way, it definitely works.

---

### Post by credobyte on 2009-09-25
> **mcduck said:**
> What do you mean "didn't work"? Did you remove "panel" from the required_components -key, log out and back again and the panel still started? In that case you must have added a command to start the Gnome-panel somewhere else, since that gconf key is what normally autostarts it.

I just disabled the panel and enabled it again that way, it definitely works.

```
sudo apt-get autoresponder
autoresponder -all "yes"
```If seriously, I tried almost everything.

---

### Post by mcduck on 2009-09-25
> **credobyte said:**
> ```
sudo apt-get autoresponder
autoresponder -all "yes"
```If seriously, I tried almost everything.

Then all you can do is to try t figure out where you have added a command to start gnome-panel.

Just to make sure, here' are the exact steps for removing Gnome-panel from your session:

1. Start Gconf-editor (alt-F2 and run "gconf-editor")

2. Browse to desktop/gnome/session

3. Edit the "required_components" -key and remove "panel" from it.

4. Log out from Gnome.

Next time you log back the panel won't start. Unless you have yourself set it to start in some other place.

---

