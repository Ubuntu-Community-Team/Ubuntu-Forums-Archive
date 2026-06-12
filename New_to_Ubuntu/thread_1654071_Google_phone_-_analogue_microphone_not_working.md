---
title: "Google phone - analogue microphone not working"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by craig1976 on 2010-12-27
Hi

I've tried to phone people using the Google phone in my e-mail account. When the other person answers I can hear them but they cannot hear me.

I think I need to change a setting in Ubuntu but not sure what. The microphone works with other devices and has enabled me to record sound. 

I'm using Ubuntu Hardy Heron.

any help would be great. thanks!

Craig

---

### Post by phob0ss on 2011-07-12
**sudo apt-get install pavucontrol**
then run pavucontrol
in input devices choose port "Internal Microphone"
and that's it.
It worked for me. At least the mic meter is moving in chat settings in Gmail when I talk. I didn't try to talk to anyone though.

---

### Post by phob0ss on 2011-07-13
Oh, and do not forget to run alsamixer in console and toggle mute of the microphone off (M button). You can switch between channels with left and right arrows and increase volume with up and down arrows.
I checked how it works today and everything seems to be fine.

---

