---
title: "Change screen resolutions through Terminal?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-18
Hi there.

Can somebody please tell me how to change the screen resolutions through a terminal command??

---

### Post by kellemes on 2009-05-18
[xrandr]("http://www.manpagez.com/man/1/xrandr/")

---

### Post by raziiq on 2009-05-18
thanks for the help mate.

I also found this command for changing screen resolutions.

**sudo dpkg-reconfigure -phigh xserver-xorg**

---

### Post by kellemes on 2009-05-18
Doesn't "dpkg-reconfigure -phigh xserver-xorg" reconfigure xorg?
Personally I wouldn't touch xorg only to change resolution..

---

### Post by raziiq on 2009-05-18
dont know much about it, but this is what i searched from other forums.

BTW i have gone through that xrandr, as being a noob to the Terminal, so couldnt get how to use it, can you please give me an example on how to use this command to change the resolution for example 800x600?

BTW can you please explain, what is this xorg??:)

---

### Post by kellemes on 2009-05-18
Type xrandr from terminal gives you a list of modes you can use on your system..
Now you can switch mode like so..
```
xrandr -s 0
```
```
xrandr -s 1
```
and so on..

Xorg is the basis of your graphical system, in general you don't want to touch it if it works ;-)

---

### Post by raziiq on 2009-05-18
oh ok, thanks for the help :)

---

