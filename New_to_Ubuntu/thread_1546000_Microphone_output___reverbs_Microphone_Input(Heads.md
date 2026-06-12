---
title: "Microphone output   reverbs Microphone Input(Headset)"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by mojo risin on 2010-08-04
Hello,

I have got following problem. I am using a headset for talking to somebody on the internet or recording my voice. While the sound is working well on both speakers and headsetphones , the microphone output is what makes problems.

The problem I have is that for every (about)second I utter a sound(word/syllable), it gets doubled, not just fainlty echoed but more like a  double (reverberation). This creates a problem in such that I can't have any conversation with anybody since this double output is hard to understand. I tried so far to to update my alsa, although this did not make any differences. I did not expect too much of an update either though, because I think it is not primary a problem of sound, but rather of the microphone input processing.

I have not found any relevant topic towards this problem yet. I upoaded some data from the terminal procedure for troubleshooting sound , (I am uploading it so you know my system and related items) and I also have uploaded an example of my issue(a wav done in terminal compressed as a tar.)

---

### Post by ajgreeny on 2010-08-04
I presume you have checked that this is not simply the sound from speakers being picked up by the microphone and then sent round the system again, ie feedback.  Normally that would just cause typical feedback screaming, but I just wonder.

Try listening with headphones so that the sound is not coming from speakers and can not be picked up by the mic.

---

### Post by mojo risin on 2010-08-04
Hi, I am using a headset. (which has two seperate plugs: one for the mic and one for the speakers of headphones) The sound isn't coming from the laptop speakers but rather from the headphones. The mic  hardly ever pics up sounds from speakers as I found out before(for example if you hold the mic close to a radio speaker it will hardly pick up any sound) Also the output(the doubled output) is also true for those who hear me on their laptops(via skype)

[IMG]http://a.imageshack.us/img440/5947/68064197.jpg[/IMG]similar to this.

---

### Post by bosyber on 2010-08-05
So as we found talking about this on skype, it is exactly the same problem as this:
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg25810.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg25810.html)
... same hardware, but sadly, also without any answer.

---

### Post by mojo risin on 2010-08-05
ok now I have got a new bigger problem!.
I was working in windows for a while restarted the laptop to go to ubuntu, and did the daily update. since then I don't have any sound at all.

[http://www.alsa-project.org/db/?f=467f38960634739c61c5b03c3e070ee14dc9fb70](http://www.alsa-project.org/db/?f=467f38960634739c61c5b03c3e070ee14dc9fb70)

---

### Post by mojo risin on 2010-08-05
Thankfully to soundcheck my sound works again. properly. my original problem how ever remains .

---

