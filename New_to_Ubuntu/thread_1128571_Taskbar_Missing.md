---
title: "Taskbar Missing"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by shiva2285 on 2009-04-17
HI
I am not able to locate my missing taskbar..and i am new to this OS..so i have no idea how to proceed..and i did little bit of reserach and i could not figure it out exatcly.....all the time i have to use alt+tab to switch between differnt windows i opened..

---

### Post by ninjapirate89 on 2009-04-17
Sounds like you deleted your bottom panel. Do you still have a top panel?

---

### Post by ninjapirate89 on 2009-04-17
If you do still have a top panel just right click on it and click New Panel. A new panel will appear on bottom. Next right-click on this newly created panel and click Add To Panel. I can't remember for certain what applets are included by default but I do know that the applet that shows your open windows is named Window List.

---

### Post by roger_1960 on 2009-04-17
Hi

In KDE

Try alt-F2 then "kicker"

---

### Post by SuperSonic4 on 2009-04-17
You can also type "plasma" instead of "kicker"

---

### Post by qarma on 2009-05-07
I have the same problem. No taskbar visible. Only the desktop icons. 

But this "Alt-F2" tip is not helping me. Nothing happens when I push the combination. 

I am using the Netbook Remix edition on an Aspire One.

---

### Post by kwokyinc on 2009-05-07
Easy. See below.

Copied from: [http://userbase.kde.org/Plasma#My_panel_is_gone.2C_how_do_I_get_it_back.3F](http://userbase.kde.org/Plasma#My_panel_is_gone.2C_how_do_I_get_it_back.3F)




_**My panel is gone, how do I get it back?**_

Input the following command: 

```
kquitapp plasma; rm $KDEHOME/share/config/plasma-appletsrc; plasma
```

This deletes your plasma settings, so you'll get the default configuration back. If running all the 3 commands at once doesn't work, try typing them in manually and wait a few seconds before running the next command. 

(Note that the $KDEHOME environment variable may not be set. Try ~/.kde (Fedora, Kubuntu Intrepid, Debian, upstream default) or ~/.kde4 (OpenSUSE, Kubuntu Hardy and several others).)

---

### Post by Zyto on 2009-06-28
This is the code that worked for my kubuntu 9.04 machine

```
kquitapp plasma; sudo rm ~/.kde/share/config/plasma-appletsrc; plasma
```

Thanks to all those who put time into finding this solution!

---

