---
title: "MP3s start OK then slow drastically"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by iank1 on 2009-06-08
I am completely new to Ubuntu (ex Windows) and am happy so far. Now I need to get MP3s to play.

Scenario: I reboot into Ubuntu; I select the application 'Rhythmbox Music Player'; I select an MP3 song; the song starts to play normally but only for about 15 seconds; after about 15 seconds it slows drastically to about 1/400th of normal speed; one second of music takes about 6.5 minutes to play; the sound becomes a series of clicks (sometimes resembling a pneumatic drill); there are no error or warning messages; MP3 files played OK in Windows.

My computer is a Toshiba Notebook Equium L20, Celeron 1.4 GHz, 1GB ram. My playback hardware devices appear to be:

Card 0: Multimedia audio controller, IXP SB400 AC'97 Audio Controller, driver= ATI IXP AC97 contoller
Card 1: Modem, SB400 AC'97 Modem Controller, driver =ATI IXP MC97 controller.

Any suggestions are welcome. I am happy to use the Terminal if instuctions or links are specific. Thank you.

---

### Post by LowSky on 2009-06-08
try another application, for instance banshee

to install using terminal

```
sudo apt-get install banshee
```

---

### Post by iank1 on 2009-06-08
Thanks Lowsky for your promtp reply. Unfortunately the same problem happens in Banshee. I think I have a hardware/driver problem. Any more suggestions?

---

### Post by durand on 2009-06-08
Have you tried other music formats? Like ogg or flac? Try converting one of your mp3s with [soundconverter]("apt://soundconverter")

---

### Post by iank1 on 2009-06-08
Thanks Durand,
Have converted one of my MP3 files to ogg. using sounconverter but still have same problem. Although new to Ubuntu, I believe that Rhythmtbox and Banshee will play MP3 (and .ogg iles) files. Ubuntu does not give any error or warning messages so my problem must be hardware or driver related. Any comments welcome.

---

### Post by durand on 2009-06-08
> **iank1 said:**
> Thanks Durand,
Have converted one of my MP3 files to ogg. using sounconverter but still have same problem. Although new to Ubuntu, I believe that Rhythmtbox and Banshee will play MP3 (and .ogg iles) files. Ubuntu does not give any error or warning messages so my problem must be hardware or driver related. Any comments welcome.

I was just wondering whether it was a codec problem.

---

### Post by eMJayy on 2009-06-08
Try switching the driver being used for music and movies by going to *System > Preferences > Sound*. Test the selection first to make sure the driver is compatible with your sound device. Then, if you find alternate drivers that work, try to play music files using the new setting. I think Alsa drivers are supposed to support your sound device. 

Also try temporarily turning off System sounds (located in the _Sounds_ tab right next to _Devices_ tab of the Sound Preferences menu). Unclick *Play alerts and sound effects* and retest playback of an mp3. I've found that having System sounds turned on can sometimes conflict with other programs that use sound (for me, it conflicts with using 5.1 Surround Sound).

---

