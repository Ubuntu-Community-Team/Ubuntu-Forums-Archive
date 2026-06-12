---
title: "Evolution tray icon"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by Plops on 2010-09-10
Hello,

Would someone be so kind as to enlighten me as to how to restore the Evolution tray icon where Pidgin and Empathy etc also used to reside? It disappeared when I forced Evolution to terminate the other day.

Many thanks,

Plops

---

### Post by mr_luksom on 2010-09-10
Choose Startup Applications from Preferences, and then I believe it is Notifications (could be wrong, I'm not at my ubuntu machine)

---

### Post by Plops on 2010-09-10
Thank you. The 'Evolution Alarm Notifier' is there; however, it's the mail notification tray icon which I would like to restore. The Evolution Alarm Notifier is still working well. I would be happy with adding it to the list of startup apps if I knew the command.

Thanks again. Plops.

---

### Post by cake nom nom on 2010-09-10
are you referring to the little green chat bubble? and did all of the icons disappear? or just the one?

---

### Post by philinux on 2010-09-10
> **Plops said:**
> Hello,

Would someone be so kind as to enlighten me as to how to restore the Evolution tray icon where Pidgin and Empathy etc also used to reside? It disappeared when I forced Evolution to terminate the other day.

Many thanks,

Plops

It's likely just the notification area applet needs adding back to the panel. Right click "add to panel". I that doesn't do it then see below.

If you've not heavily customised the panels the quickest way to get back to the **default** is like this.
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by cake nom nom on 2010-09-10
right click your panel bar > add to panel > notification area


does this fix the problem?

---

### Post by Plops on 2010-09-10
Thanks Philinux - that worked. The only thing is now when I start Spotify the icon is no longer in the notification area. Can you tell me how to get that back? Many thanks, Plops

---

### Post by philinux on 2010-09-10
> **Plops said:**
> Thanks Philinux - that worked. The only thing is now when I start Spotify the icon is no longer in the notification area. Can you tell me how to get that back? Many thanks, Plops

Not sure which bit worked, you dont say.

I dont use spotify, maybe there's a setting in it to display a tray icon.

---

### Post by Plops on 2010-09-10
The gconftool command was the bit that worked. Thanks again. Plops

---

