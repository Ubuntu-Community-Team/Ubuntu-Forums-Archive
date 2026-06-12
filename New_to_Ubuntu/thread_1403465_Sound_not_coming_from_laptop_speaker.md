---
title: "Sound not coming from laptop speaker"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by shashanka on 2010-02-10
Hello i have dell studio 14 laptop with  windows 7 and ubuntu 9.10  64bit.
I am not able to get any sound from laptop speaker, But when i plug my earphone sound plays fine. I have searched in google and tried various methods but still no sound... 

Here are outputs of necessary comands :

lspci | grep -i audio :
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]



cat /proc/asound/card0/codec#* | grep -i codec :
Codec: Realtek ID 665

and in alsamixer none of the channels are muted.

---

### Post by Jefferythewind on 2010-02-10
I have had a few problems with my sound card before, especially with built in devices like speakers or microphone.  I seemed to solve all my problems just by playing with the settings in the "sound preferences" window.  For example, in the "Output" menu in "sound preferences" you choose connector, either speakers or headphones.  I think if you look around in there you will find the problem.

good luck.

---

### Post by warfacegod on 2010-02-10
Make sure "PCM" volume is high enough.

---

