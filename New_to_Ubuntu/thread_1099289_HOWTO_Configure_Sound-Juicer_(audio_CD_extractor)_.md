---
title: "HOWTO: Configure Sound-Juicer (audio CD extractor) for mp3 VBR and Paranoia"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by o.besner on 2009-03-18
I love Sound-Juicer. I think it's a great app that doesn't get the love it deserves, mainly because it is deceptively complicated to setup and much more powerful than it looks. Here is, in three steps, how to tweak it properly.


Step 1: Enable mp3 ripping
------

Sound Juicer is based on Gstreamer, like Totem and Rhythmbox. To enable mp3 playback, you must intall the Good, the Bad and the Ugly (like the movie) packages. You will find them in Synaptic Package Manager, if you search for "Gstreamer". You really can't miss them.

Step 2: Enable error correction in Sound-Juicer
------

Sound Juicer can, when set up properly, detect scratches and attempt to read problematic sectors. When enabled, it's not as good as EAC on Windows but definitively better than iTunes or Windows Media Player. 

Important : enabling full paranoia will lower your rip speed. It's worth it. Ripping a cd takes a few minutes, but you will keep the files for a long time, and who doesn't have a few scratched CDs in his collection?

Open a console, and type ```
gconf-editor
```

Go in apps ---> sound-juicer and change the paranoia value from "8" to "255"

Step 3 : Ripping in mp3 VBR
----------

Variable bitrate encoding is the way Lame (the mp3 encoder) was meant to be used. Quality is decided on a scale from 0 to 9, 0 being best and 9 worst.

Why you should use it : 
- for the same file size, a VBR mp3 will sound noticeably better than a file with a constant bit rate. It's logic : bitrate is subtracted from silence/quiet parts and added to noisier parts of your songs.
- Does not break compatibility with anything I know

Why you might not want to use it: You cannot predict the file size that will be produced, you can only choose the quality scale.

Here's a correlation between the quality settings and the obtained bitrates :
-V 0 (best) : 220-250 kbps
-V 2 (high) : 175-210 kbps
-V 3 (recommended) : 160-190
-V 5 (good iPod setting) : 110-135 kbps

Open Sound-Juicer. Go in Edit --> Preferences --> Edit Profiles --> select "CD Quality,Mp3".

This should be your new pipeline :

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=2 vbr-min-bitrate=32 vbr-max-bitrate=320 ! xingmux ! id3v2mux
```


The only thing you should change is "vbr-quality=2". You should instead insert your desired quality level here. What is generally recommended is to try a few settings by yourself, and then selecting which bitrate is transparent for you.

Hope this can help. This is a mashup of what I have found on the Arch Linux and Ubuntu forums, but I've never seen it on a single page.

---

### Post by dondrup on 2009-04-04
i installed juicer using synaptic but cannot find it to open it. i restarted and still can't find it. shouldn't it be in Applications>Sound and Video? using 8.10

thanks!

---

### Post by o.besner on 2009-04-04
> **dondrup said:**
> i installed juicer using synaptic but cannot find it to open it. i restarted and still can't find it. shouldn't it be in Applications>Sound and Video? using 8.10

thanks!

On Ubuntu, it is renamed "Audio CD Extractor" or something very similar.

It is indeed under Applications --> Sound and Video

However, the real name of the program is Sound Juicer.

---

### Post by dondrup on 2009-04-04
ah, there it is. i also looked at a "how to find application" thread and found the ALT+F2 worked well if i typed in "sound-juicer".

thanks

---

### Post by logos34 on 2009-04-05
> **o.besner said:**
> I love Sound-Juicer. I think it's a great app that doesn't get the love it deserves, mainly because it is deceptively complicated to setup and much more powerful than it looks. 

Poorly designed app, IMO.  Configuration/settings are a nightmare for linux noobs.  They should redo it or replace it with a better one.

---

### Post by o.besner on 2009-04-05
> **logos34 said:**
> Poorly designed app, IMO.  Configuration/settings are a nightmare for linux noobs.  They should redo it or replace it with a better one.

True. Grip also needs to be easier to configure. Why not integrate cd ripping with Brasero or even Nautilus ? Drag n' drop.

---

### Post by logos34 on 2009-04-05
> **o.besner said:**
> Why not integrate cd ripping with Brasero

right, like you can do with K3b (which I run on gnome).  But, yeah, maybe Brasero.   Or nautilus browser.  It already burns.  How hard can it be to provide cd rip support, or at least a plugin?

---

### Post by L8erG8er on 2009-08-17
Thank you o.besner for this little tutorial.  I only recently realized that my sound juicer was ripping everything to a 128 constant rate.  This works great.

---

### Post by acornbrain on 2009-09-23
can't seem to use juicer...

when I hit 'Extract', Sound juicer closes and that's the end of that.

---

### Post by atari05 on 2009-10-21
This seems to do the trick!

However I'm a confused.

whats the difference between vbr= and vbr-quality= ?

I would thinking setting one or the other would allow gstreamer to set the vbr LAME value..

Also, I have noticed for the vbr values to work you have to set min and max bit rates....doesn't that take the ease out of just saying "hey lame, use -V0" and it doing its thing?

I'm assuming there much be some weirdness with gstreamer that requires all this "unessary arguments"?

---

### Post by o.besner on 2009-10-21
Hey Atari,

I'm not using Ubuntu nor sound-juicer anymore (respectively Arch Linux and K3B) but if I remember well vbr= is the variable for cbr, abr and vbr and vbr-quality= is the same as LAME VBR -V* setting. 

Enjoy

---

