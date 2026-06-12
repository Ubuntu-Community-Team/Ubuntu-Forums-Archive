---
title: "Initialization order in /etc/network/interfaces"
date: 2005-04-19
forum: Networking &amp; Wireless
---

### Post by nautilus on 2005-04-19
Hmm, I have an odd situation.  I have a Tun/Tap interface which I would like to initialize via /etc/network/interfaces, naturally, after eth0 has come up (my primary interface).  I've tried simply putting them in order, and that doesn't work...  I've taken 'auto tun0' off, and appended 'up ifup henet' to the eth0 bit, and that does something unexpected; it hangs.

Well, the last option is having a shell script which brings up the Tun/Tap interface, and have that called on 'up' from the eth0 entry in my interfaces file, but... that seems like a poor solution to me.

Any ideas?

---

### Post by mendicant on 2005-04-19
Maybe try reversing things--use pre-up?

---

### Post by nautilus on 2005-04-20
Right, but calling ifup from either directive seems to lock up, making booting touch-and-go.

What I need is a way to make eth0 a prerequisite of tun0, the way one can make a module a prerequisite for an interface...

---

### Post by mendicant on 2005-04-20
Yeah--just an off chance on that one.  Calling a script, as you mention, will work.  It's too bad it won't just work off the interfaces file, though.

---

### Post by nautilus on 2005-04-20
s/too bad/brain damaged/

It's weird.  :(

Well, thanks for the hand anyway, I'll figure something out.

---

