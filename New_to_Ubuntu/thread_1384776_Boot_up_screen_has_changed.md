---
title: "Boot up screen has changed"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-18
Another development this morning..when I logged on, the screen which gives you a choice of what OS to use I noticed there are 2 Ubuntu versions listed ( Linux 2.6.31-17-generic and Linux 2.6.31-14) and there is some sort of error message which flashes up but it's too fast to read. All I can catch is something is depreciated....yesterday I booted up and got an error message that some app had a problem and did I want to delete it which I did. All I could catch was this _TS client Applet and OAFIID:Gnome.
SO I have the choice of the two Linux os and my windows. That wasn't there before today. I have GBU GRUB version 1.97 beta4. My Ubuntu seems to be a mess :(

---

### Post by llamabr on 2010-01-18
> **ThePinkWitch said:**
> My Ubuntu seems to be a mess :(

Is it still booting correctly?  If so, it's not a mess at all.  I wouldn't worry about that deprecated error.  If everything is working.

The extra line is because you recently did an update, and it updated your kernel image.  now you can use the old one (don't) or the new one (automatically, probably.)

---

### Post by ThePinkWitch on 2010-01-19
> **llamabr said:**
> Is it still booting correctly?  If so, it's not a mess at all.  I wouldn't worry about that deprecated error.  If everything is working.

The extra line is because you recently did an update, and it updated your kernel image.  now you can use the old one (don't) or the new one (automatically, probably.)

oh ok. Thankyou :) which one should I use..the later one -17?

---

### Post by Paqman on 2010-01-19
> **ThePinkWitch said:**
> oh ok. Thankyou :) which one should I use..the later one -17?

Yep. If you remove the older one using Synaptic, it'll be removed from the Grub menu as well.

---

### Post by llamabr on 2010-01-19
You can leave the old one there, though, too.  You might need it, in a pinch.

Grub will automatically put the newest one at the top for you.  Just let it work, or pick the newest one, when prompted.

---

### Post by ThePinkWitch on 2010-01-19
Thanks guys :)

---

