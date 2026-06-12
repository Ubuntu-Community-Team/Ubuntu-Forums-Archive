---
title: "Sound will only come back upon restart"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by wgrosvenor64 on 2009-08-12
I'm using ubuntu 9.04 on an Acer Aspire 4720Z notebook.  I am so pleased with it.  Everything works fine but I think one of the upgrades may have done something to my sound.

When I first start the notebook, the sound is great.  I can play DVDs, go to youtube, etc. but if the notebook is sitting idle for awhile, the sound will disappear.  When I restart, the sound will come back as if nothing was wrong.

Please help me, I don't use sound all of the time, but it does get annoying when I do want to use it.

---

### Post by NightwishFan on 2009-08-12
When the sound fails try a few commands from the terminal.

```
speaker-test
```
```
alsamixer -c0
```
```
paplay (DRAG AND DROP FILE HERE)
```

The first command will test speakers.
The second will reveal your volume control
The third will try to play a file of your choice.

Tell me how it goes.

---

### Post by wgrosvenor64 on 2009-08-12
These are the results:

```
speaker-test
```

```
 speaker-test 1.0.18

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 30.069397
 0 - Front Left
Time per period = 30.054719
 0 - Front Left
Time per period = 30.059998
 0 - Front Left
Time per period = 30.059471
 0 - Front Left
Time per period = 30.065232
 0 - Front Left [CODE]

[CODE]alsamixer -c0
```

```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.18 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00]                                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;                        &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     100   100<>100  100<>100 100<>100 100<>100  100<>100                     &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Mic Boos  IEC958  IEC958 D   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
[CODE]

[CODE]paplay (DRAG AND DROP FILE HERE)
```

No matter what file I put there, it says that it cannot be opened.  I must be doing something wrong. 




> **NightwishFan said:**
> When the sound fails try a few commands from the terminal.

```
speaker-test
```
```
alsamixer -c0
```
```
paplay (DRAG AND DROP FILE HERE)
```

The first command will test speakers.
The second will reveal your volume control
The third will try to play a file of your choice.

Tell me how it goes.

---

### Post by NightwishFan on 2009-08-12
Sometimes paplay does not work, it is fine.

Did speaker test play any sound? The second command is an alternate mixer, to make sure nothing is muted.

---

### Post by Temposs on 2009-08-12
Something you should try is killing pulseaudio, which is a program that sort of organizes the sound systems on Ubuntu.

Just whenever your sound stops working, go to System->Administration->System Monitor, and click on the Processes tab, if it's not already selected. Then, find the pulseaudio process, and right click and choose "Kill Process". Then, see if your sound works after that. Note, you may have to restart programs that you have open once you kill pulseaudio, in order for the sound to work on them.

---

### Post by NightwishFan on 2009-08-12
This is an excellent link for reference, it should help, since I will not be online much longer.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by wgrosvenor64 on 2009-08-12
> **NightwishFan said:**
> Sometimes paplay does not work, it is fine.

Did speaker test play any sound? The second command is an alternate mixer, to make sure nothing is muted.

The speaker did not make any sound until I followed the suggestion of killing the pulse audio.  Now I can't get it to stop.

I'm assuming killing pulse audio is a temporary solution.  Would I have to do that every time?

How do I turn this sound off?

---

### Post by NightwishFan on 2009-08-12
If sound works without pulseaudio, I believe you can remove it.

```
sudo apt-get remove pulseaudio
```

---

