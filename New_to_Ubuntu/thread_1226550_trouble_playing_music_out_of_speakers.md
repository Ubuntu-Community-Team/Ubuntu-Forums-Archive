---
title: "trouble playing music out of speakers"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by thomas.rs on 2009-07-29
Hey everyone!

New to Ubuntu. Been installing some new programs and love it. Came across a few things one of them is that I was having trouble playing my mp3s so I downloaded a bunch of plugins and was finally successful. Now im having trouble playing anything out of my speakers. I can hear it in my headphones but not out of my speakers any ideas? Keep in mind that Im very new to this

---

### Post by Volt9000 on 2009-07-29
You said it works out of your headphones. Where do your headphones plug in? Into your speakers, or into your sound card's output?

---

### Post by thomas.rs on 2009-07-29
I plug them into the headphone jack in my computer

---

### Post by Volt9000 on 2009-07-29
Ok, so with the same jack, headphones work but speakers don't, correct?

First thing I would do is check the obvious: are the speakers plugged in, turned on, and connected properly?

It's possible your speakers may be dead, or the audio cable going to the speakers is not working. Best thing to do is take the speakers to another known, working computer and test them out there. If they don't work there either, it's a problem with the speakers.

---

### Post by thomas.rs on 2009-07-30
The speakers that arent working are the ones in my laptop. I can only listen to stuff with my headphones

---

### Post by Volt9000 on 2009-07-30
Ah, I see. Well that will certainly make them harder to diagnose!

Are you sure the speakers are turned up? Not just in Ubuntu, but also on the laptop? Some laptops have a way to mute the speakers with some funky Function+key shortcut.

Unfortunately the only other way I can think of to test the speakers out, would be to boot into another OS where the speakers are known to be working, and test them out there.

---

### Post by daimaru on 2009-07-30
> **thomas.rs said:**
> Hey everyone!

New to Ubuntu. Been installing some new programs and love it. Came across a few things one of them is that I was having trouble playing my mp3s so I downloaded a bunch of plugins and was finally successful. Now im having trouble playing anything out of my speakers. I can hear it in my headphones but not out of my speakers any ideas? Keep in mind that Im very new to this
couldnt bother reading all replies :) but try installing "PulseAudio Device Chooser" 
```
sudo apt-get install padevchooser
```go to "Applications>Sound&Video>PulseAudio Device Chooser" select "playback" tab right click and choose your speakers as output device. (do this while audio is playing, even if you dont hear it) you can set it as default under output (rightclick again)

btw probably wont work :) cheers

---

