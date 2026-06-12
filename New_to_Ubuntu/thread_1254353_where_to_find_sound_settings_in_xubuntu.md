---
title: "where to find sound settings in xubuntu?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Harlequin. on 2009-08-31
Yeah I´m having alot of problems with my sound and I can´t actually seem to find any programs in which I can edit the sound preferences.

Looking for what´s in the picture below.




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=126852&d=1251663573[/IMG]

---

### Post by Harlequin. on 2009-08-31
Can no one freaking help with this?

---

### Post by braete on 2009-08-31
you cant find sound preferences ?

it should be under system/preferences

---

### Post by Harlequin. on 2009-08-31
> **braete said:**
> you cant find sound preferences ?

it should be under system/preferences

There is no system/preferences...

Using Xubuntu 9.04.

---

### Post by Harlequin. on 2009-08-31
Omfg no one can help with this?

---

### Post by ftabor on 2009-08-31
In your Top Task Bar, on the left, do you not have an Ubuntu Icon, then Applications, Places, System?  If so, click System, then Preferences, then Sound.

---

### Post by Weidbrewer on 2009-08-31
There are a lot of threads on these forums, and sometimes it takes a little while for someone to get you an answer.  The usual party line is to wait 24 hours before self-bumping a thread.   Also, "OMFGs" and such might turn people off to giving you attention.


That having been said, as **Harlequin** posted above, it should be under system => preferences from the drop-down at the top of your screen.  (Your shot only really shows you FireFox window, so it's hard to show where it would be on your desktop layout.)  Also, one can usually double-click the speaker icon to get the menu that you have up.  


The big question is - What type of problems are you have, specifically.  It's hard to offer help with just a generic "a lot of problems."

---

### Post by Harlequin. on 2009-08-31
> **ftabor said:**
> In your Top Task Bar, on the left, do you not have an Ubuntu Icon, then Applications, Places, System?  If so, click System, then Preferences, then Sound.

Jesus christ, if it was there I wouldn´t have posted this bloody thread.

---

### Post by Harlequin. on 2009-08-31
> **Weidbrewer said:**
> There are a lot of threads on these forums, and sometimes it takes a little while for someone to get you an answer.  The usual party line is to wait 24 hours before self-bumping a thread.   Also, "OMFGs" and such might turn people off to giving you attention.


That having been said, as **Harlequin** posted above, it should be under system => preferences from the drop-down at the top of your screen.  (Your shot only really shows you FireFox window, so it's hard to show where it would be on your desktop layout.)  Also, one can usually double-click the speaker icon to get the menu that you have up.  


The big question is - What type of problems are you have, specifically.  It's hard to offer help with just a generic "a lot of problems."

The screenshot is what I´m looking for.. when I hit applications and go to system, there´s no sound options. I know that acting like a dickhead isn´t going to get me any help, but I´ve had no damn sound since I installed xubuntu and I´ve spent all week trying to get it working.

My problem is that my sound cards should be working, and they have all the right drivers, they have been unmuted etc and there´s still no sound. I´m so frustrated right now.

---

### Post by Harlequin. on 2009-08-31
Master is set to 100% on the speaker thing next time the time display.. I would really like some help......

---

### Post by roger_1960 on 2009-08-31
Hi

I think the reason that you have had a few answers which dont seem right is that the menus in Xubuntu are different to those in Ubuntu and the previous posters may not know this.  I have not used the latest Xubuntu so I'm not certain but:

try right clicking the speaker symbol - does it give a volume control option?

if not

open terminal (accessories>terminal I think) and type "alsamixer"

This should give you a graphic (just) mixer.  Make sure it is all on, particularly the PC speaker volume which is at the far right, reached by using the left/right arrows.

Hope this helps.

---

### Post by Harlequin. on 2009-08-31
> **roger_1960 said:**
> Hi

I think the reason that you have had a few answers which dont seem right is that the menus in Xubuntu are different to those in Ubuntu and the previous posters may not know this.  I have not used the latest Xubuntu so I'm not certain but:

try right clicking the speaker symbol - does it give a volume control option?

if not

open terminal (accessories>terminal I think) and type "alsamixer"

This should give you a graphic (just) mixer.  Make sure it is all on, particularly the PC speaker volume which is at the far right, reached by using the left/right arrows.

Hope this helps.

Yes I know I figured if I mark the thread as [Xubuntu] people would realise it´s xubuntu, but alas..

Anyway I fixed this problem.

---

### Post by angry_norwegian on 2010-05-04
> **Harlequin. said:**
> Yes I know I figured if I mark the thread as [Xubuntu] people would realise it´s xubuntu, but alas..

Anyway I fixed this problem.

How? I have the same problem. No sound, and no sound preferences.

---

### Post by Sir Jasper on 2010-05-05
Hi,

Try Multimedia > Volume Control and see if it´s Muted.

My regards

---

### Post by bdalzell on 2012-10-10
for Xubuntu 12.04 this is still, to me a mystery, except that one can use an item called Mixer that can be added to panel but does not appear anywhere else on my system. click on panel then choose:

panel>add new items and then choose Mixer which will bring up a control for pulseaudio. 

in addition unlike the other *buntus, the general set of system settings gadgets are found by going to:

applications menu> settings>settings manager

however there is no sound manager in that set of settings managers.

the bottom panel also has a small speaker icon which

---

