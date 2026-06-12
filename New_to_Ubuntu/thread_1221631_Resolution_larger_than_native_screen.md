---
title: "Resolution larger than native screen"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by dr_pressure on 2009-07-24
Hi,

I'm running Ubuntu on a netbook -- 1024x600 screen -- and I want to connect it to an external monitor.

Currently if I go into the display preferences and enable the external monitor, it will not increase the resolution. I suspect this is because it still displays on the main screen.

What I'm looking for is a way to disable the main screen and display at a higher res on the external monitor.

Any suggestions?

Cheers!

---

### Post by Hospadar on 2009-07-24
You should probably look into xrandr, or one of it's graphical frontends like grandr, it may or may not work depending on your graphics hardware and the drivers you are using, but it'd be my first guess for what will work.

It's the program in linux designed to deal with hotplugging and on-line x server changes.

---

