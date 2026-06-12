---
title: "mouse pointer and printscreen"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Michael Dooley on 2010-05-11
Last week I updated my main computer from 9.04 to 9.10 and then to 10.04, lucid lynx I believe. Since then, I have had troubles with my mouse pointer being an extremely light blue color and appearing as if a Japanese character - which made it quite difficult to use as a selecting device. 

I also noticed that (1) my themes appeared corrupted or messed up and using the System, Appearances, dialog box to get a good mouse pointer did not work. (2) Also, when trying to use the printscreen function to record my difficulties, the resulting captured image looked like my desktop but with strangely scrambled graphics. 

In addition, (3) switching to a Guest session resolved all these difficulties. (4) Booting into a low graphics mode resolves the mouse pointer issue and screen capture issue but some of the themes still appear scrambled.

I have tried renaming my .gconfig file to .gconfigold but lost metacity compositing. The theme appearance still was not optimal as in a guest session.

I think that I should test renaming (and thereby resetting) other files in my home directory such as .gnome, .gnome2, .gconfd, and perhaps .nautilus. Could anyone with more lucid experience than I have perhaps suggest a better course of action? I hate to keep booting into a low graphics mode just to be able to use my system.

Thanks for any assistance you can render.

---

### Post by Michael Dooley on 2010-05-15
Follow-up:

After cloning a successful install from another machine and observing the cloned partitions for a few days, I have decided that my problem was probably due to a faulty graphics card - specifically a loose graphics chip heatsink. I replaced the card with a similar card and have had no troubles since.

---

