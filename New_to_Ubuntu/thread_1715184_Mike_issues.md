---
title: "Mike issues"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by dobbie on 2011-03-26
I am having trouble with skype, I can see and hear the other person and they cannot see me. I therefore assume that there is a problem with my mike. I have no idea of where to even look for mike controls. Sorry if this sounds like a silly question but I am not really very computer savvy.

---

### Post by roger_1960 on 2011-03-26
Hi
Try this:

Go to accessories>terminal

Type > alsamixer return and then scroll right using the right arrow to highlight "mic" and then increase the volume with the up arrow.  Then ESC to exit.

I assume the problem is with hearing you rather than seeing you!

---

### Post by prshah on 2011-03-26
> **dobbie said:**
> I therefore assume that there is a problem with my mike. I have no idea of where to even look for mike controls.

Click the volume control applet (near the date/time), and choose "Sound preferences"; open the "Hardware" tab and ensure that you have atleast one input device (may be combined as a singe input/output device). Then, click the "Input" tab, and "choose" the relevant input device. Unmute the input and adjust volume until the sound meter registers sound.

if you run into problem, please post back with screenshot of the Sound preferences window, Input tab.

---

