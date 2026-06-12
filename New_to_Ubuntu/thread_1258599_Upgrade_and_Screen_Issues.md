---
title: "Upgrade and Screen Issues"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by crania on 2009-09-05
Hi Guys,

This is my first post ever so please be gentle!!

I've had a few linux versions on a dual boot system for a couple of years now and they have always been relatively trouble free, thanks to some good luck and good friends I guess.

Today I downloaded 9.04 and when I install it or use live CD my desktop screen looks terrible. The colours are all wrong and when I open a new window(?) it is basically unreadable. When the Kubuntu logo comes up during the boot phase it looks good only at login screen and desktop do I have the problem.

Any help would be very much appreciated and my friends assure me the support doesn't get any better than these forums. Also please make replies as simple as can be, I like computers etc but I'm not very good.

Thanks in advance!!

---

### Post by Liolikas on 2009-09-05
Which vga card and drivers proprietary/not you have?

---

### Post by ziroday on 2009-09-05
Hi crania! Welcome to the forums,

To help you out we're going to need to know the model of your graphics card. To find that out you can do: ```
lspci | grep VGA
```

It would also be really helpful if you could attach your Xorg log file located in: ```
/var/log/Xorg.0.log
```

---

### Post by crania on 2009-09-05
Not sure how to find out which vga card I have! I really am that hopeless... sorry

---

### Post by crania on 2009-09-05
Thanks guys, here goes

This was what i could make out of my VGA stuff:

01:00.0 VGA Compatible controller: Silicon Integrated Systems [SIS] 661/741/760 PCI/AGP or 662/671Gx PCIE VGA Display Adapter.

for the log stuff:

permission denied

Hope it helps!!

---

### Post by cmcanulty on 2009-09-05
I had a similar issue on a Ubuntu 9.04 install. Tried everything, then rt clicked desktop,change desktop background, visual effects, none, and now all is fine.

---

### Post by crania on 2009-09-05
After much playing around I finally was able to see the icons for screen settings and change resolution and alls working. Thanks guys for your help.

---

