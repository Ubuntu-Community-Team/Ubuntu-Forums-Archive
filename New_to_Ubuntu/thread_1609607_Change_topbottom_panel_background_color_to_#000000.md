---
title: "Change top/bottom panel background color to #000000 (darker than applet background)"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2010-10-30
Hi there, I have changed the panel background color to be pitch black #00000--but the inherent color that comes with Ambiance theme where the applets sit have a grayish tinge--I want this background to also honor the settings I want i.e. #000000; How do I change this color?

See screenshot of what I am talking about.

Thanks
S

---

### Post by starcraft.man on 2010-10-30
I think you want:

Step 1:
system > preferences > appearance, right click theme on the page, colours tab. 

Step 2:
play?

---

### Post by shuttleworthwannabe on 2010-10-30
> **starcraft.man said:**
> I think you want:

Step 1:
system > preferences > appearance, right click theme on the page, colours tab. 

Step 2:
play?

Thanks for the suggestions--I tried that but the background color where the applets sit is stubbornly grey.

Here is [another thread]("http://ubuntuforums.org/showpost.php?p=9629583&postcount=5") of what I want to achieve--but the gtkrc file in the themes folder does not have that line to block out.

---

### Post by buntudawg on 2010-10-30
Removed-Misread post

---

### Post by shuttleworthwannabe on 2010-10-30
I have done that and the result is the screenshot image--look carefully at the top panel and you will see the difference in the contrast of the background color where the menu bar is and the system tray applets--this color is grey; the rest of panel on the another hand is pitch  black with pellet #000000

also see the thread link with a solution--but in maverick this gtkrc file in the themes folder does not have those lines to # out?

Hope I am making sense here?

S

---

### Post by starcraft.man on 2010-10-30
> **shuttleworthwannabe said:**
> I have done that and the result is the screenshot image--look carefully at the top panel and you will see the difference in the contrast of the background color where the menu bar is and the system tray applets--this color is grey; the rest of panel on the another hand is pitch  black with pellet #000000

also see the thread link with a solution--but in maverick this gtkrc file in the themes folder does not have those lines to # out?

Hope I am making sense here?

S

I just opened up the gtkrc file for ambiance theme and at the very top I see bg_color:#FFFF.

Try editting these color definitions. Make a backup first. Shouldn't be too hard.

Edit: To be clear, the line is gtk-color-scheme. Wish we had easier tools.

---

### Post by shuttleworthwannabe on 2010-10-30
> gtk-color-scheme = "base_color:#ffffff\nfg_color:#4c4c4c\ntooltip_fg_color:#ffffff\nselected_bg_color:#f07746\nselected_fg_color:#FFFFFF\ntext_color:#3C3C3C\nbg_color:#F2F1F0\ntooltip_bg_color:#000000\nlink_color:#DD4814"


I do not see what you see, sorry.

In the other thread, I commented out the following line:
> #include "apps/gnome-panel.rc"
It is right at the bpttom--this sorta fixes the panel colors to be same but big problem now--clock fonts are not visible? Bummer.

BTW, I > sudo cp -R /usr/share/themes/Ambiance ~/.themes/
 and then edited the gtkrc file.

How to get the Clock font back to white?

---

### Post by shuttleworthwannabe on 2010-10-31
Guys, [here is the solution for all]("http://www.webupd8.org/2009/08/modify-colors-on-your-gnome-desktop.html")--gnome-color-chooser!

Enjoy!

---

