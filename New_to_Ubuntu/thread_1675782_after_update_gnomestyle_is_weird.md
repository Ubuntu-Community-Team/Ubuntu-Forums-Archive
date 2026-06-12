---
title: "after update gnomestyle is weird"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by toffifeemann on 2011-01-26
hey guys,
this morning i ran an update, now for some reason everytime i boot, the whole gnomestyle is changed... after a few seconds everything changes back to normal besides the style of nautilus and its icons
see the screenshot [IMG]https://dl-web.dropbox.com/get/Photos/ugly.jpg?w=dbf7aad7[/IMG]
i already tried changing back the style under pref->appearance, general styles and styles of icons etc...
i run ubuntu 10.10 and i would like this to go back to normal, hope someone can help me
ps: im not too deep into ubuntu so please explain what i have to do well, thanks!

---

### Post by coffeecat on 2011-01-26
Two things:

You forgot to add the screenshot! :) When you post it, please use the 'manage attachments' utility (you can use the paperclip icon in the message toolbar) to upload an image rather than linking to a off-site image hosting site.

Second - you've tagged your thread 'Lubuntu', yet you seem to be talking about Ubuntu/gnome. Please clarify.

---

### Post by toffifeemann on 2011-01-26
1. oh yeah oops sorry, ill do that
2. sorry again, apparently i clicked the wrong thing in the dropdown menu, yeah it's an ubuntu/gnome issue - how can i change it to ubuntu?
thanks!

---

### Post by coffeecat on 2011-01-26
I found the following on another thread about this issue, but I can't guarantee it will work. What it does is to remove the configuration files for Nautilus so that when you restart they are regenerated to default settings. Hopefully, this will cure this ugly theme but it will also change any settings you have made yourself in Nautilus.

Two methods, from the GUI and from a terminal.

From the GUI: Open your home folder and press ctrl-H to reveal hidden files. Open the .gconf folder and then the apps folder. Now delete the 'nautilus' folder and all contents. Now reboot.

From the terminal:

```
rm -vr ~/.gconf/apps/nautilus && sudo reboot
```

As far as the Lubuntu tag is concerned, if you can't change that yourself, you can ask a moderator to do it for you. Use the [img]http://ubuntuforums.org/images/buttons/report.gif[/img] button against your own post to send a request to a moderator. Don't worry that it says 'Report Abuse'. It can be used for more innocent requests as well. :)

---

### Post by toffifeemann on 2011-02-10
hey, sorry for the late reply, was quite busy lately
anyway, the problem didnt go away, now, sometimes the laptop boots fine and everything is the way i like it, but more often than not the whole theme is ugly again, i have to go to appearances and the windowstyle changes back to normal but nautilus doesn't.
I just tried you approach but it didn't help.

Any other suggestion? 

Also after that update when it changed to this ugly theme, the buttons to close, maximize and minimize buttons were on the top left, now they're back on the top right, how can i change this?

about the lubuntu prefix: i reported abuse, thanks!

---

