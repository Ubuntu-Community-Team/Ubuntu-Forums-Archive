---
title: "Command to find Debian version of xorg?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by kansasnoob on 2009-05-15
I know I can just look in synaptic and see that Jaunty is using xorg 1.7.4* but I'm wondering if there's a command I can run from terminal to determine the Debian version of xorg?

I know in development it was advertised as 1.6.

Just something I'd like to know, and at the moment I'm writing a review of a Hanns-G 22" Widescreen.

BTW it's working great so far in 9.04 and Mint Gloria RC1, not so good in win XP! Xorg automatically installed the proper 16:10 resolution ratios without even reconfiguring X!

I haven't tried 8.04.2 (Hard) yet.

---

### Post by lykwydchykyn on 2009-05-15
try:
```

aptitude show xserver-xorg

```

Actually it's a little confusing.  It's not 1.7.4, it's 1:7.4; xorg is actually at 7.4 (not sure what the 1 means), but to get the version of xserver:
```

aptitude show xserver-xorg-core

```
which is indeed version 1.6.

---

### Post by anewguy on 2009-05-15
Now I have a question on this - I ran both of the commands as I had never seen them before, so I was curious.  Why do both list a LOT of conflicts, saying other things are < 7?  Just from the outside looking in, it indicates to me that we only have a partially upgrade xserver.  Could this be responsible for some of the problems people have with drivers, etc?

Dav :)

---

### Post by lykwydchykyn on 2009-05-15
> **anewguy said:**
> Now I have a question on this - I ran both of the commands as I had never seen them before, so I was curious.  Why do both list a LOT of conflicts, saying other things are < 7?  Just from the outside looking in, it indicates to me that we only have a partially upgrade xserver.  Could this be responsible for some of the problems people have with drivers, etc?

Dav :)

The conflicts are there to prevent you from installing it with an incompatible version.  For example, if it lists a conflict with "sompackage (<6.2)" that means it won't install if you have a version of sompackage installed less than 6.2.  Those are not problems on the system, they are "safety checks" to make sure you're not running two incompatible packages on the same system.

---

### Post by kansasnoob on 2009-05-15
Errrrrm, maybe I'd be better off just saying what OS works well and what doesn't:confused:

Of course I'll include that I'm using the OpenChrome driver.

But, I was amazed at how easy this was to set up!

Even the full screen video is great in both VLC and Totem. Some Flash videos play very well in full screen, others a bit choppy, but that was the same on my old CRT!

I must also add that I'm visually impaired (actually legally blind), so if it ain't easy I'm lost!

---

### Post by anewguy on 2009-05-16
Thanks for the info - I learned something new again!

Thanks!
Dave :)

---

