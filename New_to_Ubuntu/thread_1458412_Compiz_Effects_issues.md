---
title: "Compiz Effects issues"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-20
I have my graphics ramped up through SYSTEM>PREFERENCES>APPEARANCE and from there I've selected the Visual Effects tab and selected extra.

This is cool because now my windows behave like rubber. So I go into Compiz thinking it would be cool to use the Virtual Desktops in the 3D cube effect. Now I can't use my Virtual Desktops **at all**. When I tried to turn it on it brought up two windows that asked me how I wanted some settings... I didn't really understand them and the last one said that it was going to lock down my desktop.

CTRL+ALT+LEFT/RIGHT doesn't work and neither does clicking on the Virtual Desktop on my panels/bottom taskbar. I think I've finally gotten Virtualbox to work and I think it would be interesting to switch back and forth from windows on one virtual desktop to Ubuntu on the other. I just can't even work with my Virtual Desktops, period.

How do I get these virtual desktops to STOP being locked and how would I go about getting the 3D desktop to work because it's more than just clicking that little check mark.

I'd like to know how to make it look like my windows are being sucked into the taskbar like a genie or like their lit on fire too -- but that comes as something in the back seat of my mind to getting my virtual desktops to actually work.

---

### Post by Water_Spirit on 2010-04-20
Have a look at this under configuration

[http://wiki.compiz.org/Plugins/Cube#Rotating_the_Cube](http://wiki.compiz.org/Plugins/Cube#Rotating_the_Cube)

---

### Post by orphanlast on 2010-04-20
The hell... I didn't do anything yet and the Virtual desktops are now working. I was just playing with my rubber windows and POW onto the next screen.

Ubuntu is really weird. I'll read that link now.

---

### Post by orphanlast on 2010-04-20
Great! It locked up again!

I think that Wiki link did a good job explaining various things about the Cube and what you can do to it with various plugins, but it's just not working at all... 

Maybe I need a specific plugin. It says I need "Rotate Cube" plugin but it's not at all in synaptic.

---

### Post by anewguy on 2010-04-20
Okay, please forgive some obvious questions:

- you do have like 4 or more virtual desktops enabled?

- have you installed the compiz desktop manager from synaptic package manager?  It gives you a lot of control, and you do need to enable the cube there.

Best of luck!

Dave ;)

EDIT:  The package name is compizconfig-settings-manager in Synaptic package manager.

---

### Post by orphanlast on 2010-04-20
> **anewguy said:**
> Okay, please forgive some obvious questions: 

Don't apologise, you're volunteering to help me. The least I can do is answer some questions.

>  - you do have like 4 or more virtual desktops enabled? 

I enabled 6 just because I wanted to use all 6 sides of the cube. Any more seems insane to me and I'm somewhat curious how it would work out. But in a word, yes.

>  - have you installed the compiz desktop manager from synaptic package manager?  It gives you a lot of control, and you do need to enable the cube there. 

Yes it is.

---

### Post by David Batty on 2010-04-20
Enabling six sides will give you a six sided cube (whatever that is called) plus top and bottom. I don't think it is possible to use the top and bottom of the cube other than to paste walpapers on.

---

### Post by anewguy on 2010-04-20
> **orphanlast said:**
> Don't apologise, you're volunteering to help me. The least I can do is answer some questions.

....

Yes it is.

I was being a little stupid there - of course compiz desktop manager is installed - what I really meant to refer to was the compizconfig-settings-manager as mentioned in my edit.  Sorry.

Also, I think you got the error about download the cube plugin for a very simple reason - in compizconfig-settings-manager, if you check "rotate cube" but don't have the "desktop cube" checked, it will give you that error.  Usually after acknowledging it the settings manager goes ahead and enables the cube for you.  I'm assuming if you were using something other than the compizconfig settings manager it probably gets the same hick-up (I know it's trying to say "you want me to enable cube rotation, but you haven't told me to use the cube", but you'd think a slightly less cryptic message might be in order).

Don't know if that will help you at all or not.

dave ;)

As far as having it work one time, then not work the next, I'm not sure.

For me, to use the cube, I just find a place on my desktop without a window in it, hold down the center/scroll button on my mouse and just start moving up/down/left/right.  I've never checked to see what my center mouse button is set for, but if you need to know I can check.

---

### Post by orphanlast on 2010-04-20
AHA! I'm getting a little closter: [http://www.youtube.com/watch?v=6IU3f66DaSo](http://www.youtube.com/watch?v=6IU3f66DaSo)

I've been spending my time exclusively in "Effects" when I should have been check marking all stuff in "Desktop".... Still researching. 

This person in that youtube video their desktop acting really freakin' cool.

---

### Post by orphanlast on 2010-04-20
Yup, that did it!

SWEET!

You guys are AWESOME!

That video will show you how to make any effect that you'd like.

I do have some questions for anyone that might have the answer, are there compiz mods that have even more animations?

---

### Post by Water_Spirit on 2010-04-20
Have you installed simple-ccsm, compiz-fusion-plugins-main and compiz-fusion-plugins-extra. simple-ccsm gives some more options.

---

