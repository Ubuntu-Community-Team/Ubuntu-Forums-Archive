---
title: "total noob.... sound card driver?"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by lnxusr351 on 2011-08-31
Hello, fellow Ubuntu users...
I am a recovering Windows user... I need some help... I have a Sound Blaster Audigy sound card in my box, but I am having difficulty installing/finding a soundcard driver. I have found some options, but I don't understand terminal as well as I'd like.

 I have used Terminal regularly in Android OS. I do understand that some commands don't work in Android.... I have alot of reference material, but not much direction. 

Note: Linux does see the card, I just don't know how to make it work. There is a native card on the motherboard that doesn't work/broken. In terminal, I used the command cat/proc/asound/cards which gave me the following: 

0 [HDMI]: HDA-Intel - HDA ATI HDMI  (video card?)
                  HDA ATI HDMI at 0xe5010000 irq 17
1 [CA0106]: CA0106 - CA0106
                     Audigy SE [SB0570] at 0xb000 irq 18
                 
I have found alot of information regarding this on www. alsa-project .org. If I am on the right track, by all means let me know. 

Any help would be greatly appreciated. 
-Mike

---

### Post by bigpayne69 on 2011-08-31
see if this helps
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)

---

### Post by 3rdalbum on 2011-09-01
Click on the Sound icon in the top panel, then go to Sound Settings. In the "Output" tab, click on the sound output device that you want to use, and choose the sound output port that corresponds to what you've actually got the speakers plugged into.

That sets up Pulseaudio. For things that don't use Pulseaudio, you may need to set up the same settings using 'alsamixer', which needs to be run in the terminal.

---

### Post by lnxusr351 on 2011-09-01
Thank you for the assistance, I got it up and running.

---

