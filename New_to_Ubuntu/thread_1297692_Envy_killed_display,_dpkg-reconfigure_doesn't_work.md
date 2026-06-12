---
title: "Envy killed display, dpkg-reconfigure doesn't work"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by Tyrsius on 2009-10-22
I have been running Ubuntu off the onboard video card in this box for long time without issue. I just got a free Radeon x1300 and slapped it in the box. It booted up fine, and so I ran envy to set the driver for it. Now when I boot the GUI is just some red symbols and runny colored lines.

I tried running dpkg-reconfigure xserver-xorg from the recovery menu as root, but it had no effect.

How do I change back the driver? I am really stuck here.

---

### Post by yeats on 2009-10-22
If you have envyng installed, you should be able to run it from the terminal by typing:

```
envyng
```

It will have a simple text interface that should allow to roll back what you did.

That's if you can get to a terminal.  When the same thing happened to me, the X server wouldn't release the keyboard and I had to ssh in to solve the problem :-).

---

### Post by arochester on 2009-10-22
Try:

Not booting into your normal kernel (top of boot list)

Boot into Recovery Mode (second on boot list)

Look for an option something like " Try to recover Xserver" (you might need to scroll up and down to find it )

Have a go at that...

---

### Post by Mark Phelps on 2009-10-22
> **Tyrsius said:**
> I have been running Ubuntu off the onboard video card in this box for long time without issue. I just got a free Radeon x1300 and slapped it in the box. It booted up fine, and so I ran envy to set the driver for it. Now when I boot the GUI is just some red symbols and runny colored lines.

You didn't say which Ubuntu version you're running, but if it's it 9.04 (or newer) your problem is that there are no ATI drivers that work with your card anymore.

To remove the ATI drivers and replace with the open source ones, see the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Tyrsius on 2009-10-23
Thank you mark, that guide got everything fixed. Had to completly purge fglrx and reinstall the ati driver, but its working again.

---

### Post by Mark Phelps on 2009-10-23
Glad to see that you were able to recover.

Just wish everyone wouldn't just tell folks to install the restricted ATI drivers by default -- that's caused more problems than I care to count!

---

