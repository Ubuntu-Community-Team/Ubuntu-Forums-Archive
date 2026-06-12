---
title: "recording radio programs"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-05-21
Hi Ubuntu Community:

I want to record a radio program... it is a wonderful jazz program!

How do I get started? How should I connect my sound card and the radio tuner, and what software should I used to record the program?

Any other advice will be very much appreciated!!!:D

Many thanks!
Phil Smith
Duluth, GA

---

### Post by apjone on 2009-05-21
Does your radio have a phono socket (head phones etc) ? 
Does the station not have a webstream ?

---

### Post by Old Jimma on 2009-05-21
Hi Apjone:

Thanks for your reply.

Here are answers to your questions:

1. Does your radio have a phono socket (head phones etc) ? 
A: The radio has stereo RCA jacks and a nice fat head phone jack.

2. Does the station not have a webstream ?
A: Yes... the radio station is the public radio station in Atlanta, GA: [http://www.pba.org/](http://www.pba.org/)

However, that station does not publish a .pls URL. Also, when I followed the "help" link after clicking on the "listen online" button, the "help" says: "Are there Windows Media Player choices for Linux? You can use MPlayer, which is free, or The CrossOver Plugin from CodeWeavers for $25."

I don't know what that means, but I see the $ sign!!!#-o

Thanks,
Phil

---

### Post by apjone on 2009-05-21
If you install mplayer you can run 
```

mplayer -dumpstream rtsp://pubint.wmod.llnwd.net/a48/o1/production/wms/wabe/local-wabe-829859.asf -dumpfile ~/Desktop/pba.mp3

```

from a terminal to record the station to pba.mp3 on your dekstop.


SORRY I GET NO SOUND WHEN I TRY! :(

---

### Post by kaptengu on 2009-05-21
Another way (not a pretty solution) is to enable mix capturing under switches in the volume control (to enable this switch, Edit->Preferences). Now you can record what you hear from your speakers with e.g. gnome-sound-recorder.

---

### Post by boof1988 on 2009-05-21
> **apjone said:**
> If you install mplayer you can run 
```

mplayer -dumpstream rtsp://pubint.wmod.llnwd.net/a48/o1/production/wms/wabe/local-wabe-829859.asf -dumpfile ~/Desktop/pba.mp3

```

from a terminal to record the station to pba.mp3 on your dekstop.


SORRY I GET NO SOUND WHEN I TRY! :(

Thanks for this tip.

I just recorded a stream to the file.  Then opened up another terminal and used another instance of mplayer to play the file.  It may not be the most elegant, but it works for me.  I can pause the playback of the file.  It seems to me that I can't pause stream for very long when I'm listening to it directly.  But when I record the stream and then listen to it I can pause for as long as I need.

---

### Post by boof1988 on 2009-05-21
> **apjone said:**
> If you install mplayer you can run 
```

mplayer -dumpstream rtsp://pubint.wmod.llnwd.net/a48/o1/production/wms/wabe/local-wabe-829859.asf -dumpfile ~/Desktop/pba.mp3

```

from a terminal to record the station to pba.mp3 on your dekstop.


SORRY I GET NO SOUND WHEN I TRY! :(

Not trying to hijack this thread... Just think that the following question may help other people as well.

Is there a way to have this command record for a set time (say 1/2 hour)?

---

### Post by unutbu on 2009-05-21
boof1988, you could make a script that launches mplayer, sleeps for 1/2 hour, and then terminates the mplayer process:

```
#!/bin/sh
mplayer -dumpstream rtsp://pubint.wmod.llnwd.net/a48/o1/production/wms/wabe/local-wabe-829859.asf -dumpfile ~/Desktop/pba.mp3 &
pid=$!
sleep $((60*30))
kill $pid

```

---

### Post by boof1988 on 2009-05-21
> **unutbu said:**
> boof1988, you could make a script that launches mplayer, sleeps for 1/2 hour, and then terminates the mplayer process:

```
#!/bin/sh
mplayer -dumpstream rtsp://pubint.wmod.llnwd.net/a48/o1/production/wms/wabe/local-wabe-829859.asf -dumpfile ~/Desktop/pba.mp3 &
pid=$!
sleep $((60*30))
kill $pid

```

Thanks...  I'll give it a try.

---

### Post by logos34 on 2009-05-21
> **Phil Smith said:**
> Hi Apjone:

Thanks for your reply.

Here are answers to your questions:

1. Does your radio have a phono socket (head phones etc) ? 
A: The radio has stereo RCA jacks and a nice fat head phone jack.

2. Does the station not have a webstream ?
A: Yes... the radio station is the public radio station in Atlanta, GA: [http://www.pba.org/](http://www.pba.org/)

However, that station does not publish a .pls URL. Also, when I followed the "help" link after clicking on the "listen online" button, the "help" says: "Are there Windows Media Player choices for Linux? You can use MPlayer, which is free, or The CrossOver Plugin from CodeWeavers for $25."

I don't know what that means, but I see the $ sign!!!#-o

Thanks,
Phil

I have no problem streaming their audio in Firefox using the Mozilla-mplayer plugin.  Just click on 'Listen online' and a separate window should popup and start playing.

Alternatively I was able to right-click on that popup window, copy the URL
([http://www.publicbroadcasting.net/wabe/ppr/wabe3.asx](http://www.publicbroadcasting.net/wabe/ppr/wabe3.asx)) and use it in **Streamtuner** (+Streamripper).  Just  make a new station preset, add the .asx url, and hit play.  Then hit 'record' to save. (configure first)

streamtuner (in the repos) is probably the most popular way to get streaming audio.

You could also record as suggested above using Sound Recorder (-->from 'mix'), or simply do

arecord -f cd -t raw | lame -x - out.mp3

(records sound card output, converts on the fly to mp3 (cbr 128 kbps)

just some ideas to consider

---

### Post by andrew.46 on 2009-05-21
Hi,

Just be a little careful with '-dumpstream' though as changing the suffix does not alter the nature of the stream with MPlayer. For example using the stream that you mentioned:

```

mplayer -cache 2048 mms://pubint-wabe3.wm.llnwd.net/pubint_wabe3 \
        -dumpstream -dumpfile **[COLOR="Red"]test.asf[/COLOR]**

```

leaves an audio file that FFmpeg identifies as:

```

Stream #0.0(eng): Audio: wmav2, 32000 Hz, stereo, s16, 40 kb/s

```

while changing the *output file* to mp3:

```

mplayer -cache 2048 mms://pubint-wabe3.wm.llnwd.net/pubint_wabe3 \
        -dumpstream -dumpfile **[COLOR="Red"]test.mp3[/COLOR]**

```

still creates the *same type of file*:

```
Stream #0.0(eng): Audio: wmav2, 32000 Hz, stereo, s16, 40 kb/s
```

So if you are saving the stream in this way you must either identify the stream correctly first to label it correctly, don't give it a suffix at all and work it out later or perhaps save it straight to wav and encode it at your leisure:

```

mplayer -cache 2048 mms://pubint-wabe3.wm.llnwd.net/pubint_wabe3 \
        -vo null -vc null -ao pcm:waveheader:fast:file=test.wav

```

What other program gives you so many possibilities :-).

Andrew

---

### Post by Old Jimma on 2009-05-21
Logos 34-dude:

I bet this is pretty close to the best thing to do. Many thanks for your reply.

I'll buy RCA to RCA and give this a test. I'm betting a Windows enthusiast that this can be done better in Ubuntu than Windows.

BTW... With all the high-falootin' techies hanging arround Ubuntu, it seems like somebody should write some nice software just to do this low-tech thing!

I'd offer a reward, but I'm not Mark Shuttleworth! ():P Hi Mark!)

Again, many sincere thanks!

Luv Ubuntu!

Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2009-05-21
ANDREW:

THANK YOU!

Phil

---

### Post by andrew.46 on 2009-05-22
Hi Phil,

> **Phil Smith said:**
> THANK YOU!

Well I felt a little awkward as my post seemed to be rapidly turning into an MPlayer tutorial and I suspect many people are not keen on the commandline for such things :-).

But if you were ever keen on using MPlayer for such a stream believe it or not the commandline can be tuned even a little *further* and below is what I would use *myself*:

```

mplayer -v -cache 2048 -bandwidth 1000000 -cache-min 80 \
        mms://pubint-wabe3.wm.llnwd.net/pubint_wabe3 \
       -dumpstream -dumpfile test.asf

```

This is with the svn MPlayer but I believe these options exist in the creaky old repository MPlayer!

Andrew

---

