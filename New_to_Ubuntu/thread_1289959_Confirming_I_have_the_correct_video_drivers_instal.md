---
title: "Confirming I have the correct video drivers installed"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2009-10-13
Okay, so I'm a fairly recent convert and I'm just wondering how I go about making sure I have the correct video drivers installed.

In windows it's detected as a radeon IGP 34xM (I would assume this means it's a 340M).  This is in a vaio PCG-K15 laptop.

The reason I was thinking I should check is because I just installed diablo 2, and while in windows the video test lets me choose between directdraw (2d) with that video card listed above and direct3d with the video card listed above, in ubuntu the only thing it detects is 

Directdraw (2d) Directdraw HAL

Is this normal?  Should it be finding something else, or is this just a result of me running wine?

If not, how do I go about checking to see what ubuntu thinks my video card is, and assuming it's wrong, how do I correct this.  If it's right, is there something else I'm missing?

---

### Post by ConXtionS on 2009-10-13
I am taking notes on this one...

this is going to be something I have also wanted to know... thanks for asking the question

Jim

---

### Post by beastrace91 on 2009-10-13
What video driver did you install?

Also if you are unsure about what hardware you have run the following in terminal: ```
sudo apt-get install sysinfo
```

Then run "sysinfo" its a handy little program that lists out all the hardware in your system.

~Jeff

---

### Post by Excedio on 2009-10-13
> **scared0o0rabbit said:**
> *snip*how do I go about checking to see what ubuntu thinks my video card is*snip*

Open a terminal: Applications > Accessories > Terminal
```
lspci -v
```Scroll back up to see your video card information.

---

### Post by superdav42 on 2009-10-13
It is probably just a wine thing. You can see if your video card is properly setup by running ```
glxinfo
``` and look to see it if it says direct rendering yes.
It will also tell you what video device it detects under render string in the middle somewhere.

For further debugging about the type of card you have and how much memory you got you can run cat /var/log/Xorg.0.log

---

### Post by scared0o0rabbit on 2009-10-13
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: c0300000-c03fffff
    Prefetchable memory behind bridge: e0000000-efffffff
    Kernel modules: shpchp


So I guess that means it's correctly detecting my video card and has the right driver installed, right?

---

