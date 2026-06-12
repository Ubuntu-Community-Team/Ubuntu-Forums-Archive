---
title: "First mistake I have deleted the toolbar and I need to restore it"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by verachion on 2010-02-04
Hmm I have deleted the toolbar because I have installed a docking bar, little did I know it would get rid of the most valuable tabs. How can I restore it so I can get to adminisration, preference, applications e.t.c.

---

### Post by howefield on 2010-02-04
Do you still have the top bar ?

Right click and select New Panel.

You probably want to right click the new panel, and select add to panel, then add, Deleted Items, Show Desktop, Window List and Workpace Switcher. You may then right click them and "move" to your desired position.

Or for the top bar, you'd want, Menu Bar, & Notification Area, INdicator Applet Session, Indicator Applet.

---

### Post by BugBuster on 2010-02-04
Run this command in a terminal.

rm -r ~/.gconf/apps/panel

and then logout and login again..

You should get the default ubuntu panels.

---

### Post by verachion on 2010-02-04
THankyou so much everyone I got to the new panel and add but I didn't know what all the applications were for. This site is amazing, your all so helpful, I don't think I have experienced a forum like this and I am a member on quite a few. 

Now if only i can find the application where the window explodes when you close it, then that me done for the day ;P

---

### Post by thatguruguy on 2010-02-04
install compizconfig-settings-manager for the "exploding windows" thing.

---

### Post by verachion on 2010-02-04
> **thatguruguy said:**
> install compizconfig-settings-manager for the "exploding windows" thing.


Hi thanks for replying, I have looked on the compizconfig-setting-manager and I can't see anyt reference of it, I am using 9.10 if that helps, any advice?

---

### Post by howefield on 2010-02-04
Try going into CompizConfig Settings Manager and make sure you have check against "Animations" & "Animations Add=-On"

Then click on Animations and select the Close animation tab.

Highlight the top line in the Animation selection box and press the edit button. Choose Explode from the "Close Effect" drop down box. 

Then close your way back out.

Does that do it ?

---

### Post by verachion on 2010-02-04
> **howefield said:**
> Try going into CompizConfig Settings Manager and make sure you have check against "Animations" & "Animations Add=-On"

Then click on Animations and select the Close animation tab.

Highlight the top line in the Animation selection box and press the edit button. Choose Explode from the "Close Effect" drop down box. 

Then close your way back out.

Does that do it ?

Thanks for your help I have eventually found it, jeesh this makes you think. I have selected it, and the arrow is pointing down, but when I close a window nothing happens? do I have to save it or reboot the system? any help you can spare a tired noobie would be great.

---

### Post by howefield on 2010-02-04
Have you been able to get this dialogue box ?

---

### Post by verachion on 2010-02-04
its all gone wrong now, I went in to animation and added the explosion and copied the other effects but now I cant access anything it looks like I cocked it up by trying to figure it out. Now when I hover over application, places or system it just freezes and then explodes ;)

---

### Post by howefield on 2010-02-04
Can you open a terminal and type 

```
metacity --replace
```

This will stop compiz and hopefully allow you to reset compiz back to defaults. If you can, in compizconfig settings manager click on preferences and in the Profile & Backend tab, press the Reset to Defaults button.

---

### Post by verachion on 2010-02-04
> **howefield said:**
> Can you open a terminal and type 

```
metacity --replace
```This will stop compiz and hopefully allow you to reset compiz back to defaults. If you can, in compizconfig settings manager click on preferences and in the Profile & Backend tab, press the Reset to Defaults button.

You are a genius, I managed to reboot in to recovery and then boot back in and change the defaults in the end, however, all these tips and hints I am going to write down and keep in a book just in case. 

Now its back to the explosion: 

Right I have added the explosion tab in animations but I have to put something a window match field which I suppose is the command you give it so it knows to kick in. I have a strange feeling I am doing this all wrong, surely there must be a guide for newbies in regards to compiz setting manager?

---

### Post by verachion on 2010-02-04
> **howefield said:**
> Have you been able to get this dialogue box ?

Howefield here is a snapshot of what I have where do I go from here ?

---

### Post by howefield on 2010-02-04
> **verachion said:**
> Howefield here is a snapshot of what I have where do I go from here ?

Straight back out of there :)

It is the Animations options you want to be in, not the Animation Add-ons.

I'll screen shot in a minute.

Ok, this is the window you want, the Animations options.

You'll see where I have highlighted the top line in the Animation Selection box ?

With that line highlighted, press the Edit button, and choose your effect from the drop down field, in this case explosion.

---

### Post by verachion on 2010-02-04
> **howefield said:**
> Straight back out of there :)

It is the Animations options you want to be in, not the Animation Add-ons.



First off I apologise I should have read what you wrote carefully, I appreciate your time and effort with me. I see now, I have got the plane effect working but not the explosion it just sort of flashes and thats about it.
 
Do you know how I would set up a command for the window to explode when you minimise or close it? I saw on youtube somebody doing it and it looked great the window literally shattered all over the desktop.

---

### Post by howefield on 2010-02-04
No need for apologies. Once you've got it, it'll be sweet.

Just to be clear, you are now able to get the explosion working, the problem is that it doesn't work well ?

If that is the case, perhaps you should put the settings that you changed in the Animations Add-On options screen back to where they were.

I can screenshot you the numbers if needed.

---

### Post by verachion on 2010-02-04
> **howefield said:**
> No need for apologies. Once you've got it, it'll be sweet.

Just to be clear, you are now able to get the explosion working, the problem is that it doesn't work well ?

If that is the case, perhaps you should put the settings that you changed in the Animations Add-On options screen back to where they were.

I can screenshot you the numbers if needed.

Yes please that would be great, also whats the super button? I am just looking in to zooming in and out and its all super buttons? I know theres all these questions but I am keen to learn.

---

### Post by PhilGil on 2010-02-04
The Super button is the Windows logo key on most keyboards.

For example, to zoom in hold down the Windows key and turn the scroll wheel on your mouse.

---

### Post by howefield on 2010-02-04
> **verachion said:**
> Yes please that would be great, also whats the super button? I am just looking in to zooming in and out and its all super buttons? I know theres all these questions but I am keen to learn.

Super key is the key near the bottom left corner of the keyboard with the Windows logo on it.

Explosion defaults should be set as per the attached screen shot. Put yours back to match and try enabling it again.

---

### Post by verachion on 2010-02-07
> **howefield said:**
> Super key is the key near the bottom left corner of the keyboard with the Windows logo on it.

Explosion defaults should be set as per the attached screen shot. Put yours back to match and try enabling it again.

Thanks to your help howefield m desktop is smoking, all the effects are working and it looks great, thanks for taking time out in teaching me.

---

### Post by howefield on 2010-02-08
You're welcome, if you have any more questions, just ask, someone around here is likely to have the answer.

---

