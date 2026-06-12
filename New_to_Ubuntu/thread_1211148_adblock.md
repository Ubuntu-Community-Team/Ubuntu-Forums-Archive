---
title: "adblock"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by DarinB on 2009-07-12
i use adblock with firefox 3.xx
i allowed an ad but now i don't know how to un allow it.
Now every time i go to cnn i get a pop up, very anoying how can i block everything again?????

---

### Post by LewRockwell on 2009-07-12
you can manage adblock plus filter items via the user interface

there is a slight learning curve to adblock but it's worth it to get rid of all those stinkin' ads!

.

---

### Post by DarinB on 2009-07-12
i realize this i am having difficulty figuring out how to reapply the original settings, any ideas?/????

---

### Post by drs305 on 2009-07-12
> **DarinB said:**
> i realize this i am having difficulty figuring out how to reapply the original settings, any ideas?/????

Tools, Addons, Adblock Plus, Preferences. Filters. From there, you can remove all custom filters, update, etc. Also check the "My Exceptions" list. From the Edit menu, you can use "Find" to locate a specific filter to update, remove, etc.

---

### Post by DarinB on 2009-07-12
i just tried adding easylist usa from the preferences subscriptions, it seems to have stopped the cnn pop ups. but i would like to know how to undo what i did by allowing the diverting of the window. unless it has nothing to do with adblock and is in firefox its self????

---

### Post by LewRockwell on 2009-07-12
> **DarinB said:**
> i realize this i am having difficulty figuring out how to reapply the original settings, any ideas?/????

ok, we'll do this in the most basic fashion for the benefit of all...

from your firefox "tools" drop-down menu you will select "add-ons" and then at the new window you will select "extensions" and then uninstall "adblock"

restart firefox...then

re-install adblock plus, subscribe to the filter of your choice(via the user interface) and that should get you back to what you started with as long as you did it that way previously

again...as simple as I could make it...to be of the most value to the most people...

.

---

### Post by LewRockwell on 2009-07-12
> **DarinB said:**
> i just tried adding easylist usa from the preferences subscriptions, it seems to have stopped the cnn pop ups. but i would like to know how to undo what i did by allowing the diverting of the window. unless it has nothing to do with adblock and is in firefox its self????

you can also block pop-ups via your firefox preferences(a little browsing through those should do the trick)

(and I believe you can create exceptions to the blocker as well...probably what happened in your case)

.

---

### Post by zerhacke on 2009-07-12
If you don't mind digging into the innards of Ubuntu, check out your hosts file.  There's several sample hosts files on the internet you can use to kill connections to tons of ad servers, and it lightens the load on Firefox.

---

### Post by DarinB on 2009-07-12
ok i have proven how much i have no clue what i am doing!!!!!!!
i found the tab in firefox preferences > content > exceptions > sure enough cnn was there, and others i didn't want. 
Sorry to waste everyones time, but i am slowly (very) slowly learning this stuff.

---

### Post by DarinB on 2009-07-12
After i posted my apology i saw all the other posts **thank you to all that responded**. Grateful to the ubuntu community!

---

### Post by LewRockwell on 2009-07-12
> **zerhacke said:**
> If you don't mind digging into the innards of Ubuntu, check out your hosts file.  There's several sample hosts files on the internet you can use to kill connections to tons of ad servers, and it lightens the load on Firefox.

over time these efforts will become more and more fruitless as the ad folks figure out ways around the blockers

definitely a constant battle...

(try running your browser set to no cookies, no pop-ups, no java, no javascript, install ghostery, install adblock plus, install noscript, and even firebug if you like...then the interwebs become a whole different jungle indeed)

.

---

