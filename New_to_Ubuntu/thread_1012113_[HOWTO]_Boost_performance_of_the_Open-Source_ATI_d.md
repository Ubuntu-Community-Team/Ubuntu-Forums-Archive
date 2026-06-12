---
title: "[HOWTO] Boost performance of the Open-Source ATI drivers"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Mazza558 on 2008-12-15
Today I stumbled on a fix for the awful slow scrolling experienced by many ATI cards using the open-source ATI drivers on Intrepid Ibex (8.10). This definitely works on the ATI Mobility 1150 graphics card, which means any Inspiron 1501 will be boosted by this tweak. Either way, try it out, and see if it makes a difference for you.

So here it is:

**Step 1: Open Xorg.conf in Gedit**

```
gksudo gedit /etc/X11/xorg.conf
```

**Step 2: Add the Xorg option**

Add this line under the "device" section:

```
        Option          "AccelMethod" "EXA"
```

and then save the file.

**Step 3: Test it out!**

Finish whatever you're doing and press Ctrl + Alt + Backspace to logout and restart the X server. Log in - feel the difference?

**Doesn't work?**

No problem, just open the same file and remove the tweak.

**X is broken?**

If you can only get to a terminal after this tweak, run this in the terminal to fix it:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Izek on 2008-12-15
It DOES work for me in hardy, BUT, there's like no performance boost.

How do I know it is working? screens are rendered horizontally instead of default.

---

### Post by Duck2006 on 2008-12-15
This,

sudo gedit /etc/X11/xorg.conf

Should be.

gksudo gedit /etc/X11/xorg.conf

---

### Post by Mazza558 on 2008-12-15
> **Duck2006 said:**
> This,

sudo gedit /etc/X11/xorg.conf

Should be.

gksudo gedit /etc/X11/xorg.conf

Updated the original post.

---

### Post by Mazza558 on 2008-12-15
> **Izek said:**
> It DOES work for me in hardy, BUT, there's like no performance boost.

How do I know it is working? screens are rendered horizontally instead of default.

What's your graphics card?

---

### Post by Izek on 2008-12-15
> **Mazza558 said:**
> What's your graphics card?

ATI Radeon HD 3200 (Integrated)

It's a RadeonHD that's not supported by radeonhd, it's supported by fglrx.

---

### Post by Mazza558 on 2009-01-21
Just a note - Jaunty has this setting enabled automatically, so requires no tweakage.

---

