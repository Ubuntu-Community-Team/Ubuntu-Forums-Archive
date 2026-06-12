---
title: "Clock Weather &amp; Temperature Display"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-11-01
Is anyone besides me having the problem that in Ubuntu 9.10 I can't get the Weather & Temperature to display next to the clock?

---

### Post by Teber on 2009-11-01
you could be more specific about precisely how you tried to get weather display?

---

### Post by Incendia on 2009-11-01
What happens when you try to get it to display?

---

### Post by scout4536 on 2009-11-01
I have had this problem with 9.04 as well.  One day it all worked fine, had the weather and temp icon on panel.  Then one day it all disappeared, even on 9.10.  I don't know if an update caused this, but I also know about the problem.  When I try to activate these using the preferences the panel blinks once and the icons do not show up, is that happening to yours?   Hopefully I can track down a fix for this and post it.

Forgot to mention I am also using UNR 9.10.  Still looking for fix, though.

Fixed it----see post #9

---

### Post by Incendia on 2009-11-01
> **scout4536 said:**
> I have had this problem with 9.04 as well.  One day it all worked fine, had the weather and temp icon on panel.  Then one day it all disappeared, even on 9.10.  I don't know if an update caused this, but I also know about the problem.  Hopefully I can track down a fix for this and post it.

I had something similar in 7.04 where the trash disappeared in the bottom right corner. It was fixed in 7.10, though. :]

---

### Post by el.puerco on 2009-11-01
> **hifly1231 said:**
> Is anyone besides me having the problem that in Ubuntu 9.10 I can't get the Weather & Temperature to display next to the clock?

I'm using UNR 9.10 and I can't seem to get weather and temperature to show up. I've added my location under preferences and made sure to have the display options set, but nothing.

---

### Post by hifly1231 on 2009-11-01
> **scout4536 said:**
> I have had this problem with 9.04 as well.  One day it all worked fine, had the weather and temp icon on panel.  Then one day it all disappeared, even on 9.10.  I don't know if an update caused this, but I also know about the problem.  When I try to activate these using the preferences the panel blinks once and the icons do not show up, is that happening to yours?   Hopefully I can track down a fix for this and post it.

This is exactly what's happening with me.  Mine worked in 8.10 & 9.04, but since I've upgraded to 9.10 it won't show.  Just like you said...when I right click on the clock, select preferences, and check weather & temperature, the clock will blink, and I'll see the very slightest expansion to the left of the clock where the weather & temperature would normally show, but it doesn't.  Right now I've added Weather Report to the panel, but I would rather have it by the clock where it used to be.  It looks much cleaner.

Keep me posted if you find the fix for this, OK?  Thanks!!!

---

### Post by senorgomez on 2009-11-02
same problem here with fresh ubuntu 9.10 upgrade

---

### Post by scout4536 on 2009-11-02
HOLY CRAP!!! Found the fix LOL  It is so silly too, I was playing around and got it working.  Left click on clock panel, expand Locations and then click "set" at the bottom, then the icons will show up  LOL  silly stuff.  Make sure you have Show Weather and Show Temp activated in preferences.

Yay!!!!!

...now why do I feel so dumb.....duh   lol

--oh, and the "set" button icon turns into a 'Home" icon

---

### Post by hifly1231 on 2009-11-02
> **scout4536 said:**
> HOLY CRAP!!! Found the fix LOL  It is so silly too, I was playing around and got it working.  Left click on clock panel, expand Locations and then click "set" at the bottom, then the icons will show up  LOL  silly stuff.  Make sure you have Show Weather and Show Temp activated in preferences.

Yay!!!!!

...now why do I feel so dumb.....duh   lol

--oh, and the "set" button icon turns into a 'Home" icon

THANKS!!!  That's the answer!!!

---

### Post by senorgomez on 2009-11-02
> **scout4536 said:**
> HOLY CRAP!!! Found the fix LOL  It is so silly too, I was playing around and got it working.  Left click on clock panel, expand Locations and then click "set" at the bottom, then the icons will show up  LOL  silly stuff.  Make sure you have Show Weather and Show Temp activated in preferences.

Yay!!!!!

...now why do I feel so dumb.....duh   lol

--oh, and the "set" button icon turns into a 'Home" icon

I was just about to post that!
I feel a bit daft now too ><
Even reinstalled... it was then that I noticed it lol :D

But yea, consider this thread SOLVED.

---

### Post by jejeman on 2009-12-21
It worked for me too, but I needed to reset my location.

I've already set my location, but for some reason it didn't displayed temperature value beside the clock. The 'set' button was already activated (it was a house icon). So, I opened preferences, removed the location, and added it again. Checked the show temp option, closed the preferences, clicked the set button.

Thanks guys for clearing this out.

---

### Post by dingletec on 2009-12-22
Regarding clicking "Set" after expanding locations, "Set" was not showing up for me at first (9.10).  But once I clicked down at the bottom where it shows my location, the button magically appeared. 

So happy to have this resolved!

---

### Post by risby on 2010-01-04
Unfortunately, this has made no difference to me. I have Ubuntu 9.10 (karmic koala) and Clock 2.28.0.

I can click on and off the date and seconds check boxes with immediate effect but neither the weather nor the temperature boxes are effective. I have my location with the "home" icon set.

---

### Post by mookiemeister on 2010-03-05
Thanks.  I was able to fix mine too.

I was trying to figure out why my ubuntu laptop doesn't display the weather/temperature while it displayed fine on my desktop.  Like the previous poster said, you need to set the 'home' location. I set it on my desktop but forgot to set it on my laptop.

---

### Post by Prime3869 on 2010-04-30
Until I found this thread, I thought that I actually had a problem with an otherwise flawless install of Lucid.

Thank you!

---

### Post by kid1000002000 on 2010-05-14
perfect.  had to delete and add locations, then set worked perfectly.

---

### Post by yishaishimoni on 2010-06-02
Sorry, doesn't work here.
I have Ubuntu 8.04 and after almost two years it suddenly stopped showing temp and weather. Changing prefs adds and removes blank space to the left of the clock. Tried removing all locations and re-adding them, removing and adding other ones, pressed the set button, changed global appearance preferences.
Nothing worked.
Any advice?

---

