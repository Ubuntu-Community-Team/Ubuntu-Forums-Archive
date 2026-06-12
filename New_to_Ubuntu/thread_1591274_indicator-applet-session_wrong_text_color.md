---
title: "indicator-applet-session wrong text color"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by aala on 2010-10-09
This is for the ones that may need to fix the wrong color of your "indicator-applet-session".

You know, how sometimes you happen to have a dark color panel and the text for your "window-list-applet" is white/or light color as it should be and the "clock-applet" works good also, but the new "indicator-applet-session" won't display the right color, and it's just annoying as hell.

Well if that's your case you might want to add the following to your gtkrc file; It should be in...
[LIST=1]If it's local: /home/your_name_here/.themes/your_theme_here/gtkrc
[/LIST]
[LIST=2]if it's system wide: /usr/share/themes/your_theme/gtkrc
[/LIST]

so just do, for quick access alt+F2 or open terminal and then:

for your local theme```
gedit /home/your_name_here/.themes/your_theme_here/gtkrc
```
for a system wide installed theme
```
sudo gedit /usr/share/themes/your_theme/gtkrc
```

and then add the following code within the widgets configuration...
```
widget "*fast-user-switch-applet*" style "panel"
```...
save and exit,... logout and log back in, and it should be good now or just do: press alt+F2 and then type```
pkill gnome-panel
```and I think that will also do the job without logging out....

Hopefully it'll work for you guys. It does for me so, I don't see why it wouldn't work for you!

Good luck! :guitar::popcorn::lolflag: 
¡you might take a look at this 2 images to see with more detailed what I mean!

---

### Post by wanchai on 2010-11-21
This is great, works for me too. 

The more general question is how to find out the widget names that we need to use in gtkrc.

I'd also like to change the background of the Windows Selector applet but I didn't know how to reference it in gtkrc. Then I found out about [[COLOR="Blue"]gtkparasite[/COLOR]]("http://chipx86.gith*******/gtkparasite/") (it's in the repository). After [[COLOR="Blue"]disabling the gnome-panel[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7143619&postcount=6") I could restart it using [FONT="Courier New"]GTK_MODULES=gtkparasite gnome-panel[/FONT]. Then I was able to find the name of the windows selector applet widget: [FONT="Courier New"]window-menu-applet-button[/FONT]. I can now change the appearance of, for example, the background of the windows selector as it appears in the panel. However, I still haven't figured out how to change the next level, i.e. the menu entries that pop up when the window selector is clicked.

---

### Post by ardinotow on 2010-12-12
I use custom theme and here is my config where located in /home/ardinoto/.themes/Equinox olive bright
```
[Desktop Entry]
Name=Equinox olive bright
Type=X-GNOME-Metatheme
Comment=

[X-GNOME-Metatheme]
GtkTheme=MurrinaVerdeOlivo
MetacityTheme=Equinox Light Glass
IconTheme=Faenza-Dark
GtkColorScheme=fg_color:#000000000000,bg_color:#d3d3d7d7cfcf,text_color:#000000000000,base_color:#ffffffffffff,selected_fg_color:#ffffffffffff,selected_bg_color:#d2adddbe4739,tooltip_fg_color:#000000000000,tooltip_bg_color:#f5f5f5f5b5b5
CursorTheme=DMZ-Black
CursorSize=18
NotificationTheme=ubuntu
BackgroundImage=/media/entertainments/My Pictures/WALLPAPER/Green/Green - 0025.jpg
```

I have tried to add ```
widget "*fast-user-switch-applet*" style "panel"
``` in gtkrc where located in /usr/share/themes/MurrinaVerdeOlivo/gtk-2.0 but nothing change. What should I do?

---

### Post by xouns on 2011-03-09
I don't seem to have a gtkrc file, just an index.theme, which seem to contain the info. But then, when I add the line you said, my indicator applet is still grey in stead of the Dark Blue I specified for the text.

Is there a way to change it into a different colour altogether?

[edit: silly me, I was looking at icons. Problem solved]

---

