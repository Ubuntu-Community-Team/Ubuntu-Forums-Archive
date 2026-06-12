---
title: "buttons disappeared"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by cjv8888 on 2008-12-06
After the recent updates,  the buttons - (minimise, maximise, close ) have all disappeared from both the Nautilus as well as Firefox.

How do I get them back?

I am running Ubuntu 7.10 on this computer

---

### Post by Joeb454 on 2008-12-06
What happens if you hit Alt+F2 and then type ```
metacity --replace
``` Do they come back?

---

### Post by cjv8888 on 2008-12-06
> **Joeb454 said:**
> What happens if you hit Alt+F2 and then type ```
metacity --replace
``` Do they come back?

nothing happened. still the same

---

### Post by snova on 2008-12-06
Run the same command in a terminal and check for output. There should at least be an error message...

---

### Post by cjv8888 on 2008-12-06
> **snova said:**
> Run the same command in a terminal and check for output. There should at least be an error message...

The screen blinked and the terminal came back with a non-responsive cursor on the next line.

---

### Post by michaeltobin on 2008-12-11
ive done the same thing with no close/maximise/minimise

help would be appreciated

---

### Post by Duck2006 on 2008-12-11
Are you running compiz?

---

### Post by michaeltobin on 2008-12-11
yep, tried reinstalling it and still the same

---

### Post by Duck2006 on 2008-12-11
> **michaeltobin said:**
> yep, tried reinstalling it and still the same

What happens when you turn it off?

---

### Post by LowSky on 2008-12-11
This sounds like the Nvidia/Compiz/FF3 issue with the 177 driver

Hit F11 twice and bar should come back in FF3 if not run the command below

run this from Alt+F2
 ```
metacity --replace
```
it will turn compiz off

---

### Post by michaeltobin on 2008-12-11
thanks for the suggestion but nothing happened.

as well as having no min/max/close buttons every window is automatically maximised and where the close 'x' was there is now a small blue circle (which i cant click on)

After a few hours of messing around, ive got them back thanks, not sure what exactly fixed it though (doh) so cant post to help anyone else with this problem, sorry

---

### Post by cjv8888 on 2008-12-13
My min/max/close buttons are still missing though.
Tried the above methods a few times but nothing happened.
Any other suggestions?
Thanks

---

### Post by cjv8888 on 2009-01-01
I still cannot get back the min/max/close buttons.
I am running Gutsy on a rather old machine with no special effects at all.  May be that is why turning off the Compiz did not help.

The title bar is still there , but in stead of the buttons on the right edge of the title bar there is a little drop button to the left of the title that will give the min/max/close options if I click on it.

Help please.

---

### Post by thekryan on 2009-01-04
I have the same problem with Firefox. I tried the methods you mentioned but it didnt helped. Firefox window seems to be maximized and no minimize buttons are visible. When I try to unmaximise it with hotkey alt+F5 nothing happens again. M

---

### Post by cjv8888 on 2009-01-06
I was unable to solve the above problem and then the system played up more suddenly with the loss of write permission to FAT32 on a USB harddrive as well as to a dual booting Fat32 internal hard drive.
So I deleted the 7.10 and did a new install of 8.04 on the drive. Now everything is working perfectly and also noticeably faster than the flawed Gutsy install before.
Did take most of the day to get things right but we Ubuntu users are suckers for that, usually? :)

---

