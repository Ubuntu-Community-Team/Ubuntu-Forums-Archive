---
title: "Maya44 USB Inputs"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by BRASE on 2011-06-21
Hi,

I have been using ubuntu for a few years now. I have been searching/reading these forums for a while now too but this is my first post on the ubuntu forums.

I have just bought a Maya44 USB and  i am trying to get the inputs to work under Ubuntu i have been searching but have not found a solution.

The card works for output but not for input alsamixer says there are no capture devices. When i first tried the card the output was low so i had to turn it up. I think the inputs just need to be turned up but there is no volume controls for the inputs in alsamixer. I want to use the card in mixxx and also with JACK/QJackctl. Could someone please help me with a solution. Like how to turn up the inputs or add the correct controls in alsamixer or any other suggestions.

Hope this makes sense.

All help is greatly appreciated.

Thanks

Adam

---

### Post by krzakx on 2011-08-14
Hi! I have similar problem. I can record using MAYA44 but the input signal is very low.
When I record to Ardour2 the signal is very low. 

[IMG]http://screenshooter.net/data/uploads/su/ps/dvui.jpg[/IMG]

The Output is OK

[IMG]http://screenshooter.net/data/uploads/or/gj/lino.jpg[/IMG]

Any solution?

---

### Post by Tropcon on 2011-08-14
BRASE, welcome to the forums! And greetings to you also, krzakx.

Now, down to business. It makes it difficult to be a total help, because I don't own a Maya44 USB. However, I do have a few ideas.

First off, just to make sure it's not something obvious, the Maya44 USB has line-level inputs. So make sure that you're input is coming from a powered source.

Secondly, and most likely, your audio path is as follows (unless I am quite mistaken): Hardware -> ALSA -> PulseAudio -> JACK -> Ardour.
That is how my plain old Ubuntu 11.04 routes audio when using JACK, and my guess is that your OS behaves in the same way (judging by the screen-shots).
It is interesting to note (and this is the important part) that when recording audio using JACK, nothing I do in ALSAMixer has any effect on the volume of the audio I am recording (really strange, I know.) However, Pulse will control the signal just fine. (Someone care to tell me how (and why) they do that? I never use Pulse Audio on my multimedia OS because it just gets in my way, so I'm still a little fuzzy as to how it works. I'm using a SoundBlaster Live!, by the way.)

Anyway, my suggestion is to get a good PulseAudio mixer (there's one in the Software Center called "PulseAudio Volume Control") and play around with that instead of ALSAMixer.

Let me know if you find anything. I've taken an interest in this subject.

     Tropcon

---

### Post by kamilek_snk on 2011-11-07
Unfortunately, there is'nt configuration which work with any software.

That must be problem with driver, it seems like there is'nt DC in inputs.
I will try solve that problem on University of Technology in my town.
Be turn on!

---

