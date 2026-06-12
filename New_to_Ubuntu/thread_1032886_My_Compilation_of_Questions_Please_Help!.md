---
title: "My Compilation of Questions Please Help!"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by MaximoMilkman on 2009-01-06
Hey guys i am new to linux obviously.. im trying to get the 3d cube to work and the wobbly windows.. i have some version of that comp config or whatever that program is ... I had the checkboxes enabled on the wobbly windows and 3d cube but they wouldnt work!i hear people talking about compz-fusion or something like that where do i get that?? Is that a new version of the 3d boxes or something? Also is there a way to go back to default settings basically something that makes everything go back to the way it was on the first boot up.. ?? What is a BERYL theme and how can i use one of those?? ALSO where can i get an updated list of repositories or whatever you call them.. Anyone know of any docks for ubuntu/xubuntu that are semi easy to install or get?? I have so many questions i will keep them coming! =) this is quite a nift OS i must say but it is very difficult to navigate at first.. but i guess practice makes perfect.

---

### Post by JoshuaRL on 2009-01-06
Well, first off welcome to Ubuntu.  Now, as I understand it you have two problems, right?  I see Compiz with Desktop Cube and Wobbly Windows, and a dock that works well.

For Compiz, let's start off with a little information.  Compiz used to have just a few plugins and cool stuff it could do.  Nice, but conservative.  Then some developers broke off and made Beryl, an offshoot that was more wild, but less stable.  As of about Gutsy (7.10) they merged together again as Compiz-Fusion.  Yay!  

Now, to get the settings you want, go to Add/Remove Applications and make sure you have the Compiz Configuration Settings Manager, not just the Simple CCSM.  That way you can have full control of all the plugins Compiz has now.  To do that, go to System->Settings->Appearance and the Desktop Effects tab.  Make sure you have desktop effects on, and which one doesn't really matter.  After that, make all the changes you want in System->Settings->CompizConfig Settings Manager.

For a dock, you have two options.  Avant Window Navagator is like the MacOSX dock, and Cairo is like another menu/app launcher but in dock form.  Both are available from Add/Remove and work well, but require a compositor (read Compiz enabled system).

Does that help?

---

### Post by Kellemora on 2009-01-06
Hi MM

Compiz-fusion is in the repositories!
I'm not familiar with Xubuntu, but in Ubuntu you get it through Synaptic Package Manager.

To get a CUBE you need 4 workspaces turned on, default I think is only 2.

To see the CUBE you would hold down CTRL-ALT and the left mouse button, then spin the thumbwheel around to spin the box around.  (or move your mouse around I guess if you have that type).

Compiz requires a 3D accelerator graphics card in order to turn it on.  Else it will revert back to OFF each time you try to turn it on.

I have Compiz only loaded on one of my computers to show it off.
It has some nice features, like the wiggly windows, etc.  But since I need to move things around quite often, I leave it turned off.

I'm an old geezer, don't know about the rest of the stuff you are talking about!

TTUL
Gary

---

### Post by MaximoMilkman on 2009-01-06
somewhat but... i kinda got angry at my taskbar and ended up deleting the whole thing since for some reason a google searchbox look alike on my taskbar refused to go away so i was forced to delete my taskbar.. i heard some guys talking about some gnome code that can restore this do you know what it is??

---

### Post by MaximoMilkman on 2009-01-06
Kellemora yea i believe i have the requirments i tested it on there tester and i passed i have some integrated intel graphics controller but i guess it is good enough.. i will look into turning the 4 boxes on instead of 2 also thanks!

---

### Post by JoshuaRL on 2009-01-06
> **Kellemora said:**
> 
I'm not familiar with Xubuntu, but in Ubuntu you get it through Synaptic Package Manager.


Xubuntu is the base OS of Ubuntu but with XFCE as the desktop environment instead of Gnome.  It's lighter, uses less system resources, and can usually run on older computers a little better.  If you want to try it out, put this in:
```
sudo aptitude install xubuntu-desktop
```
And then just choose it from the Sessions menu on login.

> **MaximoMilkman said:**
> somewhat but... i kinda got angry at my taskbar and ended up deleting the whole thing since for some reason a google searchbox look alike on my taskbar refused to go away so i was forced to delete my taskbar.. i heard some guys talking about some gnome code that can restore this do you know what it is??

Ooh, I see.  Well, do you still have the lower bar?  If so, we can fix this easy.  If not, it's a small bit more difficult but still doable.

---

### Post by cardinals_fan on 2009-01-07
> **MaximoMilkman said:**
> somewhat but... i kinda got angry at my taskbar and ended up deleting the whole thing since for some reason a google searchbox look alike on my taskbar refused to go away so i was forced to delete my taskbar.. i heard some guys talking about some gnome code that can restore this do you know what it is??
If you still have the lower panel, right click it, navigate to something settings, and hit the plus button to create a new panel.

---

### Post by hyper_ch on 2009-01-07
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

