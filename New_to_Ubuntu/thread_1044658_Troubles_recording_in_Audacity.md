---
title: "Troubles recording in Audacity"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by DeLaney on 2009-01-19
I initially downloaded audacity to make some soundtracks, and get feedback on my guitar, as well as try to learn how to put music together. I could record with the settings as they were and things were fine for a bit. Then I figured I should try to get a drum beat, so I downloaded Hydrogen to create a drum beat, only to realize I can't get the drum beat to hydrogen to enter into Audacity. After an hour or so of searching, I came upon these instructions; 

[http://audacityteam.org/wiki/index.php?title=Recording_audio_playing_on_the_computer](http://audacityteam.org/wiki/index.php?title=Recording_audio_playing_on_the_computer)

I used the instructions for Linux, (ALSA, obviously) and it worked. Then I tried to put some guitar over the drum tracks and it wouldn't record the guitar. So I tried to open a fresh Audacity and then record my guitar and it failed again. I set the settings back to what I remember them being, and tried again, and still no luck (I was using OSS when recording with guitar, so I figured when I returned to OSS the ALSA settings wouldn't bother it). I've played with the ALSA settings a little bit, based off what that tutorial's told me, and I've gotten no where. Can anyone help?

---

### Post by candtalan on 2009-01-22
Maybe audacity is having trouble in connecting with the sound device in some circumstances when other sound functions are also using the sound device. I am not any expert on this, but I think audacity is a bit sensitive to this sort of thing. (?)
This may also depend on the design of your soundcard or hardware  sound chips I think.
However, I have recently helped a friend record from a problematic PC simply by using an extra connection from the sound sockets Line Out (or speakers out) and taking it not only to the speakers but also to the sound sockets Line In (not necessarily microphone in, which might also work).

This means that from one socket Speakers Out, you need two out going  connections, one going to your speakers, the other going to Line In. 

In order to achieve this, a simple method would be to use a Y junction or sharing cable. It would have typically, a 3.5mm stereo jack (male) to plug into your sound sockets Speakers Out, and also have a 3.5mm stereo socket (female) on each end of the two sharing leads.

You will then have a source available from your Line In, and Capture or recording source can be configured suitably by using the  mixer (or open Volume control etc).


hth

---

### Post by DeLaney on 2009-01-23
I'm not sure what you mean. I'm fairly noobish at this whole thing, this is really my first go at using Audacity in Linux, and it some of the subtleties are completely different. I'm not really sure why it's not working either. It worked with OSS, but it didn't after I put it back to OSS feed. Could ALSAmixer even affect that? That's the only thing I can think of.

---

