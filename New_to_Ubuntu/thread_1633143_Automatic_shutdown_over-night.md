---
title: "Automatic shutdown over-night"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by 00arthuryu on 2010-11-28
Hi
My ubuntu seems to be shutting down automatically over long periods of time, i.e. overnight. (without anyone touching it) Is it possible to see the cause of the shutdown through any logs??

Thanks :popcorn:

---

### Post by admiralspark on 2010-11-28
Yeah, it's probably due to the default power settings which will shut down a non-active computer after, say, one hour. Go to Menu-->Preferences-->Power Management, then set it to whichever settings you'd like. Notice you may also need to change the screensaver properties as well....though doubtful.

---

### Post by 00arthuryu on 2010-11-29
That was one of the first things I checked, although the options you mentioned do not exist, the closest option would be putting the computer to sleep, in which case it was set to "never".
Screensaver is also set to "off"

Thanks for the input though :)

---

### Post by jhomie1 on 2010-12-10
Hey i think this is what you might want:

in the terminal type: "sudo shutdown -h m" substituting "m" with the number of minutes until shutdown for example: "sudo shutdown -h 35" this will turn off the computer in 35 mins.

and if you want a specific time then you have to do it in the 24hr time frame, for example: "sudo shutdown -h 20:00" this will offcourse turn your computer off at 8:00pm.

hope this helped.

---

