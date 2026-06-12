---
title: "Sound still coming from laptop speakers even with headphones"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-09-10
Hey all,

I just installed Ubuntu 8.04 on my laptop and for some reason the sound continues to come out of the laptop speakers even when something's plugged into the headphone jack (headphones or external speakers).  It still comes out of the headphones/speakers, too, though.

I looked under System > Preferences > Sound, but didn't know what any of the items there were...was I on the right track?  Suggestions?

---

### Post by The Thug on 2009-09-10
I had the same problem on my laptop running 9.04 and found the solution using this thread...

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by talsemgeest on 2009-09-10
> **The Thug said:**
> I had the same problem on my laptop running 9.04 and found the solution using this thread...

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)
Yep, you will have to open up the volume control and make sure that "Headphone" is ticked under the "Switches" tab.

---

### Post by diablo75 on 2009-09-10
> **talsemgeest said:**
> Yep, you will have to open up the volume control and make sure that "Headphone" is ticked under the "Switches" tab.

I've had this problem happen to me before and I don't have a "headphones" option available in the Switches tab (and I have all available switches enabled in Preferences).  Though a restart solved the problem, I think it was caused by trying to use Virtualbox and some other sound producing application (like VLC) at the same time.

---

### Post by Wataru8675 on 2009-09-10
Okay, so what do you do if your speaker codec isn't listed in the output of " zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz"?  I found the section he was talking about, but mine isn't there.  I got 2 codecs from the first command.

> ==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 272

==> /proc/asound/card0/codec#1 <==
Codec: Generic 11c1 ID 1040
Neither of them are there, nor any derivitives close to them, and I've scanned the list 3 times now.

Also, I don't even HAVE a "Switches" tab...much less a headphone selection under it.

---

### Post by Wataru8675 on 2009-09-12
Any suggestions?

---

### Post by LewRockwell on 2009-09-12
> **Wataru8675 said:**
> Hey all,

I just installed Ubuntu 8.04 on my laptop and for some reason the sound continues to come out of the laptop speakers even when something's plugged into the headphone jack (headphones or external speakers).  It still comes out of the headphones/speakers, too, though.

I looked under System > Preferences > Sound, but didn't know what any of the items there were...was I on the right track?  Suggestions?

there are two types of jacks commonly associated with headphones and external speakers/audio-devices

one type disconnects internal speakers so that the headphones enable one to listen without disturbing others(most everyone reading this has experienced these devices previously)

the other type does not provide any disconnect and is normally utilized where such selectability is not necessary

for example, almost every laptop with internal speakers has the disconnect type

desktop computers with separate sound cards will normally not provide the disconnect type on the speaker out jack(also note that sound cards may well have one "signal output"(non-amplified) and one "speaker output"(various amplification depending on MFG and design)

desktop computers with motherboard integrated sound capacity AND a speaker output jack on the rear of the machine AND a headphone jack on the front of the machine will sometimes have the disconnecting type jack on the front of the machine so that is easy to just plug headphones in to silence the machine(since the external speakers would normally be connected at the back of the machine

.

---

### Post by Wataru8675 on 2009-09-12
Thing is, my jack is the silencing type when I'm running Windows.  It's an Ubuntu thing. =)

---

