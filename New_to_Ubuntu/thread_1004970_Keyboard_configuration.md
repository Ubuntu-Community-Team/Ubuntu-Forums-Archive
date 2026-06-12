---
title: "Keyboard configuration"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by nu2this2 on 2008-12-07
Hello all,

I've been using Hardy Heron now for a little while on a dual boot system (Ubuntu/WinXP). So far I really like Ubuntu but have noticed while using it,a few things don't seem to work so well in Ubuntu as Winxp.

One bit of hardware in this category is my keyboard. The basic functions work fine however my volume +/- control keys don't work properly. While pressing the keys, the volume level slider (on the screen) indicates an increase or decrease, however there is no corresponding change in the actual speaker volume. Is there any way to configure my keyboard?

Also having Printer problems ie, I don't have the same options I have in WinXP.

Any thoughts?------------Thank you.

---

### Post by ugm6hr on 2008-12-07
Best 2 have 2 separate threads: 1 per issue.  But anyway....

1. Your keyboard issue is nothing to do with your keyboard.  The keyboard works fine in Ubuntu, since Gnome recognises the volume function.  Have you found that using the Gnome volume slider (near top right corner on panel) actually changes your speaker volume?  If so - then Im confused...  If not, then it is likely that Gnome is controlling a different volume than your speakers.  You will see that there are a number of volume controls available, dependent on your sound card.  For example, my laptop has front, surround and centre volumes, in addition to a main (overall) control.  Just try them out, til you find the one that works.  You can then configure Gnome to control the correct volume.  To see the list off all volume controls, just type *alsamixer* in the Terminal.

2. You will need to specify a lot more detail re: your printer problems.  It is likely to be a driver issue.  HP and Samsung are 2 of the few printer manufacturers that support Linus fully with drivers; everything else is basically done by the Linux community.  hence the fewer features supported.

---

### Post by nu2this2 on 2008-12-07
Thanks ugm6hr,

I tried the slider you mentioned and it has no effect on the speaker volume whatsoever. Thank you for this information. I will try the terminal commands to see the various controls.

---

### Post by nu2this2 on 2008-12-08
I was able to find the volume controls in the terminal but can't figure out how to adjust them. When I click on the various controls, nothing happens. I'm trying to post a screen shot of what I'm looking at.

Maybe this will help.

file:///home/ken/Desktop/Screenshot-ken@ken-desktop:%20~.png

---

### Post by nu2this2 on 2008-12-08
Ooops, Sorry, that didn't work.----------Can't seem to post the screen shot from my desk top.

/home/ken/Desktop/Screenshot-ken@ken-desktop: ~.png

---

### Post by nu2this2 on 2008-12-08
Finally got it----------------------I hope!!

Can't figure how to make adjustments. Can anyone help?

Thank you.


[ATTACH]95734[/ATTACH]

---

### Post by ugm6hr on 2008-12-09
Arrow keys for left / right and up/down.
M key to mut/unmute.
Rab to switch to playback / recording / All.

---

### Post by nu2this2 on 2008-12-09
[QUOTE=ugm6hr;6327680]Best 2 have 2 separate threads: 1 per issue.  But anyway....

1. Your keyboard issue is nothing to do with your keyboard.  The keyboard works fine in Ubuntu, since Gnome recognises the volume function.  Have you found that using the Gnome volume slider (near top right corner on panel) actually changes your speaker volume?  If so - then Im confused...  If not, then it is likely that Gnome is controlling a different volume than your speakers.  You will see that there are a number of volume controls available, dependent on your sound card.  For example, my laptop has front, surround and centre volumes, in addition to a main (overall) control.  Just try them out, til you find the one that works.  You can then configure Gnome to control the correct volume.  To see the list off all volume controls, just type *alsamixer* in the Terminal.

Thank you,
I was able to adjust the various controls however nothing made a change in my speakers volume. The volume slider indicates increase and decrease on my monitor but with no variance in sound. I am using a desktop connected to external speakers through a HP keyboard.

I found the Gnome volume controls and there are many options to choose from. The option for "External speakers" does not exist however. What I am attempting to do is to control the volume coming out of the speakers via the media control keys that are available on my keyboard. These work fine in WinXP but not in Ubuntu. I'm really confused as to why this doesn't work. :confused::confused:

---

### Post by ugm6hr on 2008-12-10
Do you get sound at all from your speakers?

If yes - check each volume control in alsamixer one at a time; one of them must control the speaker volume (make sure you check the headphone one too - they may not be correctly labelled).

I understand what you are trying to do, but to solve that problem, we need to find out which alsamixer control relates to your speakers.

---

### Post by xjcannonx on 2008-12-10
if you right click on the speaker icon on your gnome panel you can go into preferences.
Have you tried this, there are many different options to choose from, for me its realtekALC861-VD-OSS Mixer

---

### Post by nu2this2 on 2008-12-10
Thanks to you both. Sorry for the long delay--------I'm in the states.


ugm6hr

Yes, I can adjust the speaker volume by up/down arrow in either the Headphone or PCM controls. I must have alsamixer visible on my monitor and one of the two controls highlighted.

xjcannonx

I have tried this method as well. I don't really understand what you mean when you refer to "realtekALC861-VD-OSS Mixer"

--------------------------------------------------------------------------------

---

