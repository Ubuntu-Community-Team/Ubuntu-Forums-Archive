---
title: "Trying to understand linux sound devices and record sound"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by jnbr on 2009-04-12
OK, asking this again in beginners talk as I don't think I'm putting enough information in to get an answer when I ask elsewhere.

I am trying to understand how sound works in linux, specifically in Ubuntu with my laptop. Now to my, probably naive, view my laptop has a soundcard, a speaker and a microphone. When I want to record sound I should be able to record from the microphone or direct from a source sent to the sound card; so if I want to record a WAV file to an MP3 I should be able to play the wav file, run the recorder and select either microphone or sound card (or something similar)

Hoewever what happens is that when I run xvidcap or audacity it asks for an input sound device which seems to default to /dev/dsp or ask for me to type in a source but what would that source be? /dev seems to contain dsp and adsp and a range of other things which I have no idea what they mean, while /dev/snd contains; controlC0, hwC0D0, pcmC0D0c etc (again I have no idea what that means)

So I look at the ALSA mixer to see if that helps; it contains the following devices;
[LIST]
[*]  Master (presumably the main output volume)
[*]  Headphones (OK makes sense)
[*]  PCM (nope no idea what that is)
[*]  Front (??? front what?)
[*]  Front Mi (must be a microphone as putting the control up gets feedback)
[*]  Mic (already set to max, but doesn't feedback)
[*]  Mic Boos (boost? why does this exist in addition to mic)
[*]  Capture (capture what, has a record box which is checked)
[*]  Capture (again, so presumably it's different but I didn't understand the first one let alone the second)
[*]  Digital (digital? it's a computer! it's all digitial!)
[/LIST]
and underneath that five check boxes marked;
[LIST]
[*]IEC958 (?)
[*]  Caller ID (why is caller ID under a volume control?)
[*]  Input Source
[*]  Input Source (again)
[*]  Off-hook (again what is this doing under a volume control)
[/LIST]

Now after a long bit of investigation I discover that I should apparently use a system called pulseaudio to handle the sound and make the /dev/dsp device take input from the combination of that mixer control. Except that whatever I do the input is only ever from the microphone. (which isn't what I want even though googling seems to suggest that everyone else gets exactly the opposite is the problem and most people have problems getting the microphone working)

Now I'm sure all the above makes sense, just not to me :-(. Can anyone out there explain what is going on with sound devices in linux, point me to a simple explanation of linux sound for beginners or even explain how I can actually record the sound that goes to my speakers rather than from the microphone. As it is I keep googling for what seems like a sensible search phrase and getting results which are just a dump of the man page and which say things like 'padsp -M name - the name of the stream to feed to pulse audio' which is fine if you have the faintest idea of what they are on about which I don't

Yours frustratedly.

---

### Post by theozzlives on 2009-04-12
On my desktop, I used a patch cable to record my tapes into MP3 files to put them on CD. Worked fine with audacity, used a tape deck and the input of my sound card.

On my laptop, I have digital inputs that I don't use, but have had problems with my built-in mic (of course I've only used it in pidgin to try to talk to people on Yahoo).

I use Alsa mixer on both computers.

---

### Post by jnbr on 2009-04-12
> **theozzlives said:**
> On my desktop, I used a patch cable to record my tapes into MP3 files to put them on CD.

So you just ran a cable from the sound output to the microphone input? I suppose I could do that but I wouldn't expect good sound quality as there would be a horrible impedance mismatch. Probably be better than what I have got so far but it just seems to me that there should be a way to record the sound that goes to the speakers rather than have to let it go to the speakers and then back via the microphone.

---

### Post by Macchi on 2009-04-12
I've been also trying to understand the intricate drivers and settings for audio. Ufortunately I did not manage yet to configure audio for Skype and Wine on a EEE 900- Thanks for any hints.

---

### Post by markbuntu on 2009-04-13
This might be what you are looking for


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by SunnyRabbiera on 2009-04-13
> **jnbr said:**
> 
[LIST]
[*]  Master (presumably the main output volume)
[*]  Headphones (OK makes sense)
[*]  PCM (nope no idea what that is)
[*]  Front (??? front what?)
[*]  Front Mi (must be a microphone as putting the control up gets feedback)
[*]  Mic (already set to max, but doesn't feedback)
[*]  Mic Boos (boost? why does this exist in addition to mic)
[*]  Capture (capture what, has a record box which is checked)
[*]  Capture (again, so presumably it's different but I didn't understand the first one let alone the second)
[*]  Digital (digital? it's a computer! it's all digitial!)
[/LIST]
and underneath that five check boxes marked;
[LIST]
[*]IEC958 (?)
[*]  Caller ID (why is caller ID under a volume control?)
[*]  Input Source
[*]  Input Source (again)
[*]  Off-hook (again what is this doing under a volume control)
[/LIST]


It goes like this:
Master: The main volume of the system
Headphones: self explanatory
PCM: PCM usually is extra boost in sound volume, it stands for Pulse code modulation.
But its use varies per system, it sometimes acts as master volume on some systems
[http://linux.about.com/cs/linux101/g/pcmlparpulsecod.htm](http://linux.about.com/cs/linux101/g/pcmlparpulsecod.htm)
Front: This one also adds extra volume boost, its usually another boost to the main volume but again varies per system.
Front Mic/ Mic/ Mic boost: usually Microphone boost/ volume
Capture/ Capture 2: again varies per system, its sometimes associated with Mic volume though.
Digital: Digital output signal, for digital speakers and such (the default signal of a PC is actually analog not digital as you would expect)

The IEC958 entry I am unsure of
Caller ID: I think this is mainly for systems with dial up, I do know most dial up clients for linux come with a caller ID and this is probably a leftover of that era.
Also might have relations to VoIP (Voice over internet provider) clients, but this is a wild guess.
Input source: perhaps extra mics, I am unsure...

---

### Post by nwadams on 2009-04-13
> **SunnyRabbiera said:**
> It goes like this:
Master: The main volume of the system
Headphones: self explanatory
PCM: PCM usually is extra boost in sound volume, it stands for Pulse code modulation.
But its use varies per system, it sometimes acts as master volume on some systems
[http://linux.about.com/cs/linux101/g/pcmlparpulsecod.htm](http://linux.about.com/cs/linux101/g/pcmlparpulsecod.htm)
Front: This one also adds extra volume boost, its usually another boost to the main volume but again varies per system.
Front Mic/ Mic/ Mic boost: usually Microphone boost/ volume
Capture/ Capture 2: again varies per system, its sometimes associated with Mic volume though.
Digital: Digital output signal, for digital speakers and such (the default signal of a PC is actually analog not digital as you would expect)

The IEC958 entry I am unsure of
Caller ID: I think this is mainly for systems with dial up, I do know most dial up clients for linux come with a caller ID and this is probably a leftover of that era.
Also might have relations to VoIP (Voice over internet provider) clients, but this is a wild guess.
Input source: perhaps extra mics, I am unsure...

Seems to be covered pretty well. However a few additions/changes. For my laptop (dell xps m1330) i have two headphone jacks so the volume channels are front and surround for the respectively. As well what you guys have called digital happens to reference my internal mic. 

recording sound out...hmm. Well i'm not 100% on soundcapture but i'm sure there is some software. Worst comes to worst you can take a cable from your headphone out to your mic in and record through that channel (one of your capture channels i think)

---

### Post by SunnyRabbiera on 2009-04-13
well like I said it varies per system, currently on my spare box I triple boot between XP/ Ubuntu and Opensuse.
In Ubuntu the master volume is Master, but in Opensuse its PCM.
Actually right now my spare computer has become my primary as I play around with it a lot these days.
Linux brought life back into her

---

### Post by Didius Falco on 2009-04-13
Just to add a little bit I dug up on the **IEC958**. This is all from the glossary from [http://www.sweetwater.com/expert-center/glossary ]("http://www.sweetwater.com/expert-center/glossary")

> **[FONT=verdana, arial, helvetica][SIZE=2]IEC958 Part-4[/SIZE][/FONT]** 
A digital interface protocol that is used to transfer digital audio data between professional digital audio equipment such as [PCM]("http://www.sweetwater.com/expert-center/glossary/t--pcm") and DAT mastering recorders, [MDM]("http://www.sweetwater.com/expert-center/glossary/t--mdm") recorders and other equipment. This protocol is most commonly known as [AES]("http://www.sweetwater.com/expert-center/glossary/t--aes")/[EBU]("http://www.sweetwater.com/expert-center/glossary/t--ebu"), but IEC958 Part-4 is the actual name for it. Two channels of digital audio are carried on a single line. An [XLR]("http://www.sweetwater.com/expert-center/glossary/t--xlr")-type connector and a shielded cable is typically used. More recently a two-line standard has come in to play as more people are working with [24/96]("http://www.sweetwater.com/expert-center/glossary/t--24/96") material.For those (like me) wondering what the IEC part means:

> **[FONT=verdana, arial, helvetica][SIZE=2]IEC[/SIZE][/FONT]** 
Abbreviation for the [International Electrotechnical Commission]("http://www.iec.ch/"). Founded in 1906 the International Electrotechnical Commission is a global organization that prepares and publishes international standards for all electrical, electronic and related technologies. They are responsible for organizing and establishing standards that are employed in all sorts of electronic equipment. This includes things as fundamental as establishing what are now common electrical unit terms such as [Hertz]("http://www.sweetwater.com/expert-center/glossary/t--Hz"), Gauss, Weber, etc. A few other standards they've done that are relevant to us are the IEC [time code]("http://www.sweetwater.com/expert-center/glossary/t--timecode") standard used by many DAT machines, the IEC power cable connection, which is the most common type of removable power cord connector used in our industry, and the set of standards known as [IEC958]("http://www.sweetwater.com/expert-center/glossary/t--IEC958"), which define digital audio transfers between equipment.

---

### Post by JohnLM_the_Ghost on 2009-04-13
> **jnbr said:**
> if I want to record a WAV file to an MP3 I should be able to play the wav file, run the recorder and select either microphone or sound card (or something similar)

This sounds a bit wrong...
You simply don't (re)record something you already have recorded... like WAV files.

WAV files can simply be encoded to MP3s, with no dealing with soundcard whatsoever. (except of course you cannot play them without one, but it is not required for encoding)

---

### Post by jnbr on 2009-04-14
> **JohnLM_the_Ghost said:**
> This sounds a bit wrong...
You simply don't (re)record something you already have recorded... like WAV files.

WAV files can simply be encoded to MP3s, with no dealing with soundcard whatsoever. (except of course you cannot play them without one, but it is not required for encoding)

Not quite what I was trying to do, I am not trying to convert an audio format that I already have but I used a poor example to illustrate the simplest case of what I was trying to do, i.e. to record from one application to another.

What I am trying to achieve is to record some videos from the internet which need to be watched several times over (guitar tuition videos, hence the fact that they require reasonable sound quality and warrant watching several times as they are educational stuff). Now I could watch them 'live' each time but bandwidth problems mean that's not really feasible. So far I'm using xvidcap but have the sound problems described, to reduce that to a simpler problem while I invesitigate I have been playing WAV files and using audacity or xvidcap to try to rerrecord them without going via the microphone. However it is at this point that I discover I really don't know what is going on with linux sound.

---

### Post by JohnLM_the_Ghost on 2009-04-14
hmm... there might be a bunch of problems with those programs...

by default in Ubuntu (8.04 and newer) sound is controlled by PulseAudio which is a sound server (it grabs output of different applications then mix them) what sends sound to it's back-end driver, which is ALSA.

Well problem might be that xvidcap uses OSS sound system (both PulseAudio and ALSA have emulation modes, but it might still run into problems)

And I can't quite recall what Audacity did, but I remember it had some funny behaviour (like trying to grab ALSA directly, probably cause it used to be normal behaviour before PulseAudio)... I might look into that later.

Also it comes to my mind that JACK was built to stream audio between applications. Neither xvidcap or audacity is compatible as far as I know, but it can wrap around OSS (hence also xvidcap) and can stream to a JACK compatible software, like Ardour. But setting up JACK is a little bit of pain.

But on other hand... videos (and other content) from internet is still downloaded to cache. So it is very likely that you can copy them from cache and watch them locally without rerecording anything. (might involve some video conversions though)

Anyway, here is some short descriptions on audio on Linux.
**PulseAudio** is a sound server what deals with separate applications routing their output to back-end driver (either ALSA, OSS or other PulseAudio server over network)
PulseAudio is a fairly new program still not in wide use (I mean most other distros don't use it)
more info in links
[http://en.wikipedia.org/wiki/Pulseaudio]("http://en.wikipedia.org/wiki/Pulseaudio")
[http://pulseaudio.org/]("http://pulseaudio.org/")

**ALSA** is a sort of sound driver suite.
So in short it is sound driver.
More technically it is an abstraction layer for applications, to deal with different kinds of sound cards.
It is still quite common to use ALSA directly, and not by a sound server such as PulseAudio, so many applications still try doing that.
[http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture")
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

**OSS** is also a sound driver system, similar to ALSA, however it is more low-level and regarded as obsolete (even though it has been recently developed further).
OSS is the one what accesses /dev/dsp and therefore can deal with one application only, but ALSA's, PulseAudio's and JACK's OSS emulators/wrappers (and even newer OSS implementations) try to overcome this.
However as OSS is older and more portable, some software still use OSS for sound (like xvidcap).
[http://en.wikipedia.org/wiki/Open_Sound_System]("http://en.wikipedia.org/wiki/Open_Sound_System")

**JACK** what I mentioned already, is also a sound server, but it has emphasis on inter-application streaming, instead of application-to-driver streaming.
[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit]("http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit")
[http://jackaudio.org/]("http://jackaudio.org/")

---

### Post by jnbr on 2009-04-29
Well after all that I now understand (a bit) more about linux sound but still couldn't get it to record from anything other than the microphone. Having said that I found an alternative solution through a firefox plugin to record the flash video stream directly.

---

