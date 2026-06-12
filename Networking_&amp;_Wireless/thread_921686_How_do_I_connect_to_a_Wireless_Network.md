---
title: "How do I connect to a Wireless Network?"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by Hyside on 2008-09-16
Having trouble finding how to connect to a Wireless Network. I had this problem a few months back when I had originally installed Ubuntu on the same laptop. 

Anyone care to help me? I simply cannot find the program which managed Wireless Networks.

---

### Post by nixscripter on 2008-09-17
If you're using normal Ubuntu (which uses gnome), there should be a small icon on your Notification Area called the network manager applet. If your wireless card is working, it should let you connect by pulling down a menu. Right click it and make sure that "Enable wireless" is checked. If you can't see it, open a Terminal and run: ```
nm-applet
``` and it should appear. If you're using Kubuntu (which uses KDE), I don't know what they do, but it should be similarly easy.

If you don't see an "enable wireless" option, your card isn't being detected, and that's the problem.

---

### Post by Hyside on 2008-09-18
Thanks, I'll try that now!
**Edit:** It appears as though its not reading any Wireless Works. It must not be reading my Wireless card then. Maybe I should try installing Ubuntu from my Install Disc rather than using Wubi?

---

### Post by nixscripter on 2008-09-18
Just try booting from a LiveCD proper -- don't bother with an install yet -- and see if it works then. I don't know what Wubi does with your hardware, but a real boot should use everything the same way a normal install would.

Getting it working off the CD, in fact, would be a good first step before you install.

---

### Post by Hyside on 2008-09-19
> **nixscripter said:**
> Just try booting from a LiveCD proper -- don't bother with an install yet -- and see if it works then. I don't know what Wubi does with your hardware, but a real boot should use everything the same way a normal install would.

Getting it working off the CD, in fact, would be a good first step before you install.
Thanks, I'll see if it works. If it doesn't, I'll ask you through a PM because you seem fairly knowledgeable on the subject.

---

### Post by nixscripter on 2008-09-20
Posting would probably be better. That way, everyone can see your answer.

In my experience, wireless on linux is one of those things that just works 80% of the time, works after you fight with it tooth and nail 18% of the time, and works after you buy some new hardware 2% of the time.

The one disadvantage of the CD is that it caches everything in memory, so it's a lot slower than Wubi (whose performance I am assuming is reasonable). But it uses the real hardware, so in the case of hardware drivers, that's the best way to go.

---

