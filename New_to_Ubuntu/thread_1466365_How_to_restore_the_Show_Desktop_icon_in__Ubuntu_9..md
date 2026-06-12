---
title: "How to restore the Show Desktop icon in  Ubuntu 9.10 netbook remix"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by mohico on 2010-04-30
Hello

I'm giving Ubuntu 9.10 netbook remix a go after seeing it in action on the Nokia N900.

2 quick questions:
- I've deleted the Show Desktop icon (the one with the Ubuntu symbol on the up-left corner) by mistake and can't get it back - any advice?
- It seems that I can't get rid of the menu on the left - is it the one things work? I'd like to see a clear desktop - should be do-able, no?

Looking forward to your tips.

Best
M

---

### Post by Jon Monreal on 2010-04-30
I don't use UNR, so I can't offer much help.

For the first problem, try right-clicking on the panel and selecting "Add to Panel...". "Show Desktop" should hopefully be in this list.

---

### Post by mohico on 2010-04-30
> **Jon Monreal said:**
> I don't use UNR, so I can't offer much help.

For the first problem, try right-clicking on the panel and selecting "Add to Panel...". "Show Desktop" should hopefully be in this list.

Thanks for the reply. Surprisingly, there is no "add to Panel" option!! I get (Preferences, About, Remove from Panel, Move, and Lock to Panel)!

Best
M

---

### Post by Paqman on 2010-04-30
> **mohico said:**
> Surprisingly, there is no "add to Panel" option!!

There won't be, because there's no free space in the panel to add one to. In UNR the panel is taken up by one big transparent applet. In cases like yours that's actually a bit of a pain.

I'm not 100% this will sort you out, but you should be able to restore the default panels by opening an terminal and pasting in this:
```

gconftool-2 &#8211; -shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by mohico on 2010-04-30
> **Paqman said:**
> 
I'm not 100% this will sort you out, but you should be able to restore the default panels by opening an terminal and pasting in this:


Many thanks! It works! :)

Any ideas re. the second question? Do I have to stick with a menu for ever - can I get a Desktop in UNR somehow?

M

---

### Post by Jon Monreal on 2010-04-30
Try Preferences>Switch Desktop Mode.

You might need to install ubuntu-desktop.

---

### Post by Paqman on 2010-04-30
> **mohico said:**
> can I get a Desktop in UNR somehow?


Well, that menu is (most of) what sets UNR apart from the regular Gnome Ubuntu desktop. You should be able to turn your Netbook Remix into standard Ubuntu though, just uninstall all the Netbook packages (netbook-launcher, maximus, etc) and install ubuntu-desktop.

---

### Post by dalee on 2010-04-30
Hi,

I didn't have to uninstall UNR desktop to get Gnome working. I simply installed the Gnome packages I wanted. I then could to log into either desktop. But, if you don't like UNR, there is little reason to keep it either.

dalee

---

### Post by mohico on 2010-04-30
> **Jon Monreal said:**
> Try Preferences>Switch Desktop Mode.

You might need to install ubuntu-desktop.

The desktop-switcher is not available. As I've understood from other threads, the package was dropped as it was too buggy. Now the only way to do it seems to be by "killing the ume-launcher process" (or uninstalling it as you pointed out) - something I will leave after going through the beginners' tutorials offered on this forum.

Many thanks. 
M

---

### Post by themusicalduck on 2010-04-30
I found out that you can go into normal desktop mode if you press ctrl+alt+f1, type ```
sudo service gdm stop
``` (this will close any open programs at the time) and then type ```
startx
```

Although I think I last used it on Karmic not Lucid, and I don't know if using it in this mode would cause any problems with using it in netbook remix mode.

---

