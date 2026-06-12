---
title: "Desktop black; icons there but invisible"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by OllieGab on 2009-11-01
After some sound problems when upgrading from 9.04 to 9.10 I have now got the sound back.
However, my desktop is now black, no icons showing, no background image visible. (Whether this and the previous problems are related, well who knows...)
I know the icons are there because I can click roughly where I know they should be and be able to launch an application or, for instance, check the icon's properties. It's just not visible!

Anyone had a similar problem?

Cheers Ollie

---

### Post by LewRockwell on 2009-11-01
turn off compiz

if, as you describe, you can click-through your black screen to do it...our screen magically re-appeared as soon as we selected "None" at the Visual Effects area

(note to the buntu-crew...compiz should be OFF by default...argh)

[http://ubuntuforums.org/showthread.php?t=1308317](http://ubuntuforums.org/showthread.php?t=1308317)


it should also be noted that previous versions of ubuntu suffered from the compiz blues as well

search=compiz problems

as always, your mileage may vary, buyer beware, and buyer be aware

.

---

### Post by Mr_JMM on 2009-11-01
Hi,

Thanks LewRockwell, this worked for me.

To clarify:
System -> Preferences -> Appearance -> Visual Effects -> Normal

I can only guess that some of my hardware is not supported in 9.10.

In 9.04 I had Compiz enabled with all the bells and whistles with no problem.

Hopefully a fix soon or might have to upgrade Videocard.

Also, whilst looking for the solution lot's of people where talking about Nautilus. Although none of the solutions worked for me I do have an error if I run Nautilus from terminal:
```
(nautilus:2087): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
```
Would be curious to know if anyone else has this issue.

---

### Post by LewRockwell on 2009-11-01
here at the tech bench we note that folks just want their computers to WORK

if they want bells and whistles they can go to Disney World

.

---

### Post by Logan 1229 on 2009-11-01
> **OllieGab said:**
>  desktop is now black, no icons showing, no background image visible.

Cheers Ollie

Had same problem.  Solved mine by going into System->Preferences->Display & changing the resolution (lowered it).  For some reason the higher 'default' resolution was giving me a black desktop.  Would have had to lower it anyway as this desktop is connected to a 42" LCD TV & I want to be able to read the font from across the room.

Cheers

---

### Post by OllieGab on 2009-11-01
> **LewRockwell said:**
> turn off compiz

if, as you describe, you can click-through your black screen to do it...our screen magically re-appeared as soon as we selected "None" at the Visual Effects area

(note to the buntu-crew...compiz should be OFF by default...argh)

[http://ubuntuforums.org/showthread.php?t=1308317](http://ubuntuforums.org/showthread.php?t=1308317)

.

Great! That sorted it! And the sluggishness disappeared as well!
I did like some of the compiz stuff but, as someone said, the important thing is that the machine works!

---

### Post by Mr_JMM on 2009-11-01
> **LewRockwell said:**
> here at the tech bench we note that folks just want their computers to WORK
Yes, that was the problem, it DIDN'T WORK.

> **LewRockwell said:**
> if they want bells and whistles they can go to Disney World.
I don't think it was asking too much for something that used to work perfectly in 9.04 (even if it is "bells and whistles") to work in 9.10 (more so when it all worked ok with KDE desktop that I installed on top of gnome).

I don't mind little things like this failing, part and parcel of running Linux I suppose.

I'm not sure how to take your responses above but I didn't think they were helpful. Such a shame you undone my gratitude for your help.

Something else I'm getting used to.

---

### Post by LewRockwell on 2009-11-01
> **Mr_JMM said:**
> I'm not sure how to take your responses

We're not sure exactly WHY you somehow thought our posts were directed towards YOU?

We thought this thread was originated by OllieGab?

Perhaps we are mistaken and in error...

Nevertheless, commentary and advice is freely given here...your refund is in the mail...

no offense and none taken, us hippopotamuses have thick skin...

[http://en.wikipedia.org/wiki/Hippopotamus](http://en.wikipedia.org/wiki/Hippopotamus)

.

---

### Post by schtum on 2009-11-02
> **LewRockwell said:**
> here at the tech bench we note that folks just want their computers to WORK

if they want bells and whistles they can go to Disney World

.

This attitude is exactly why Linux will never be a mainstream OS. I personally don't mind that I had to fiddle with my network settings and disable visual effects in order to get 9.10 working as well as 9.4, but why would I ever subject my mother to such nonsense? I wouldn't even recommend Ubuntu to my more tech savvy friends, other than to say that the price can't be beat. If you want a computer that "just works," get a Mac. Ubuntu is a hobby, it demands time and patience.

---

