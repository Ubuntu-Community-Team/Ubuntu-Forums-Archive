---
title: "I broke my FireFox fonts!"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by KlytusLord on 2011-01-18
So, I have been goofing around installing and removing different window managers and other software. Along the way, I somehow messed up my firefox fonts.

I am back to the gnome/metacity desktop, and all the fonts in firefox look like the old DOS terminal fonts. The rest of the system seems fine. This is not just the font used to display web content, and therefore not affected by the font settings within firefox. All of the fonts in firefox are not cleartyped, including the menu, and bookmark fonts.

I have already uninstalled and reinstalled firefox, but alas the problem persists.

Any ideas?

I am probably just going to re-install Ubuntu from scratch, now that I am done experimenting with all of the window managers, but it would be good to fix firefox in the meantime.

---

### Post by KlytusLord on 2011-01-18
As a follow up, whatever I did affected all of the Mozilla applications. Thunderbird has the exact same issue as firefox, with the same weird font being used in the menu and sidebar and message list.

All other Gnome applications seem ok.

I am about to re-install Ubuntu, but it would be nice to know what happened, so I can avoid it in the future :)

---

### Post by balaknair on 2011-01-19
1) try installing the firefox GNOME integration package

sudo apt-get install firefox-gnome-support


2) You can try resetting Firefox configuration with a terminal command

sudo dpkg --reconfigure firefox

Not quite sure what might have happened but I'm guessing the package that integrates FF with GNOME got messed up(firefox-gnome-support). Likewise for thunderbird-gnome-support

---

### Post by KlytusLord on 2011-01-19
Thanks for the advice.

It claims both packages are already installed.

---

