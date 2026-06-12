---
title: "Mic not working with Skype"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Stoker580 on 2010-06-09
Hi

I've installed Ubuntu 10.04 Netbook Edition on my Acer Aspire One and it is working well with one exception so far. I've installed the latest version of Skype 2.1.0.81 which again works well with the exception of the microphone. Initially I would get about half a second of sound on the test call and then it would go silent (although I could hear the Skype announcement). I tried installing Pulse Audio Volume Control as recommended in another thread but now I don't get that first half second of sound. When I try to adjust the sound options in Skype there is only one option available - Pulse Audio Server (local).

The mic works ok with Sound Recorder if I choose the CD Quality options but when I use the Voice options nothing is recorded/played back.

Can anyone help?

---

### Post by decrow06 on 2010-06-09
In skype's sound options, disable skype from automatically adjusting the levels.  Then, in the pulse audio volume control box, select input devices and unlock the two input channels.  then drag one of them, it doesn't matter which, all the way to the left.  this should do it.

---

### Post by Stoker580 on 2010-06-09
Many Thanks Decrow06. That worked a treat - I had seen advice like this before but the added piece of info that you provided about needing to unlock the two channels made all the difference. I've only to sort out the menus now which appear to be black on black until the pointer passes over them. I think i've seen this mentioned on another thread somewhere so I'll start searching.

BTW How do I indicate that my query is solved?

---

