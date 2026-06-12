---
title: "Crystal Eye webcam not working in skype 2.1"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Suparna on 2010-04-18
I have an Acer Travel Mate with a built-in webcam. I am having problems with the video as well as audio. I followed some threads on the ubuntu forum and removed pulse. i have alsa. The webcam and audio to some extent were working. I do not know what happened.

When i try to test the vidoe i get a blank screen the light on the camera is alos not coming on. not working with cheese either.

The audio, i can hear the recorded message but not my own voice. Very frustrated!

Please help.

Suparna

---

### Post by ajgreeny on 2010-04-18
Which version of ubuntu are you using, and why oh why did you remove pulse?  There have been some difficulties with pulse, I know, but removing it completely is not usually the best answer;  it's like beheading yourself because you have a headache.

Try reinstalling all the pulse packages you removed and then trying again to get things working properly by adding one or two other applications that seem not installed by default in the two most recent ubuntu versions.

Come back for more detail when and if things don't improve.

---

### Post by Suparna on 2010-04-18
Sorry, i forgot to mention. I am on Karmic.

Will try your suggestion regarding pulse and come back. what is your suggestion with regard to the webcam?

thanks

suparna

---

### Post by Suparna on 2010-04-18
i have reinstalled the pulse packages. there is no sound at all in skype now! earlier i could hear the lady at least!

whew! what next?

thanks.

suparna

---

### Post by ajgreeny on 2010-04-19
Run **alsamixer** in terminal and make sure nothing is muted or set too low as often appears to be the case.

---

