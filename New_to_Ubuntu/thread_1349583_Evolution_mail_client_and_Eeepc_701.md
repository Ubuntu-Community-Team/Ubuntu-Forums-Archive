---
title: "Evolution mail client and Eeepc 701"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by ronma on 2009-12-08
Hi everyone,

I just recently installed the ubuntu netbook remitx (9.10) on my Eeepc 701. I've been trying to use evolution mail client but the setup wizard window is too large for my screen and I can't shrink it down. I've done some searching and read bug reports on this, but they all claim the problem was fixed with 9.04. I don't know what to do from here. I have Evolution 2.28.1-ubuntu2.

Thanks for the help!

---

### Post by LunaticHiatus on 2009-12-08
I run into those situations with these little netbooks. One way around it is to have visual effects on normal, and put a second desktop below it and just drag the application down into the second desktop. Go the second desktop and click ok from there (I use this trick when os's booted from virtual machine are HUGE by default)

Sometimes all you need to do is autohide the taskbar as well. It will move out of the way long enough to click ok and then go back to whatever you where doing.

Personally, I use thunderbird, I have had no trouble with the size of that.

---

### Post by wgilbert5 on 2009-12-08
> **ronma said:**
> Hi everyone,

I just recently installed the ubuntu netbook remitx (9.10) on my Eeepc 701. I've been trying to use evolution mail client but the setup wizard window is too large for my screen and I can't shrink it down. I've done some searching and read bug reports on this, but they all claim the problem was fixed with 9.04. I don't know what to do from here. I have Evolution 2.28.1-ubuntu2.

Thanks for the help!
Bring up the terminal and type:
xrandr -q
This will allow you to change your resolution.  Works for me on my 701. 
Bill

---

### Post by ronma on 2009-12-08
> **wgilbert5 said:**
> Bring up the terminal and type:
xrandr -q
This will allow you to change your resolution.  Works for me on my 701. 
Bill

My computer doesn't seem to like going above 800x480 and I couldn't make it do it with xrandr either.

I'd like to try the second desktop idea, but I'm not sure how to make a second desktop. Is there a guide somewhere? I tried searching but the terms are kinda general. Auto-hiding the taskbar wasn't enough.

Failing that, I'll try thunderbird. Not all programs are made for netbooks, after all.

Thanks!

---

