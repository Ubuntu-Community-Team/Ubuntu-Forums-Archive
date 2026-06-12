---
title: "eeepc resolution problem"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Shnooky on 2009-01-06
I am using an eeepc with ubuntu 8.10 with up to date sofware but when i open up some windows and they are to big for the screen and i have to move the window to see all the info.  Any idea how i can make my resolution bigger

---

### Post by Hangwire on 2009-01-06
Try:

```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

and have a look at this 

[https://help.ubuntu.com/community/EeePC/Using](https://help.ubuntu.com/community/EeePC/Using)

---

### Post by snowpine on 2009-01-06
Good info!
A much simpler tip, but you can hold down the Alt key, then double-click and drag anywhere on a window to move it around on the screen. This is handy for when the top or bottom of the windows disappears off the screen of your eee.

The bottom line is, you can't change the resolution on your screen to higher than the maximum resolution. My eee (900ha) has a 1024x600 screen for example, and that is determined by hardware, not software. :)

---

### Post by snowpine on 2009-01-06
It's also worth noting that the minimum recommended resolution for Ubuntu is 1024x768: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Most eee models are less than the recommended resolution for Ubuntu. Ubuntu generally runs fine on the eee, but some windows may be too large for the screen.

Check out the Ubuntu Netbook Remix if you are looking for an alternative. I hate it personally :) but it might be just what you're looking for.

---

### Post by Shnooky on 2009-01-06
I new about the constrain y thing and how to use alt+click but how do i see what my max resolution settings are and how do I set them?

---

