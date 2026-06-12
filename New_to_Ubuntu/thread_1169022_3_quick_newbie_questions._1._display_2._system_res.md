---
title: "3 quick newbie questions. 1. display 2. system resource use 3 mouse"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by mrdzone on 2009-05-24
Thanks for being patient guys this is my first time using linux on a desktop, I have some limited experience messing around on terminals on home projects. 

I just installed Ubunt hang of this. 

I do have a couple of questions

1. My display appears "fuzzy", not the actual display but the text mostly, it just doesn't seem as crisp as it did in windows. It becomes more apparent when I enlarge things in firefox. I have fairly bad eyesight (this isn't causing the fuzziness :) ) and so I tend to scale up what I'm reading using control + 
When doing this even the images appear pretty fuzzy which doesn't happen in windows. Not a huge deal on this note but if there is a way to make the text sharper I'd appreciate hearing about it. 

2. System resources, when I had about 15 tabs open in firefox my system is gettign sluggish to the point of not usable. Espcially when minimizing firefox and opening another application, when I did that the task manager showed both cpu's very high, one over 70% one over 40%. In windows I do have to restart firefox every day just to clear the memory leaks but it never gets as sluggish as it was on linux (by the way my computer isn't the fastest known to man but it's a 2ghz dual core with 3gb of ram)

3. mouse

Is there anyway to turn off the touchpad when I have an external mouse connected and automatically turn it on when it is disconnected? Also is there any way for me to custom set my extra buttons on my external mouse? The mouse control panel doesn't seem all that helpful in these regards. 

Thanks guys so much for helping me on my journey, I have tried google of course but my google-fu is tough when I don't know how to express what I'm looking for :) 

Cheers 

-Bob

---

### Post by red_Marvin on 2009-05-24
1) I would check the font settings, especially the antialias and hinting stuff. System->Settings->Appearance if my memory serves me right. I don't know why images should appear blurry though, unless it is raster images that you view at >100% size.

2) Well, FF is pretty much considered a memory hog, if you don't need some special plugin, you might want to try some other browser, opera has a linux version, and there are others like epiphany and swiftfox.

3) When I ran gnome I had the option to turn off track pad clicking, but that is all I know of, somebody else might prove me wrong though. When it comes to customise the buttons it depends. If you want to remap them (like switching left and middle button) I think that is possible, but probably requires editing of /etc/X11/xorg.conf (boring), but more than that I do not know.

---

### Post by mrdzone on 2009-05-25
Thanks for the tips Marvin. 

1. I payed around with the fonts and ended up installing the ms fonts along with some xml files that modified the display and everything looks great now.

2. I installed opera but even though I have installed the flash plugin it refuses to display flash files... I've tried everything from sudo apt-get to using the synaptic package manager to installing from the adobe website but I can't get them to display in opera (and yet they do in firefox) so i'm downloading epihany now. 

3. I was able to turn off my touchpad but I'm wondering what happens when I dont' have my usb mouse. I'd like ubuntu to automatically turn on the touchpad for obvious reasons. Also it'd be nice to be able to assign the buttons to be useful as opposed to shiny :) 

Thanks again for your input. 

-Bob

---

