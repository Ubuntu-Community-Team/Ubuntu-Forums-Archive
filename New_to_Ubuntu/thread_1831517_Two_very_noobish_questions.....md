---
title: "Two very noobish questions...."
date: 2011-08-23
forum: New to Ubuntu
---

### Post by asportking on 2011-08-23
I'm quite new to ubuntu, and I'm still trying to figure this thing out, but I needed to ask help for a few things.
First of all, when I go to youtube, I always get a black screen where the video is supposed to be. I've installed all the adobe stuff, and it worked fine yesterday, but now I can't get any videos to play. Also, firefox, folders, and a lot of other stuff always has this "windows 98 look" about them. I'm assuming this is the way ubuntu comes, but how can you change it? I tried messing around a bit with the appearance preferences, but I can't get it to change. Thanks in advance for your help!

---

### Post by Frogs Hair on 2011-08-23
Hi and Welcome

Ubuntu is not supposed to look that way , it is a bug that affects some computers . Restarting works for some users , but I get the impression this is not working for you . There is a possible fix at the link .
 [http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

---

### Post by asportking on 2011-08-23
> **Frogs Hair said:**
> Hi and Welcome

Ubuntu is not supposed to look that way , it is a bug that affects some computers . Restarting works for some users , but I get the impression this is not working for you . There is a possible fix at the link .
 [http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)
Worked great! Thanks!

---

### Post by asportking on 2011-08-23
Ok, besides the black screen problem (which now just kind of comes and goes), I'm trying to download some themes from "gnome-look.org" (I'm assuming it's a fairly well-known site), and it's saying to extract the files into some ".themes" folder. Problem is, I can't seem to find that folder. Tried searching for it but still couldn't find it. Where is it, or is there a different way I should be applying the themes?

---

### Post by zealibib slaughter on 2011-08-23
> **asportking said:**
> Ok, besides the black screen problem (which now just kind of comes and goes), I'm trying to download some themes from "gnome-look.org" (I'm assuming it's a fairly well-known site), and it's saying to extract the files into some ".themes" folder. Problem is, I can't seem to find that folder. Tried searching for it but still couldn't find it. Where is it, or is there a different way I should be applying the themes?
 
The "." means its hidden, in nautilus just press <ctrl> H to see the hidden files.

---

### Post by madjr on 2011-08-23
> **asportking said:**
> Ok, besides the black screen problem (which now just kind of comes and goes), I'm trying to download some themes from "gnome-look.org" (I'm assuming it's a fairly well-known site), and it's saying to extract the files into some ".themes" folder. Problem is, I can't seem to find that folder. Tried searching for it but still couldn't find it. Where is it, or is there a different way I should be applying the themes?

[http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html](http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html)

also some themes may have special instructions

if you are using 11.04
some themes here:

[http://www.redmondpie.com/4-beautiful-ubuntu-unity-themes-complete-with-how-to-download-and-install/](http://www.redmondpie.com/4-beautiful-ubuntu-unity-themes-complete-with-how-to-download-and-install/)
[http://www.webupd8.org/2011/05/elementary-orta-and-minty-freshness.html](http://www.webupd8.org/2011/05/elementary-orta-and-minty-freshness.html)

---

### Post by asportking on 2011-08-23
> **madjr said:**
> [http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html](http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html)

also some themes may have special instructions

if you are using 11.04
some themes here:

[http://www.redmondpie.com/4-beautiful-ubuntu-unity-themes-complete-with-how-to-download-and-install/](http://www.redmondpie.com/4-beautiful-ubuntu-unity-themes-complete-with-how-to-download-and-install/)
[http://www.webupd8.org/2011/05/elementary-orta-and-minty-freshness.html](http://www.webupd8.org/2011/05/elementary-orta-and-minty-freshness.html)
Thanks, worked like a charm!
Sorry, but I've got one last question (I'll try to figure out stuff on my own after this question). My title bar (not sure if that's what it's called, it's the thing right above the window where you minimize, exit out windows and things like that) has mysteriously disappeared. Whenever I open a new window, it doesn't have that bar at the top. I don't know if it's something I did, or if it's a glitch, but does anyone have any suggestions? I tried restarting my computer, but it didn't help.

---

### Post by sandyd on 2011-08-23
> **asportking said:**
> Thanks, worked like a charm!
Sorry, but I've got one last question (I'll try to figure out stuff on my own after this question). My title bar (not sure if that's what it's called, it's the thing right above the window where you minimize, exit out windows and things like that) has mysteriously disappeared. Whenever I open a new window, it doesn't have that bar at the top. I don't know if it's something I did, or if it's a glitch, but does anyone have any suggestions? I tried restarting my computer, but it didn't help.
[s]Do you have the window full screened?

if you do, its on the top-left on the screen, right on the taskbar.[/s]

Stupid question. of course the window isn't full screened...

It sounds like what Ubuntu looks like when whatever window manager it uses crashes....

Open a terminal, and try

```

compiz --replace
```

---

### Post by asportking on 2011-08-23
> **sandyd said:**
> [s]Do you have the window full screened?

if you do, its on the top-left on the screen, right on the taskbar.[/s]

Stupid question. of course the window isn't full screened...

It sounds like what Ubuntu looks like when whatever window manager it uses crashes....

Open a terminal, and try

```

compiz --replace
```
Nope, sorry didn't help. When I typed it in, everything disappeared for a few seconds except for the background, then it all came back, but it didn't fix the problem. If it helps, I think the problem happened soon after I enabled "window decoration" on the compizconfig settings manager (I was trying to get that themes problem sorted out at the time).

---

### Post by madjr on 2011-08-23
> **asportking said:**
> Thanks, worked like a charm!
Sorry, but I've got one last question (I'll try to figure out stuff on my own after this question). My title bar (not sure if that's what it's called, it's the thing right above the window where you minimize, exit out windows and things like that) has mysteriously disappeared. Whenever I open a new window, it doesn't have that bar at the top. I don't know if it's something I did, or if it's a glitch, but does anyone have any suggestions? I tried restarting my computer, but it didn't help.

you can try installing all updates.

also a screenshot of your desktop would help.

hit the print screen key on your keyboard

---

### Post by asportking on 2011-08-23
> **madjr said:**
> you can try installing all updates.

also a screenshot of your desktop would help.

hit the print screen key on your keyboard
Here it is.
By the way, tried installing the updates. Restarted computer, and they still weren't showing up.

EDIT: The windows 98 thing came back up. Not sure why, it was working fine until a while ago. Sorry, but I guess I'm in need of even more help.

---

### Post by madjr on 2011-08-23
were you trying to install emerald themes also?

i think you messed something up with ccsm.

you should try to avoid using this tool, since compiz has been changing a lot starting 11.04 to integrate further with ubuntu.

in fact, ccsm will probably not be available in the next version (11.10) because of all the changes and people messing things up.

have you tried this:

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)


ps. seems webupd8 has become your new fav site now :P

---

