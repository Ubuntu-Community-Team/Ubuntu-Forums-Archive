---
title: "Can you name workspaces with compiz enabled?"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by diablo75 on 2009-03-26
I seem to be running into an issue with Compiz and or GNOME with workspace labeling and I'm beginning to feel this is a bug.

With Compiz enabled, I cannot seem to name workspaces.  The usual method of doing this is to right click on the workspace switcher, hit preferences, and a window will appear asking how many columns and rows and the number of work space I want, as well as what I want to name them.  However, with Compiz enabled, this preferences screen is reduced to only letting you specify the number of columns/rows and nothing else.

Another thing to note is that when Compiz is disabled, the named workspaces will show their names if you hover the mouse over the switcher.  For example, if I had named workspace 3 "Email" it would say, "Click here to switch to Email" if I hovered my mouse over it.  With Compiz enabled, the only thing that ever appears if you hover the mouse over ANY workspace in the switcher is "Current Workspace 'Desk 1'", *even if you aren't actually viewing the first workspace*.

So this appears to be a bug in my view.  Thoughts?

---

### Post by Lunx on 2009-03-26
> **diablo75 said:**
> .

So this appears to be a bug in my view.  Thoughts?

Yep, a bit of a google search shows this to be a pretty well known issue thats gone on for some time without the Compiz devs resolving it I guess.

---

### Post by Sambie on 2009-03-27
I think it's Gnome. whenever I go to system < preference < appearance and then to visual effects. I then click on None and Im able to get my workingspace switcher back. If I turn on my graphics it only gives me 2 working spaces, even know Im right clicking on my workspaces and attempting to add more spaces. It simply isn't working for me. I think it's gnome, if anybody else is having a problems with it.

On the related subject.... I'm having a diffcult time using the Cube... instead of giving me a cube... it's giving me a block... Do you think this causing the problem?

---

### Post by diablo75 on 2009-03-27
> **Sambie said:**
> I think it's Gnome. whenever I go to system < preference < appearance and then to visual effects. I then click on None and Im able to get my workingspace switcher back. If I turn on my graphics it only gives me 2 working spaces, even know Im right clicking on my workspaces and attempting to add more spaces. It simply isn't working for me. I think it's gnome, if anybody else is having a problems with it.

On the related subject.... I'm having a diffcult time using the Cube... instead of giving me a cube... it's giving me a block... Do you think this causing the problem?

If you enable visual effects, but you only have two workspaces, then you just need to increase the number of workspaces to four or more.  To do this, right-click on the work space switcher, hit Preferences, and you should get a box that will let you bump the number up.  Since you only have two right now, the cube is rendering as a two-sided flat surface because you only have two work spaces.  If you had three, you'd get a triangle.  Four would be a cube, and further on up, you'd have all kinds of other shapes.  You just need to bump the number up.

Back to my issue:  Workspace labeling/naming with effects enabled.  Is there a bug on launchpad I can subscribe to so I can track the progress of this issue?

---

### Post by diablo75 on 2009-03-28
> **diablo75 said:**
>   Workspace labeling/naming with effects enabled.  Is there a bug on launchpad I can subscribe to so I can track the progress of this issue?

Bump?

---

### Post by Sambie on 2009-04-09
> **diablo75 said:**
> If you enable visual effects, but you only have two workspaces, then you just need to increase the number of workspaces to four or more.  To do this, right-click on the work space switcher, hit Preferences, and you should get a box that will let you bump the number up.  


I already tried that and it's still not giving me my 4 workspaces. under Preferences on the workspaces I requested 4 columns and 1 row and when I exit Preferences, it's still giving me 2 columns. Do you know how to fix this problem?

---

### Post by Godly on 2009-04-09
Do you have desktop cube checked in Compizconfig Settings Manager?

---

### Post by lindis on 2009-04-20
been tring to solve this mystery also.
i get the same strange error on my ubuntu 8.10 with compiz installed
and cube enabled,cube effects e.t.c
But cannot figure out what is wrong.
i can also set 4 workspaces - but all will get the same name (workspace 1)

been trying all kind of settings -but no luck yet.

have anyone figured this one out yet?

/Lindis

---

### Post by ebeckhusen on 2009-04-20
I'm a little confused as to what you guys are setting, as the settings manager seems to use different terms than you do.  But here is my settings, which work for me to be able to get the cube.

Under General Options, Desktop Size set the sliders to the following:

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1

I apologize if this is the way you have them set, but as I said I don't understand how you have it currently set

As for naming the workspaces, I've never tried that, but if you can tell me where to find the option I can see if I can help you.

---

### Post by thekwill on 2010-06-10
I have the same issue on 10.04. I discovered it only yesterday when I unintentionally disabled compiz and suddenly I could name my workspaces. Now that I have compiz enabled again, the names have disappeared.

This bug seems to cover it (apparently a gnome-panel issue not a compiz issue): [URL="https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/239231"]https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/239231
[/URL]

---

### Post by stinkeye on 2010-06-10
It's got to do with the desktops being virtual in compiz.
In reality you only have one desktop.

But the good news is there is a plugin where you can name your virtual desktops and when you switch there is a display for up to 5 secs.

There is a script here which will download and compile some experimental plugins which includes a **workspacenames** plugin.
The script allows you to choose which plugins to install.
[_**[COLOR="DarkRed"]http://forum.compiz.org/viewtopic.php?f=114&t=12012[/COLOR]**_]("http://forum.compiz.org/viewtopic.php?f=114&t=12012")

---

### Post by chaeron on 2010-11-25
I installed the experimental plugin...nice....at least it tells you which workspace you've gone to. Thanks for the link Stinkeye!

But it still does not resolve the base issue where you can't show the workspace names in the gnome panel bar.

Frustrating...

---

