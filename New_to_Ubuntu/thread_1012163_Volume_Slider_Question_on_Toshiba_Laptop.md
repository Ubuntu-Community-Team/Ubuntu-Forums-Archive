---
title: "Volume Slider Question on Toshiba Laptop"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Jeebus McChrist on 2008-12-15
First I'd like to say hello. This is my first post on Ubuntu Forums but I've been a lurker for a while; the search function has been my guide for most of the time. You guys are pretty helpful. Anyways, I just recently switched to Ubuntu from Vista and am still getting the hang of things, so bear with me if this question is idiotic.

Basically, here's the issue: I have a Toshiba laptop, model A305-S6837, and it's been totally fine up until now. However, the volume slider on the  front side of the laptop, which has worked fine before, has suddenly stopped working. When I slide it, it displays the pop-up graphic on screen and the graphic shows that it's working normally. Except... it's not changing the volume. I  can change the volume with the volume slider on the top of the desktop, but the slider won't change a thing.

The only thing I've done is go into the Sound program in Preferences and I'm assuming that's what caused this. My question is, why would this cause the volume slider to stop working? I've tried restarting, and I've also checked out alsamixer (not that that would have much to do with this) and the problem persists.

If anyone can help me out, that'd be great. Thanks in advance.

---

### Post by jbrown96 on 2008-12-15
I think that the volume control is set to the wrong channel. I think you can right click on it and select channel or preferences. I generally have the best luck with PCM and master -- front will work but probably not if you want to control headphone volume. To make sure you have the right channel, play some audio and have alsamixer open in a terminal to see what is actually happening. This will make sure that the button is doing something and just set to the wrong channel.

---

### Post by Jeebus McChrist on 2008-12-15
Awesome, thanks. Got it figured out. I had just selected a different playback device and didn't realize what I was doing. Once I selected the right one it worked perfectly. Thanks again!

---

