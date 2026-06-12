---
title: "microphone doesn't work in ubuntu 9.10"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by antonio_ing on 2009-11-06
Hi guys

i just have updated to ubuntu 9.10 my old laptop toshiba satellite M50. I'm very happy about it but i recognize the microphone that does not work anymore. I see from the sound preferences that it reads something, but i do not hear nothing on the loudspeaker (the volume is high of course :-) )!

any suggestion?

---

### Post by papangul on 2009-11-06
Have you checked alsamixergui and pavuconrol that mic is not muted?

---

### Post by cosine352 on 2009-11-06
> **antonio_ing said:**
> Hi guys

i just have updated to ubuntu 9.10 my old laptop toshiba satellite M50. I'm very happy about it but i recognize the microphone that does not work anymore. I see from the sound preferences that it reads something, but i do not hear nothing on the loudspeaker (the volume is high of course :-) )!

any suggestion?

probably you need a microphone boost. see the attach pictures. hope this help. you can find the microphone boosts switches in the preferences button in the sound control.

---

### Post by dragonboss on 2009-11-06
Try using the sound recorder to record a test sound

---

### Post by gradinaruvasile on 2009-11-06
Open a terminal, type
alsamixer

Then press TAB, and u are in the capture view (tab). Press alt+printscreen, save the picture and post it here.

---

### Post by antonio_ing on 2009-11-06
here there is the alsamixer of capture

---

### Post by antonio_ing on 2009-11-06
it records the sound !!!
quite strange, maybe will be fine for skype. I'll try immediately

---

### Post by antonio_ing on 2009-11-06
i have just removed to allow to skype to change my mixer levels and everything went just fine.

Thank you very much guys

---

