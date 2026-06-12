---
title: "Changing Colors of the Main Menu Progress Bar etc..."
date: 2010-04-24
forum: New to Ubuntu
---

### Post by guguma on 2010-04-24
Hello All,

I am using ubuntu 9.10 with the New Wave theme and I am trying to do some customization but I am confused.

What I am trying to do is change the colors of gnome the progress bar, add some transparency to the main menu and change the colors of the main menu. 

The weird thing is I do not get many options in System-> Preferences-> Appearance and I do not see any System-> Preferences-> Themes.

Compiz has a window decorator section which is useless? Tried gnome-color-chooser which did not do anything.

This has always been the reason for me not to get used to linux I have no idea which application is controlling what? I remember making myself a nice menu and change the progress bar without external apps or another theme installed now I cannot find anything.

I truly appreciate any help you can throw in.

Thanks in advance.

---

### Post by guguma on 2010-04-29
Hello All,

Figured this stuff out and it turns out that all this is theme dependent. It seems that gnome-color-chooser does not work with all themes (if you want to change the color of a particular object and it uses an image rather than a color, it won't work).

**Change The Progress Bar**

Needed to find the progress bar images under the /usr/share/themes/-used theme/ and change the images

**Change the Main Menu Color**

Needed to find the main menu images under the /usr/share/themes/-used theme/ and change the images

**Transparency**

Under the Opacity, Brightness ... option under accessibility options in compiz-config-settings manager.

---

