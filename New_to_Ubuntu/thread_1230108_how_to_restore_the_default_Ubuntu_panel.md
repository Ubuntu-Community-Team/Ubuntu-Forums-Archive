---
title: "how to restore the default Ubuntu panel?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by jinhoward on 2009-08-03
:popcorn:I am a beginer of Ubuntu 9.04 .last night.I accidentally deleted the panel at the top of my desk,how can I restore it back .Is there anybody who can help me ?
Thanks!

---

### Post by naveedmanzoor21 on 2009-08-03
> **jinhoward said:**
> :popcorn:I am a beginer of Ubuntu 9.04 .last night.I accidentally deleted the panel at the top of my desk,how can I restore it back .Is there anybody who can help me ?
Thanks!


In a terminal, run   ps -A | grep gnome-panel , if you see it some thing like this

dtel@dtel-desktop:~$ ps -A | grep gnome-panel
 4436 ?        00:00:04 gnome-panel

meaning it's running, then run:

gconftool &#8211;recursive-unset /apps/panel && killall gnome-panel


 if you don't see it, then run:

gconftool &#8211;recursive-unset /apps/panel && gnome-panel

---

### Post by nothingspecial on 2009-08-03
Or if you didn`t understand all that you could right click on the bottom panel and choose new panel.

Then drag it to the top.

The right click on it and choose "add to panel" and choose the stuff you want to go there.

I think it`s gnome menu, firefox, evolution and notification area but put what you like on it.

---

### Post by jinhoward on 2009-08-03
> **nothingspecial said:**
> Or if you didn`t understand all that you could right click on the bottom panel and choose new panel.
 
Then drag it to the top.
 
The right click on it and choose "add to panel" and choose the stuff you want to go there.
 
I think it`s gnome menu, firefox, evolution and notification area but put what you like on it.
 I have tried what you said,but I simply couldn't make it to it's original state.Thanks anyway for your help!

---

### Post by 666f6f on 2010-03-08
> **naveedmanzoor21 said:**
> In a terminal, run   ps -A | grep gnome-panel , if you see it some thing like this

dtel@dtel-desktop:~$ ps -A | grep gnome-panel
 4436 ?        00:00:04 gnome-panel

meaning it's running, then run:

gconftool –recursive-unset /apps/panel && killall gnome-panel


 if you don't see it, then run:

gconftool –recursive-unset /apps/panel && gnome-panel

Small typo there, that should read *--recursive-unset*. Pretty obvious but whatever..

---

### Post by vinegar taster on 2010-03-22
Hi.  I'm also an Ubuntu newbie.  I have the same problem, but I'm using Karmic.  Will your solution still work?  I wanted to ask you before I actually tried it out, because I might do something that I will not be able to undo.  Thanks.

---

### Post by wojox on 2010-03-22
> **nothingspecial said:**
> Or if you didn`t understand all that you could right click on the bottom panel and choose new panel.

Then drag it to the top.

The right click on it and choose "add to panel" and choose the stuff you want to go there.

I think it`s gnome menu, firefox, evolution and notification area but put what you like on it.

Just do that. ;)

---

### Post by vinegar taster on 2010-03-25
> **naveedmanzoor21 said:**
> In a terminal, run   ps -A | grep gnome-panel , if you see it some thing like this

dtel@dtel-desktop:~$ ps -A | grep gnome-panel
 4436 ?        00:00:04 gnome-panel

meaning it's running, then run:

gconftool &#8211;recursive-unset /apps/panel && killall gnome-panel


 if you don't see it, then run:

gconftool &#8211;recursive-unset /apps/panel && gnome-panel
It works!  Thanks! :-)

---

### Post by jinhoward on 2010-04-06
> **vinegar taster said:**
> Hi. I'm also an Ubuntu newbie. I have the same problem, but I'm using Karmic. Will your solution still work? I wanted to ask you before I actually tried it out, because I might do something that I will not be able to undo. Thanks.
 
yes .It does works ,and the method I tried was can been seen below:
 
******************************solution********************
[I]In a terminal, run ps -A | grep gnome-panel , if you see it some thing like this

dtel@dtel-desktop:~$ ps -A | grep gnome-panel
4436 ? 00:00:04 gnome-panel

meaning it's running, then run:

gconftool –recursive-unset /apps/panel && killall gnome-panel


if you don't see it, then run:

gconftool –recursive-unset /apps/panel && gnome-panel[/I]
* *
********************************solution *******************
* *
*I hope this can also work for you system. good luck!*

---

