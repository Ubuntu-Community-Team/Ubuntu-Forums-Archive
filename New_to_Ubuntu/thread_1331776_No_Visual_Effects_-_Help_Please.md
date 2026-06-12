---
title: "No Visual Effects - Help Please"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by luckylucky on 2009-11-19
I have (finally) upgraded to 9.10, and have a little issue that I need some help with.  In previous releases I had dual monitors and visual effects run good.  Now I can't get any desktop effects.

When I go to system > preferences > appearance > visual effects 
I can't get any of the cool visual effects.  Selecting "Normal" or "Extra" gets me the following message:

"Desktop effects could not be enabled"

I have an intel video in my laptop.

Any help please?

---

### Post by NoaHall on 2009-11-19
Try this

System -> Admin -> Hardware Drivers

See if your driver is installed. If not, install it.

---

### Post by lgiordano on 2009-11-19
I had a similar problem with my intel laptop with a karmic trunk build. Ended up rolling back to hardy and then did a clean install of karmic after the official release. Works perfectly now.

Did you upgrade to karmic? Aparently you don't need an xorg.conf file anymore. Try deleting/moving/renaming your current xorg.conf (whichever you prefer with a backup of course) and reseting xorg with:
```

sudo dpkg-reconfigure xserver-xorg
```

I'm thinking it could be something from your xorg.conf file that doesn't play well with karmic.

---

