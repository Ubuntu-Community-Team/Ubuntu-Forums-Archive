---
title: "GDM2 themes"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by EgoGratis on 2010-12-05
I search the net and see all this beautiful GDM themes and always wonder, why GDM2 took such a big step back? Why are there no beautiful GDM2 themes i can choose from?

Where there any troubles with GDM and themes? Or why did GDM2 take away themes so now we don't have any to choose from!?

---

### Post by wojox on 2010-12-05
All you can do now is change the wallpaper, fonts, and theme like this

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using Ctrl+ALT+F7 or F8
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

---

### Post by EgoGratis on 2010-12-05
Yes thanks for explanation. I know you can change small things. But i want to be able to change the whole thing. Like this GDM examples:

[http://ubuntumanual.org/posts/222/20-gdm-themes-for-ubuntu-you-probably-haven-t-seen-before](http://ubuntumanual.org/posts/222/20-gdm-themes-for-ubuntu-you-probably-haven-t-seen-before)

Today i found this:

[http://www.omgubuntu.co.uk/2010/12/did-you-know-gdm-2-30-is-still-themeable/](http://www.omgubuntu.co.uk/2010/12/did-you-know-gdm-2-30-is-still-themeable/)

Aparently there are **.ui **files inside folder:

**/usr/share/gdm**

Will in near future we be able to enjoy customized GDM2 themes from other users we find in the web? What is the reason somebody would not make this possible in GDM2? Where there any troubles with themes and GDM? Does souch a thing as gdm2 theme package exist in this moment or not?

---

### Post by JOHNNYG713 on 2010-12-05
Python gdm2 [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)
NOTE, If you have installed new themes via appearances, To get the themes to show up in Python gdm2 menu you must:
1 Open terminal type sudo nautilus
2 Go to home folder  then, cntrl+h (This will show hidden folders)
3 Copy the themes from .themes to, usr/share/themes
4 Also copy any icons you have installed from .icons to usr/share/icons
5 You can now delete the themes and icons from .themes and .icons in your unhidden home folder, (Or you will have two instances of these themes and icons in appearances)
You must repeat this every time you install a theme or icon set if you want them to show in Python gdm2 menu !

---

### Post by EgoGratis on 2010-12-05
Yes again thanks for reply and explanation. Useful stuff!  I know about gdm2setup BUT:

You can't do this with gdm2setup for example:

[IMG]http://ubuntumanual.org/files/u1/90685-1.jpg[/IMG]

This is what i am after. Not just background, icons, fonts... BUT the whole thing as in GDM! Themes examples:

[http://gnome-look.org/index.php?xcontentmode=150](http://gnome-look.org/index.php?xcontentmode=150)

Why GDM2 made thing in theming area in the way that i can't find any themes at all for GDM2 in the web today? Where there any problems with themes and GDM? Is it to hard to implement or is implemented but too hard to use? What is the reason behind GDM2 not having nice theme packages available on the web?

---

### Post by JOHNNYG713 on 2010-12-05
Well If you are running Ubuntu Lucid there is gdm2.20,** [http://www.google.com/url?sa=t&source=web&cd=3&ved=0CB8QFjAC&url=https%3A%2F%2Flaunchpad.net%2Fubuntu%2Flucid%2F%2Bpackage%2Fgdm-2.20&rct=j&q=gdm%202.20%20launchpad&ei=rfH7TKGfOJKBnAeNqonGCg&usg=AFQjCNEDMUgcG_FdxQZYB0jxQDlThgIHHw&cad=rja](http://www.google.com/url?sa=t&source=web&cd=3&ved=0CB8QFjAC&url=https%3A%2F%2Flaunchpad.net%2Fubuntu%2Flucid%2F%2Bpackage%2Fgdm-2.20&rct=j&q=gdm%202.20%20launchpad&ei=rfH7TKGfOJKBnAeNqonGCg&usg=AFQjCNEDMUgcG_FdxQZYB0jxQDlThgIHHw&cad=rja)** That will give you your old login screen, BUT!  you lose Plymouth and you have no complete startup experience! no plymouth, no xspash, no usplash, and I would assume, no splashy ether ! (I have not tried splashy) I am sure given time some one will work this out!

---

### Post by EgoGratis on 2010-12-05
If something (old) will not be used in Ubuntu any more, that is not the solution. 

The Question is still the same.

> Why GDM2 made thing in theming area in the way that i can't find any  themes at all for GDM2 in the web today? Where there any problems with  themes and GDM? Is it to hard to implement or is implemented but too  hard to use? What is the reason behind GDM2 not having nice theme  packages available on the web?

Thanks.

---

### Post by TechZilla on 2011-05-04
I'm sure many users are not happy about loosing the gdm themes.

i actually like something very plain, but even that is not fully possible with gdm2.

even things that an unthematic KDM can do would suffice.  Essentially even gconf provides few config changes.

---

### Post by EgoGratis on 2011-05-27
Will LightDM in Oneiric Ocelot bring back themes? Any additional thoughts on LightDM?

Thanks!

---

### Post by EgoGratis on 2011-06-26
> LightDM is - as the name says - much lighter then GDM and is very easy to theme (it uses HTML, CSS and Javascript). 

[http://www.webupd8.org/2011/05/lightdm-to-be-default-display-manager.html](http://www.webupd8.org/2011/05/lightdm-to-be-default-display-manager.html)

Glad to hear users of Ubuntu will have custom themes again! :D

Solved!

---

