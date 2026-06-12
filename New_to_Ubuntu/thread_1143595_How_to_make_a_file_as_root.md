---
title: "How to make a file as root?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by baxna on 2009-04-30
Hello,

I'm trying to follow a tutorial so that I can enable my Thinkpad's middle mouse button for scrolling. The tutorial is located here: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#vertical_scrolling)

One of the steps says, "But you can configure it to act in the same way as in Windows, such that you can use it for vertical scrolling (keep the button pressed and move the TrackPoint up and down to scroll). To accomplish this create the file /etc/hal/fdi/policy/mouse-wheel.fdi as root with the following content..."

My question is, how do I make a file as root? I know commands such as "mkdir" and "mv" but is there one to make a new file? Maybe it's "mk" or something? Thanks for any assistance!

---

### Post by Titan8990 on 2009-04-30
sudo touch /etc/hal/fdi/policy/mouse-wheel.fdi

---

### Post by iaculallad on 2009-04-30
Or

```
gksudo gedit /etc/hal/fdi/policy/mouse-wheel.fdi
```

and place the should be content of the file as specified by the tutorial.

---

### Post by baxna on 2009-04-30
Awesome thank you! :P I tried searching through some command reference lists and couldn't find what I needed.

---

