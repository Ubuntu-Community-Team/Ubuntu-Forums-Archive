---
title: "Lost panel item"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by 2steps on 2011-05-28
[SIZE=2]I recently switched over to ubuntu and there was a set of icons on my panel, one was the music player and the other an envelope for mail[/SIZE]. [SIZE=2]I have lost them somehow and wondered how to get them back?[/SIZE]

[SIZE=2]I am also having a problem with text, most of the time text I type or on websites is very small but within the applications, firefox etc it is ok or too big and I'm not sure how to change it as the settings I found dont seem to of done much. I keep having to adjust it manual pressing Ctrl + or - on most websites etc

Any help much appreciated :) Thank you[/SIZE]

---

### Post by rvchari on 2011-05-28
> **2steps said:**
> [SIZE=2]I recently switched over to ubuntu and there was a set of icons on my panel, one was the music player and the other an envelope for mail[/SIZE]. [SIZE=2]I have lost them somehow and wondered how to get them back?[/SIZE]

[SIZE=2]I am also having a problem with text, most of the time text I type or on websites is very small but within the applications, firefox etc it is ok or too big and I'm not sure how to change it as the settings I found dont seem to of done much. I keep having to adjust it manual pressing Ctrl + or - on most websites etc

Any help much appreciated :) Thank you[/SIZE]

right click on the panel and click on add to panel
you should get a list. add any of them listed. your email and music and weather and what not can be got back. they must ve been removed or deleted from the panel at some stage.

secondly, right click on the desktop and choose the desktop background. it will open a window, configure the theme / back ground / fonts and check out which font is best suited to you.

you can customize as you like !

---

### Post by 2steps on 2011-05-28
Thank you, the text things works but I can't find the other item. It wasn't the icon for the music player, when the music player was running but minimised I could click on it and see what the track was called and also stop the music or skip tracks in a little menu that popped up but it didnt open the full music player

---

### Post by 2steps on 2011-05-28
Found a setting to zoom text only so thats great :)

---

### Post by duke.tim on 2011-05-28
You can get them back by opening up synaptic package manager

do a search for "indicator" and marking for install any that you appear to be missing.

You can also do it from the terminal
```
sudo apt-get install indicator-weather

```

where weather could also be : network, sound, applet, applet-appmenu etc...

---

### Post by Swagman on 2011-05-28
or.. Providing his version of Ubuntu is **lower** than 11:04 (Natty Narwhal) he could do a top panel rebuild to put his top panel back to how it was from clean install


```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by dcsoldschool53 on 2011-05-28
WARNING!  DO NOT USING 11.04 NATTY, I DO NOT KNOW
 WHAT HARM USING THOSE COMMANDS WILL CAUSE ON YOUR SYSTEM. YOU HAVE BEEN WARNED. 

I like using this command to reset the panel back to when Ubuntu was first installed```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```and, when I have the panel configured the way I like it. I use this command to save a copy of the configuration to my hard drive```
gconftool-2 --dump /apps/panel > ~/panel_settings
```Then, I will use this command```
gconftool-2 --load ~/panel_settings && killall gnome-panel
``` to load my saved copy of gnome panel when I need it.

---

### Post by 2steps on 2011-05-29
[SIZE=2]I have it back though it only now shows when rhythmbox is playing whereas it was there all the time before and I can't move it where I want on the panel. It wasn't just the one icon, it was three together in a section - email, rhythmbox and volume controls. It's 10.4 

Have been using computers over 20 yrs but new to anything other than windows... oh and I'm a girl lol ;) Thanks for helping 
[/SIZE]

---

### Post by 2steps on 2011-05-29
Also can I make windows minimise into the bottom panel like on windows?

---

### Post by duke.tim on 2011-05-29
If you are using Gnome it should automatically be doing that...
If it got removed 
you right click the panel
then click "add to panel..."
select "window list"

---

### Post by 2steps on 2011-05-30
Thank you :)

---

### Post by dcsoldschool53 on 2011-05-30
2steps Don't forget to mark your thread as solved.

---

