---
title: "Digital camera not detected?"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by pointyblue on 2009-08-02
Hi,

I'm running U9.04, trying to import pictures from a Canon Ixus 85is. Ubuntu doesn't detect the camera - I have checked the connections and everything seems to be fine. (It detects an old HP camera without problems.)

There's no help on Canon's site and the camera comes with drivers for Mac+Win only.

If you know how to make the computer detect the camera please help.

(Pretty desperate here.)

---

### Post by arochester on 2009-08-02
Does it have a card you can put into a card reader?

---

### Post by Sef on 2009-08-02
Plug in your camera and make sure its on, then 

Applications > Accessories > Terminal

then type in this command into Terminal:

```
lsusb
```

Then copy and paste the results here.

---

### Post by pointyblue on 2009-08-02
Guys!

:oops:

So sorry for wasting your time - was helping out my sister and (naturally) she hadn't read the manual. There was a setting in the camera menu I had to enable and then everything worked just fine.

Pretty embarrasing on my part but thanks for your input anyway.

](*,)

---

