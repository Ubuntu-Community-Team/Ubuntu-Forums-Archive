---
title: "Lost Command bar in 9.04"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Erik Ramsey on 2009-08-30
After just getting Ubuntu installed on a Dell machine, I was fooling around using a second monitor attached to my laptop. I went into some setting and attempted to manipulate the second screen in a way to make it behave differently, such as being an extended desktop. What ever I did, when I rebooted, the title or command bars at the top and bottom of the page are gone. I have a feeling they are outside the current screen (panel?) that I see. The desktop image I see is an apparent closeup of the default screen I was used to so I am lead to believe this to be true.  So, how to reset default settings? Help.
Erik

---

### Post by NoaHall on 2009-08-30
Do you have compiz enabled? If so, use super + middle scroll on mouse to scroll in and out. And what do you mean by command bar? The toolbars?

Also - if your second screen isn't connected anymore , do "sudo dpkg-reconfigure xserver-xorg" and if that fails "sudo dpkg-reconfigure -phigh xserver-xorg"

---

