---
title: "Internet time"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by twanchic on 2010-01-12
I'm trying to change the time format in the clock app. The only options I have is 12 hour and 24 hour. I want to display my time in internet time, also known as Swatch Time or Decimal Time. Anyone know how I can display time as such?

---

### Post by freesitebuilder on 2010-01-12
Synaptic has gkrellm listed for internet time - don't know if it's what you need!

---

### Post by twanchic on 2010-01-12
No that's a program for monitoring system processes I'm looking for something like clock or gworldclock. Something small that displays the current internet time.

---

### Post by J V on 2010-01-12
run: gconf-editor then navigate like so:

apps > panel > applets > *findoutwhichone* > prefs > format : internet

enjoy :)

---

### Post by twanchic on 2010-01-12
Exactly what I wanted! Thanks

---

### Post by J V on 2010-01-12
mark it solved ;)

(thread tools at the top)

---

### Post by jontta on 2011-01-05
er...

I was searching for the @time too, and the approach worked ( with minor changes in the menu path ). Thx U very much !

But... those two digits alone... it's so ugly... is there a way to add trailing zeros to the @time ( I mean, for the times between @0 and @999, so that they appear as @0000, @0999, etc ) ?

Happy New Year !

---

