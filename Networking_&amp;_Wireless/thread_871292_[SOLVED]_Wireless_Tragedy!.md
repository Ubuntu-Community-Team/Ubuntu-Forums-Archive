---
title: "[SOLVED] Wireless Tragedy!"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by PhaeZee5 on 2008-07-26
I recently updated ubuntu and lost wireless card funtionality.
Strange thing is, even an external wireless device that I have used in the past doesn't show the multitude of wireless networks at home...the only difference is that then ubuntu show an empty wireless tab:confused::confused::confused:


I also lost sound!!

I am using a Toshiba M45-S269, with Intel PRO/Wireless 2200BG Wireless card.

---

### Post by PhaeZee5 on 2008-07-26
I Feel Your Pain.

---

### Post by caljohnsmith on 2008-07-26
That's an interesting way of replying to yourself. What chipset is your wireless card? How about posting the output of the following to get started:
```
sudo lshw -C network
ifconfig
iwconfig
```

---

### Post by PhaeZee5 on 2008-07-26
I actually solved it with the recovery mode option from grub--- how do you mark a thread as solved? (This is my first post)



Thank you anyway for helping me.

---

### Post by caljohnsmith on 2008-07-26
I'm must admit that I'm amazed that you solved a wireless networking problem with the "recovery mode option from grub", but if your system is back to working, that's great. :) Anyway, to mark the thread as solved, just look for the "Thread Tools" drop-down menu near the top of the thread, and choose the option to mark the thread as solved.

---

