---
title: "replace pcmanfm"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by dzon65 on 2010-04-27
This is an openbox with a minimal/lxde install.In openbox,I've got the gnome-panels installed.And although I changed nautilus with thunar (gksu gedit /usr/share/applications/nautilus-folder-handler.desktop),replaced pcmanfm with thunar, the files still open with pcmanfm.So I need to know how I can make this work.It wasn't a prob with openbox on a gnome-core so I guess I have to edit something in lxde.
Kind regards,J.

---

### Post by dzon65 on 2010-04-27
To check,I installed gnome-panel in lxde as well.Same here,places will be opened by pcmanfm.

---

### Post by kerry_s on 2010-04-27
in gconf-editor, click "edit"-> "find", type "nautilus"
go through there & change them to the file manager you want.

are you running the lxpanel at all? 
cause under advanced it has settings for file manager. see pic

---

### Post by dzon65 on 2010-04-27
Hi kerry.Well,allready changed everything to thunar like I would if this were to be a gnome install.Unfortunately I replaced the lxpanel with a gnome one in lxde.I replaced pcmanfm by thunar as lxpanel manager.I probably didn't do it wright though.Not sure how I had to do it.But,if I get it wright,even the gnome panels under lxde will be managed by pcmanfm and not nautilus?Could you give me the wright command for the lxpanels manager?Would that be thunar%S

---

### Post by dzon65 on 2010-04-27
Reinstalled the lxpanel in lxde and changed the manager to Thunar %F.No go.

---

### Post by warfacegod on 2010-04-27
Any particular reason you prefer Gnome's panel over LXDE's?

---

### Post by dzon65 on 2010-04-27
Only one,website shortcut support.

---

### Post by dzon65 on 2010-04-27
Say W.This is strange,no matter how I change settings,places will open with pcmanfm instead of thunar.Oh yeah,did a fresh install using lxde now.I allready have about 90% installed all my stuff and it's about 2Gb.

---

### Post by warfacegod on 2010-04-27
I'll bet allot of that is left over packages.

```
sudo apt-get autoremove
```

---

### Post by kerry_s on 2010-04-27
you can do a override script. /usr/local/bin is checked before /usr/bin for the executables, i use it to override a couple of things, a simple script can make any call to pcmanfm launch thunar.

press-> **alt+f2**
type-> **gksudo leafpad /usr/local/bin/pcmanfm**
put:
```

[B]#!/bin/sh
thunar "$@" &[/B]

```

make it executable-> **chmod +x /usr/local/bin/pcmanfm**

---

### Post by dzon65 on 2010-04-27
Ok,thanks for the replies everybody.
Kind regards,J.

---

