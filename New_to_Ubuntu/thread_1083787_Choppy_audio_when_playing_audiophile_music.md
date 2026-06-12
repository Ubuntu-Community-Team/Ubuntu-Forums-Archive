---
title: "Choppy audio when playing audiophile music"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by gackt on 2009-03-01
hey guys, every time i plays audiophile music (like Flac format) the sound is choppy. The file size is about 50-80mb each file. My amarok is using alsa (i think). So what to configure in order to listen this music smoothly ( i have dual core with 2gig memory). The only way i could play this kind of music is by using vlc + Jack. Thanks, i really want this music to be played in amarok.

---

### Post by gackt on 2009-03-01
Anyone?

---

### Post by diablo75 on 2009-03-02
Is PulseAudio an available output option in Amarok?

---

### Post by gackt on 2009-03-02
Yes...and its still choppy...

---

### Post by blazemore on 2009-03-02
Is your CPU very old?

---

### Post by gackt on 2009-03-02
> **blazemore said:**
> Is your CPU very old?

Dual core 1.86, is that too old?

---

### Post by diablo75 on 2009-03-02
> **gackt said:**
> Dual core 1.86, is that too old?

Hardly.

This doesn't occur with other types of audio files, right?

---

### Post by markbuntu on 2009-03-02
If your sound is scratchy or stuttering or choppy you can edit these lines in the file /etc/pulse/daemon.conf to look like this


default-fragments = 5
default-fragment-size =25

These are not written in stone, you can play around with them.

There are also some sound cards/chips that can only be fixed with an ALSA upgrade so you may want to consider that if this does not work for you. You should also make sure users and root are members of the groups

pulse
pulse-rt
pulse-access

This will, among other things, give pulseaudio high priority with the kernel.

---

### Post by mikechant on 2009-03-02
This is a bit strange. I have a very similar spec machine to yours and I can do the following all at the same time:
a) Rip an audio CD
b) Generate a DVD iso on disc
c) Use firefox
and
d) Play flac or wav music 100% smoothly!

Have you got something running in the background which is using lots of CPU or RAM? Have you tried running the 'top' or 'htop' commands in a terminal to see what is using resources apart from your music player?

Also, if you are running pulseaudio (default in releases 8.04, 8.10 onwards unless disabled/removed), this can cause sound glitches - I seem to remember there's a guide for pulseaudio setup on this site somewhere though I can't find it at present.

---

### Post by gackt on 2009-03-02
whoa changing it to 5 and 25 is working in preview area (if you hover your mouse to the file and wait for a while)! thanks,but if i play this file in amarok it will be choppoy again Can you tell me what this number is all about? the higher the better? mine was 8 and 10.
Thanks all

---

### Post by markbuntu on 2009-03-03
> **gackt said:**
> whoa changing it to 5 and 25 is working in preview area (if you hover your mouse to the file and wait for a while)! thanks,but if i play this file in amarok it will be choppoy again Can you tell me what this number is all about? the higher the better? mine was 8 and 10.
Thanks all

It works something like this. The number of fragments and fragment size sort of determine how often the cpu is needed to be accessed to maintain smooth playback at low latency. Basically the higher the fragment size the larger each chunk of data processed by the cpu and the number of fragments is how many of these PA waits for before filling the ALSA buffer which is fixed at 64k which is about 371 msec at 44100hz/2channel/s16le. So, if you are running at 96k your buffer time is reduced by about 1/2.

It is of course way more complicated than that in reality as the kernel is also bound by other high priority activities like drawing the screen, etc that can preempt pulseaudio. Some x drivers, like the nvidia drivers are cpu hogs that do not allow tight scheduling or preemption. To accommodate them kernel writers are using low I/O scheduling times and turning off preemption which can make the audio skip since pa cannot access the kernel/cpu in time to refill the alsa buffer.

Compiz can also cause problems like this since it uses indirect rendering through the cpu.

That, and some crappy alsa drivers are currently causing serious issues with real time audio playback on some recent distro releases.

There was a big discussion about this on the PA mailing list around Feb 22-28 or so if you want to read about it yourself.

---

### Post by gackt on 2009-03-05
Thanks but i dont really get it.. changing the value to various number did not help...and i'm getting frustated not to be able to play high quality music...

---

### Post by diablo75 on 2009-03-05
You said in your OP that you are able to play back FLAC by opening them with VLC, is that correct?

---

### Post by gackt on 2009-03-05
> **diablo75 said:**
> You said in your OP that you are able to play back FLAC by opening them with VLC, is that correct?

Yes i can play flac (large file) with two ways; hover my mouse over the file and wait for a while.. or using vlc with porting to Jack (this is smoother than amarok but still dont sound smooth enough for me)

---

### Post by ramjet_1953 on 2009-03-05
Like Marcbuntu said in his reply, if you are using Compiz, did you try turning it off?

Compiz can affect many things taht are processor intensive.

Regards,
Roger:D

---

### Post by gackt on 2009-03-06
> **ramjet_1953 said:**
> Like Marcbuntu said in his reply, if you are using Compiz, did you try turning it off?

Compiz can affect many things taht are processor intensive.

Regards,
Roger:D

i'm not even using compiz anymore since it crashed my warcraft.. so is this just a matter of low spec of my laptop?? (dual core 1.8, mem 1 gig)

---

### Post by markbuntu on 2009-03-06
I think it is more of a kernel scheduling issue myself.

---

### Post by gackt on 2009-03-10
So what must i do.. i tried to configuring the number but the audio still choppy. Thanks

---

### Post by markbuntu on 2009-03-10
In the /etc/pulse/daemon.conf there are more lines you can play with.
You can uncomment these and play around with the nice level(the ; is a comment indicator, just remove it):

; high-priority = yes
; nice-level = -11

You can try folling around with these but you might get a crash without a real time kernel.

; realtime-scheduling = no
; realtime-priority = 5

You can try changing this to speex-float-1 and disable remixing.
; resample-method = speex-float-3
; disable-remixing = no

You can change the rate here.

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

Also, Are you sure your sound card is capable?

---

### Post by gackt on 2009-03-11
Thanks. I'm using laptop lenovo y410 with of course on board audio ^^. But (i hate to say this) it works perfectly with same model of laptop using windows instead of ubuntu.

---

### Post by Artemis3 on 2009-03-11
Did you try different players? If it sounds good elsewhere the problem lies in the player. Try with Totem or VLC.

---

### Post by TekNullOG on 2009-03-14
Processors don't really matter for sound quality. Personally sound ***** up depending om your sound card and the drivers available. Based on my experience, Pulse crashes all the time on an external sound card but runs perfectly on a cheap internal.

---

