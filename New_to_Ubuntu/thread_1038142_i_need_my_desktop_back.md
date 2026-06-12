---
title: "i need my desktop back"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by halovivek on 2009-01-12
hi
i installed using [this one]("http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/").
[http://anuragbansal.wordpress.com/](http://anuragbansal.wordpress.com/)
now i want my normal desktop. please guide me.

---

### Post by mjheagle8 on 2009-01-12
i'd presume just undo the steps in the article.
in gconf-editor, go to apps > nautilus > preference, reselect show desktop
in ccsm, under Desktop Cube >Appearance > Background images remove the additional wallpapers you have added. 
hope this helps!

---

### Post by halovivek on 2009-01-14
> **mjheagle8 said:**
> i'd presume just undo the steps in the article.
in gconf-editor, go to apps > nautilus > preference, reselect show desktop
in ccsm, under Desktop Cube >Appearance > Background images remove the additional wallpapers you have added. 
hope this helps!

I tried to open ccsm but it is not displayed. how to go ahead.

---

### Post by Elfy on 2009-01-14
If you haven't got it installed I wonder how you followed the how-to.. but to install

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by mjheagle8 on 2009-01-14
> **halovivek said:**
> I tried to open ccsm but it is not displayed. how to go ahead.

what do you mean it is not displayed? you dont have the program? you try to open the program and it doesnt open?
if you dont have program, 
```
sudo apt-get install compizconfig-settings-manager
```
if it doesnt open, open a terminal, type
```
ccsm
```
and post the output please.

---

### Post by halovivek on 2009-01-14
i could get the ccsm window. but i could not get the tool bar like mac in ubuntu. how to get it?

---

### Post by mjheagle8 on 2009-01-14
thats called the avant window navigator, or awn. to get it type
```
sudo apt-get install avant-window-navigator
``` in the terminal.
if you already have it, you can launch it by applications>accessories>avant window navigator.  if you want it to launch on startup, go to system>preferences>sessions and add a new item with the command ```
avant-window-navigator
```

---

### Post by halovivek on 2009-01-15
> **mjheagle8 said:**
> thats called the avant window navigator, or awn. to get it type
```
sudo apt-get install avant-window-navigator
``` in the terminal.
if you already have it, you can launch it by applications>accessories>avant window navigator.  if you want it to launch on startup, go to system>preferences>sessions and add a new item with the command ```
avant-window-navigator
```

gurudheva@gurudheva-laptop:~$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.


i am getting above one how to do that one_?

---

### Post by Elfy on 2009-01-15
You need to run compiz - go to appearances in your system preferences menu and then visual effects - if it is set to none then compiz is off.

---

### Post by mjheagle8 on 2009-01-15
you can launch compiz by opening a terminal and entering ```
compiz
```

---

### Post by halovivek on 2009-01-15
> **forestpixie said:**
> You need tor un compiz - got appearances in your system preferences menu and then visual effects - if it is set to none then compiz is off.

I dont know how to do this one. could you please help me? i need more explanation on this.

---

### Post by Elfy on 2009-01-15
Have you opened Appearances in the system preferences menu? One of the tabs is Visual appearances - it is as simple as that.

If the None is active - you have not got compiz active - all of the others use compiz.

---

### Post by mjheagle8 on 2009-01-15
do you have compiz installed?

---

### Post by halovivek on 2009-01-16
I dont know how to check this?

---

### Post by Elfy on 2009-01-16
Compiz is installed by default from hardy, or if not hardy then intrepid.

Have you actually tried to do anything that people are telling you - if you have and still get problems then you need to say so.

---

### Post by halovivek on 2009-01-16
i am using ubuntu 64bit version 8.10. how to check further that i have installed?

---

### Post by mjheagle8 on 2009-01-16
you have compiz installed then by default.

---

### Post by halovivek on 2009-01-16
> **forestpixie said:**
> Have you opened Appearances in the system preferences menu? One of the tabs is Visual appearances - it is as simple as that.

If the None is active - you have not got compiz active - all of the others use compiz.

Thank you so much ...finally i got it by activating as you said. i went i clicked it. 

i have posted that one for you all.


how to get it automatically when i login to ubuntu?

---

### Post by Elfy on 2009-01-16
From the system - preferences menu - pick sessions.

It will open a window - Add - out a description in the name and comment, in the command box

```
avant-window-navigator
```

close and it should start in boot

---

### Post by halovivek on 2009-01-16
I tried and working fine. After installing this one. if i open the movie or video screen keeps flickers. previously it was not. how to over come? this one.

---

### Post by Elfy on 2009-01-16
I've seen other issues with ati cards and compiz causing problems with videos - the answers there were turn it off to watch films - but then awn will fail.

Perhaps someone else will chime in on that.

---

### Post by mjheagle8 on 2009-01-16
> **halovivek said:**
> I tried and working fine. After installing this one. if i open the movie or video screen keeps flickers. previously it was not. how to over come? this one.

what type of movie? some movie types, such as mp4, sometimes flicker when being viewed while running compiz.

---

### Post by halovivek on 2009-01-16
> **mjheagle8 said:**
> what type of movie? some movie types, such as mp4, sometimes flicker when being viewed while running compiz.

Yes it is mp4 movies. how to over come this?

---

### Post by mjheagle8 on 2009-01-16
maybe convert it to another file type? its always been an issue for me. sometimes it works better when you dont use any other multimedia programs at the same time.

---

### Post by halovivek on 2009-01-17
> **mjheagle8 said:**
> maybe convert it to another file type? its always been an issue for me. sometimes it works better when you dont use any other multimedia programs at the same time.

Ok so there is no chance in getting fixed for jumping screen?

---

### Post by mjheagle8 on 2009-01-17
idk. maybe sometime in the future. if there is a way, i dont know about it.

---

