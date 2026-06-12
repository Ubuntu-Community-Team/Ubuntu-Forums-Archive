---
title: "Gnome Shell"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Jeff.Smith on 2010-11-15
I'm trying out gnome shell on my test machine to see if I will be running it on my main machine in the future. Right now I really like the way it is set up but I have some questions that I can't seem to find answers to on any of the online literature (most of the gnome shell stuff seems to be outdated and mostly useless to me). 

The first question is: Is there a way for me to bind keyboard/mouse buttons to various gnome features? For example, right now if you go to the top left of gnome shell it will take you to a kind of overview of your workspaces and applications, is there a way to do that via a mouse gesture or keyboard sequence?

Second question: One of the new features in gnome shell is the ability to use the 'sidebar', which allows you to quickly access applications and such. Is there a way to get a different theme for this or are you stuck with the gray one that it comes with?

Right now those are the only two questions that I have (I just started using it a short time ago) but the first one in particular is very important to me and if anyone knows the answer, please share.

Thanks


EDIT: There has to be a script that is being run upon the mouseover of the top left. I just need to know that script so that I can bind it in compiz and do it that way. Or if there is an easier way, meh, I guess that'll work as well :)

---

### Post by weasel fierce on 2010-11-15
Not a lot of customization, but it should set up a keyboard shortcut for opening the sidebar. Try the left windows / "PC" key. I dont have it installed currently, but I know it set one up by default.

---

### Post by Jeff.Smith on 2010-11-15
> **weasel fierce said:**
> Not a lot of customization, but it should set up a keyboard shortcut for opening the sidebar. Try the left windows / "PC" key. I dont have it installed currently, but I know it set one up by default.

the left windows key does open up the overview of all of your workspaces and applications, but I would rather it be done by a mouse gesture. I was trying to find the script/command that is run when the 'windows'/super key is pressed but I cant find a reference to it anywhere. If I have this command I can bind it to whatever in compiz, so that is really all I need.

---

### Post by Jeff.Smith on 2010-11-16
Bump. Anyone?

---

### Post by blackvd on 2010-11-17
I just installed it today so for themes you can go here.

[http://www.techdrivein.com/2010/09/top-6-gnome-shell-themes-ever.html]("http://http://www.techdrivein.com/2010/09/top-6-gnome-shell-themes-ever.html")

I'm using Dark Glass as its pretty amazing. 

As for your other question try checking the system preferences menu in the top right, it has tons of options to configure. FYI leave compiz off, it froze my box.

---

### Post by toekneewood on 2010-11-17
Not 100% sure but I thought that 10.10 did gesture-based window management.  Take a look at the following, it might help 

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

---

### Post by Jeff.Smith on 2010-11-22
> **blackvd said:**
> I just installed it today so for themes you can go here.

[http://www.techdrivein.com/2010/09/top-6-gnome-shell-themes-ever.html]("http://http://www.techdrivein.com/2010/09/top-6-gnome-shell-themes-ever.html")

I'm using Dark Glass as its pretty amazing. 

As for your other question try checking the system preferences menu in the top right, it has tons of options to configure. FYI leave compiz off, it froze my box.

Thanks for the themes, some of those look really good.

 Unfortunately, I went through all of the preferences, and there is nothing in there about mouse gestures. Thanks for the heads up about Compiz though. Makes the problem a little more difficult but hey, I'm sure someone here at the forum is up to it. 

>  Not 100% sure but I thought that 10.10 did gesture-based window management. Take a look at the following, it might help

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

Unfortunately, I'm pretty sure that wiki is referring to multitouch functionality for touchscreens as apposed to trackpads. Also, I am running gnome shell over 10.04 LTS. 

So, my question still remains. Is there anyway to customize gnome shell in such a way that allows you to get to the overview screen via a mouse gesture? I would really appreciate any help that anyone can provide. I've been attempting to use it on my main machine and it really slows me down not being able to use a mouse gesture to execute this command. Please help.

Thanks,
Jeff

---

### Post by admiralspark on 2010-11-22
The overview screen is not a function of Gnome, but of the Compiz WM. <IF> you can get compiz to work with gnome shell, you should be able to re-enable the feature through the "CompizConfig Settings Manager". It is enabled by default because your 'old' gnome desktop had the Extra visual effects enabled in Appearance Preferences > Visual Effects.

Let us know if Compiz works with it, I'm assuming that the Shell will want to use it's own visual effects and so it won't. Good luck!

---

### Post by Jeff.Smith on 2010-11-22
> **admiralspark said:**
> The overview screen is not a function of Gnome, but of the Compiz WM. <IF> you can get compiz to work with gnome shell, you should be able to re-enable the feature through the "CompizConfig Settings Manager". It is enabled by default because your 'old' gnome desktop had the Extra visual effects enabled in Appearance Preferences > Visual Effects.

Let us know if Compiz works with it, I'm assuming that the Shell will want to use it's own visual effects and so it won't. Good luck!

[strike]As far as I can tell Compiz isn't installed on my machine.[/strike] Also, before I installed shell it was a clean install of ubuntu, I hadn't installed any extra programs yet. 

I'll try to download Compiz and see if I can get it working that way. I should mention that, while gnome shell is running it will not let me change the visual effects in Preferences. It says "mutter is running" so I won't be able to change them.

---

### Post by Harry33 on 2010-11-23
> **Jeff.Smith said:**
> [strike]As far as I can tell Compiz isn't installed on my machine.[/strike] Also, before I installed shell it was a clean install of ubuntu, I hadn't installed any extra programs yet. 

I'll try to download Compiz and see if I can get it working that way. I should mention that, while gnome shell is running it will not let me change the visual effects in Preferences. It says "mutter is running" so I won't be able to change them.

The overview screen is not a function of Compiz.
Gnome-shell does not use Compiz at all.
Gnome-shell uses clutter and mutter.

---

### Post by Jeff.Smith on 2010-11-23
> **Harry33 said:**
> The overview screen is not a function of Compiz.
Gnome-shell does not use Compiz at all.
Gnome-shell uses clutter and mutter.

right, so is there a way to get gnome shell to allow me to use a mouse gesture to get to the overview screen? I thought I might be able to figure out the command that it was executing and then bind it in compiz, but obviously there are problems with that, so is there a workaround?

---

### Post by Harry33 on 2010-11-23
In Gnome-Shell there are three ways to open the overview screen:

1) mouse gesture: moving the mouse cursor to the upper left corner (hot spot)
2) mouse click: clicking on the word Activity (on the panel)
3) keyboard: pressing the super (windows) key

---

### Post by Jeff.Smith on 2010-11-25
> **Harry33 said:**
> In Gnome-Shell there are three ways to open the overview screen:

1) mouse gesture: moving the mouse cursor to the upper left corner (hot spot)
2) mouse click: clicking on the word Activity (on the panel)
3) keyboard: pressing the super (windows) key

I know of all three of these. Is there any way to change them? For instance to a middle mouse click or something. Moving to the top left is annoying to me and I'd rather it be something else.

---

### Post by Harry33 on 2010-11-26
> **Jeff.Smith said:**
> ... Is there any way to change them? For instance to a middle mouse click or something. Moving to the top left is annoying to me and I'd rather it be something else.

Perhaps there is.
For me the upper left corner is quite handy. After all, favourities are also there.
And doesn't almost every application panel have commands there too?
This way you do not have to click anywhere, only move the cursor and then one-click on application icon.

---

