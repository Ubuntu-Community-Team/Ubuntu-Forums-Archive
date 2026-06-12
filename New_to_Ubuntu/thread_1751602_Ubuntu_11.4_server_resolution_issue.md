---
title: "Ubuntu 11.4 server resolution issue"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by Anth420 on 2011-05-06
I installed Ubuntu 11.4 Server edition on an old computer of mine and I have it hooked up to a LCD tv. The problem is when it boots to command line, the left 3 characters of the command line are getting cut off, no matter what resolution I set the television to. The issue doesn't happen on the right side of the cli.

I thought it was an issue with the resolution, but I am not 100%. I've tried to google this issue, and none of the solutions seems to have any effect.

Thanks in advance!

---

### Post by Hedgehog1 on 2011-05-07
The issue you are having is because the LCD TV is 'over scanning' - this means the image is zoomed slightly to be sure to fill the screen.  All TVs do this (Computer monitors do not).

There are three options to solve this:

1) Your LCD TV May offer a 1:1 mode, if so you will see every pixel and not lose the edges.

2) Depending on the video driver, you may of the option of compensating for over scan.

3) In many cases, if you change the video to 640x480, your LCD TV will center that so you can see all the text.

Hope the Helps,

***The Hedge***

:KS

p.s. I use a 55" LED LCD HDTV as my monitor.  It offers the 1:1 mode, so I get a full 1920x1080 - but it is a high-end unit, and not all TVs offer the 1:1.

---

### Post by Anth420 on 2011-05-09
Thanks for the reply.

I've flipped through all the settings on the TV and they all have the same issue, so I don't believe it has a 1:1 mode.

How do I set the video to 640x480 from the command line? All of the solutions I have found on google are either for an older version of grub, or they don't have any effect on the video output.

---

