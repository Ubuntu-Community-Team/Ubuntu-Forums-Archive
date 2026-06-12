---
title: "No sound after latest update"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by KarenAK on 2010-02-09
I did the kernel update as recommended and now the sound is gone.

Current kernel version: 2.6.31-20-generic-pae

Already did the sound tutorial - nothing. 

Soundcard is recognized, everything looks like it did before - but no sound on internal or usb speakers. (Nothing is muted)


Somebody please help with either going back to an earlier kernel version or how to repair this.



(I cannot even begin to say how very, very, very tired I am of this sound issue in Ubuntu)

---

### Post by buddyd16 on 2010-02-09
I am in the same boat I just updated and have lost all sound. Sound was an issue before but I used the pulseaudio equalizer script here on the forums and had everything sounding a little better.

---

### Post by KarenAK on 2010-02-09
when I originally installed Ubuntu it took me 2 days or so to get sound and video working. I dreaded updating to Karmic because I thought it might turn out to be just as difficult. Therefore it was a nice surprise when it all worked just fine. .... And now this.

---

### Post by buddyd16 on 2010-02-11
KarenAK: I may have solved my problem so lets see if what I did works for you also.

first open a terminal and type ```
aplay -l
``` and post the output.

---

### Post by KarenAK on 2010-02-14
thank you buddyd16 - I was just coming here to tell you the same. 
I solved it by installing a different kernel
[http://www.unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint](http://www.unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint)
I installed 2.6.32-02063208
Sound was back immediately.

---

