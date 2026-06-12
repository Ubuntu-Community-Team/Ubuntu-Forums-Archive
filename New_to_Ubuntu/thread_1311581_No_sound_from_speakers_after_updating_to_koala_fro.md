---
title: "No sound from speakers after updating to koala from jaunty"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by bzzzzz on 2009-11-02
I've looked around the forums and I have found quite a few people that seem to have problems with sound after upgrading to koala.  A lot of the problem seem to be with sound card, but I don't think that's my problem.

I have been trying to get linux to work with my airport express for quite some time and most recently got it working (if jumpy) with jaunty.  This involves streaming the sound from the laptop through to the airport express which is plugged into my hifi.  

After upgrading to koala pulseaudio does not seem to realise that I have any onboard speakers.  Initially I thought it would be a problem with the soundcard, but have just played a couple of songs using rhythmbox and I turned on my hifi, to find that the sound is blaring through that.  (very few jumps as well!)

When I view youtube videos the sound is also streamed to the airport express.

I'm running koala gnome version on a dell d505 1.2GHz machine with 2GB of memory.

Thanks for your help

---

### Post by camaron1 on 2009-11-02
Try uninstalling pulseaudio, it worked for me (although with a diferent setup). If it doesn't do anything just reinstall it

---

### Post by bzzzzz on 2009-11-03
Removed pulseaudio

Now I can't stream to my hifi either.

It looks as though my computer can find the sound card, but cannot find the speakers on the laptop.

The speakers work because I have another operating system on a different partition that seems to produce sound.

---

### Post by bzzzzz on 2009-11-03
Correction, pulseaudio is removed but the sound is all being streamed to the airport express.

---

