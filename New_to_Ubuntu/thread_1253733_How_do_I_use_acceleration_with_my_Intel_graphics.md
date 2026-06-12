---
title: "How do I use acceleration with my Intel graphics?"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Stuart P. Bentley on 2009-08-30
I don't know if this is because I installed using Wubi or what, but for some reason X is using software rendering instead of my onboard Intel 945. How do I enable the use of the Intel driver?

Edit: This is on 9.04.

---

### Post by NoaHall on 2009-08-30
System -> Admin -> Hardware Drivers.
See if there's a driver there.

---

### Post by Stuart P. Bentley on 2009-08-30
Just my wireless card.

---

### Post by nhasian on 2009-08-30
you need to mention what version of ubuntu your using.

---

### Post by Stuart P. Bentley on 2009-08-30
Jaunty.

---

### Post by nolster12 on 2009-08-30
search the forums the intel cards do not work well with jaunty.  either go back to 8.04 or use the 9.10 alpha.  There are also guides that will tell you how to make jaunty work but it is a lot of tinkering around

---

### Post by nhasian on 2009-08-30
i've fixed this issue on several laptops with only copy & pasting this one line in the terminal:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

for more info see:

[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

btw, Karmic Koala alpha 5 comes out thursday.  its working great for me :)

---

