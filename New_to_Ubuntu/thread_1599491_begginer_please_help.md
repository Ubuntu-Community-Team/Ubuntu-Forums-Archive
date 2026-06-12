---
title: "begginer please help"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by mantica on 2010-10-17
hey guys im new at ubuntu. i like to customize my computer by using themes and such. can somebody explain emerald,gtk,metacity,etc.

id like to get my nautilus explorer looking like this: [http://browse.deviantart.com/customization/skins/linuxutil/?order=15&offset=24#/d2zjkl9](http://browse.deviantart.com/customization/skins/linuxutil/?order=15&offset=24#/d2zjkl9)

can somebody also tell me what murrine, auora, and other engines are?

thanks

---

### Post by buknoii on 2010-10-17
try bisigi project :)

---

### Post by Iowan on 2010-10-17
Moved to Absolute Beginner Talk

---

### Post by Sealbhach on 2010-10-17
> **mantica said:**
> hey guys im new at ubuntu. i like to customize my computer by using themes and such. can somebody explain emerald,gtk,metacity,etc.

id like to get my nautilus explorer looking like this: [http://browse.deviantart.com/customization/skins/linuxutil/?order=15&offset=24#/d2zjkl9](http://browse.deviantart.com/customization/skins/linuxutil/?order=15&offset=24#/d2zjkl9)

can somebody also tell me what murrine, auora, and other engines are?

thanks

Download the zip file with the theme from the link on that page. Create a folder called .themes in your /home folder. Copy it in there and extract it. If you need to, get Faenza icons and copy them to a folder called .icons in your /home folder. Create it if you don't have it.

If you want to learn more about the technical aspects of the different window decorators, the best thing is to use the Google. :wink:

---

### Post by 3Miro on 2010-10-17
GTK and QT are "toolkits" that provide a set of tools for people to make applications under Linux. Ubuntu comes with Gnome desktop environment, which uses gtk by default. XFCE (Xubuntu) and LXDE (Lubutnu) also use use gtk. KDE and Kubuntu use the QT toolkit. Applications are based either on GTK or QT (or in rare occasions neither), but all environments can run non-native apps just fine (well, maybe with a bit more RAM).

Window manager is what is responsible for showing/moving/resizing/managing windows on your desktop. Metacity is the old default manager for Gnome (Ubuntu's defult desktop environment) and it is somewhat outdated, but very conservative on resources. Compiz is a newer fancier manager for 3D effects and such. Compiz is the default manager in Ubuntu; should you happen to have a video card + driver that can handle it, compiz requires somewhat more power from your computer. XFCE uses xfwm4 and LXDE uses Openbox as default windows manager, both have more features than Metacity, but fewer effects than Compiz. KDE uses kwin, which is very versatile and can be set to be almost as resource conservative as Metacity or almost as fancy as Compiz or anywhere in-between.

Note all windows managers are mix-and-match, meaning you can pretty much run any environment with any windows manager, however, this sometimes leads to loss of features and/or loss of stability.

There is a sub-component of the window manager that is responsible entirely for the decorations of the window. Metacity come with its own in-build decorator (and so do xfwm4 and Openbox). Compiz can chose between "gtk-window-decorator" which does more or less the same as job as Metacity (note that in the case of Compiz + KDE or Kubuntu the decorator is kde-window-decorator). Compiz can also use Emerald, which gives very fancy looks and themes, however, it requires quite a bit of resources more than gtk-window-decorator.

To easily switch between window managers, you can install Fusion-icon (form Ubuntu Software Center), which will give you a way to change between all managers installed whenever you wish.

Now use Google to get more info on the features of every one of the above window manager and/or decorators.

---

