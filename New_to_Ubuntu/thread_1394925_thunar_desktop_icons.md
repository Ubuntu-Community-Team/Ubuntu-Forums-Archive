---
title: "thunar desktop icons"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by dzon65 on 2010-01-31
i'm using thunar as filemanager in 9.10.Since nautilus takes care of desktop icons,is there a way thunar can be set to do it as well?It's not THAT important,but I used to have my downloads to,well,download to my desktop.

---

### Post by warfacegod on 2010-01-31
> **dzon65 said:**
> i'm using thunar as filemanager in 9.10.Since nautilus takes care of desktop icons,is there a way thunar can be set to do it as well?It's not THAT important,but I used to have my downloads to,well,download to my desktop.

Assuming your using Firefox. Go to: Edit> Preferences> Main tab> under downloads> check "Save Files To"> click browse> go to Desktop> click Open or Alt+O

---

### Post by dzon65 on 2010-01-31
Hi warface.That's how it was set in the first place.Doesn't work,had to change"save downloads" to downloads.Thunar sure runs faster than nautilus but it has it's price.

---

### Post by warfacegod on 2010-01-31
> **dzon65 said:**
> Hi warface.That's how it was set in the first place.Doesn't work,had to change"save downloads" to downloads.Thunar sure runs faster than nautilus but it has it's price.

Is there a File Manager that has a decent middle ground? Actually I think you can get support plugin things for Thunar but they will (of course) cost you some performance.

---

### Post by dzon65 on 2010-01-31
Actually,thunar can do more than nautilus (editing rightclicks etc...).But there is no such plugin to enable desktop icons.
Anyhooo:[http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html](http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html)
Oh,btw,this script works better than the other ones I've tried.This will allow nautilus to open specific nautilus-related menus,the other scripts nearly killed it in a way that nautilus didn't open a d... thing.

---

### Post by warfacegod on 2010-01-31
You can add scripts to Nautilus right click.

---

### Post by dzon65 on 2010-01-31
Sure,and if you want more you can always add "actions".I'm just looking for some workspeed.Haven't even checked the thunar options.Only thing I know,it's faster.Pretty sure there's a workaround to enable desktop icons with thunar.

---

### Post by ankspo71 on 2010-01-31
Hi,
I see from the link you have replaced nautilus with thunar...
[http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html](http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html)

What menu pops up when you right click on your desktop? Is it the nautilus one or the xfce one? If it is the xfce one, then the option you need to change is in: Right click on your background > Desktop Settings > Icons Tab > then change the icons type values from 'none' to 'File/Launcher icons'. Those same options can be found in the xfce start menu (if you have the 'xfce4-panel' or 'xfce4' package installed). 

Personally, I prefer to keep the nautilus desktop as my default running desktop / file manager, and keep thunar installed as a secondary file manager.
Hope this helps.

---

### Post by dzon65 on 2010-01-31
Just a sec.Installed openbox as windowmanager,different rightclickmenu.Right back.

---

### Post by dzon65 on 2010-01-31
Hmm,that's odd.Nothing happens.Gonna log out/in.Right back.

---

### Post by dzon65 on 2010-01-31
Ok,small problem here.Nothing happens when rightclicking my desktop.Not with compiz,gtk,emerald..
Whn I use openbox,there's a totally different (openbox)menu.No compiz nor xfce one.

---

### Post by Psumi on 2010-01-31
Thunar doesn't do desktop icons because XFCE uses xfdesktop to render desktop icons.

Use pcmanfm if you want desktop icons but still want lightweight. Oh, and, you cannot position desktop icons in pcmanfm, they stay in a line like if it were an actual folder.

You will also need to start up pcmanfm as a daemon in the startup applications.

---

### Post by dzon65 on 2010-01-31
Hmm,pcmanfm ey?Okay,gonna have a look at it.Still strange nothing happens when rightclicking the desktop though.
Oh well,i'll figure it out.Thanks for all the replies people.
Kind regards,J.

---

### Post by Psumi on 2010-01-31
> **dzon65 said:**
> Hmm,pcmanfm ey?Okay,gonna have a look at it.Still strange nothing happens when rightclicking the desktop though.
Oh well,i'll figure it out.Thanks for all the replies people.
Kind regards,J.

By default, pcmanfm doesn't handle the desktop. Remember to change its settings.

---

### Post by warfacegod on 2010-01-31
> **Psumi said:**
> Rock the boat, rock the boat baby, rock the boat!

Looks like he's already got some seesaw action going. Side to side would be total disaster. Do it! Do it!

---

### Post by dzon65 on 2010-01-31
Ok,did it.

---

### Post by Psumi on 2010-01-31
Also, be careful. I believe pcmanfm deletes files, rather than moving them to the trash.

---

### Post by overdrank on 2010-01-31
Ok back on topic please. :)

---

### Post by warfacegod on 2010-02-02
Try installing Ubuntu Tweak and setting Thunar as the File Manager.

---

### Post by Leppie on 2010-02-02
> **warfacegod said:**
> Try installing Ubuntu Tweak and setting Thunar as the File Manager.
not sure if this ubuntu tweak checks this as well, but normally nautilus also controls the desktop wallpaper.

---

### Post by warfacegod on 2010-02-02
> **Leppie said:**
> not sure if this ubuntu tweak checks this as well, but normally nautilus also controls the desktop wallpaper.

I'm grasping at straws here.

---

