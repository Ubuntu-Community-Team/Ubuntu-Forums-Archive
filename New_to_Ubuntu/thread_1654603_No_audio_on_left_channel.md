---
title: "No audio on left channel"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Giraffemonster on 2010-12-28
Hello Ubuntu community, I'm having a problem with an audio related issue. I'm not receiving any sound at all from my left speaker.

 I know it's not my speaker, but instead, a software issue. If I connect the jack to my Ipod instead of sound card output, then my left speaker functions fine. When I'm just listening to my Ipod, the left earbud is working. When I listen to audio on my computer, the left speaker gives out no sound. When I listen to audio on my computer using my Ipod earbuds, the left earbud gives out no sound.

My hardware:
- Biostar Microatx motherboard
- Intel Celeron 2.66Ghz Single core
- 2GB DDR2 Transcend memory
- 40GB IDE Hard drive 7200RPM Seagate
- Nvidia 7300GT 512MB 128-bit
- Encore ENM232-8VIA (My Sound Card)
- Ubuntu Desktop Edition 10.10 32-bit

My motherboard does have onboard sound, but I disabled it. I have read from the comprehensive sound solutions guide, but unfortunately it didn't solve my problem.

I'll give any information needed if you ask for it, thanks for reading. I would appreciate help on this matter.

---

### Post by Giraffemonster on 2010-12-30
Alright, my left speaker functioned properly yesterday. Today though, there's no sound in my left speaker. I tried a few more steps from the Comprehensive Sound Solutions Guide, but still no luck.

I remember using "sudo apt-get install alsa-oss", I really have no idea why. I don't believe that I read it on a guide. All I know, is that I knew that an ALSA related package named "alsa-oss" existed, and how to install packages. I then just decided to use that command in the terminal, a while later, my left speaker started working.

Again, it's not working anymore, but I know that it can work. Help would be appreciated. Thanks.

---

### Post by vacc73 on 2010-12-31
> **Giraffemonster said:**
> Alright, my left speaker functioned properly yesterday. Today though, there's no sound in my left speaker. I tried a few more steps from the Comprehensive Sound Solutions Guide, but still no luck.

I remember using "sudo apt-get install alsa-oss", I really have no idea why. I don't believe that I read it on a guide. All I know, is that I knew that an ALSA related package named "alsa-oss" existed, and how to install packages. I then just decided to use that command in the terminal, a while later, my left speaker started working.

Again, it's not working anymore, but I know that it can work. Help would be appreciated. Thanks.
Have you gone into preferences/sounds and cliked onthe appropriate hardware, input, output devices?

---

### Post by Giraffemonster on 2010-12-31
Yes, I'm sure I've done that. I've even checked it in the PulseAudio Volume Control program.

---

### Post by vacc73 on 2010-12-31
> **Giraffemonster said:**
> Yes, I'm sure I've done that. I've even checked it in the PulseAudio Volume Control program.
***OK if you have ALSA mixer installed, make sure everything is turned on, not muted ,or click on the sync button so both sides are operating the same.If you don't have ALSA mixer installed, get it from thr soft ware centre***

---

### Post by Giraffemonster on 2011-01-01
Yeah, I have alsamixer already. So I went into terminal, and entered "alsamixer", and then unmuted all channels except for mic. I did that because it was producing a static noise in my right speaker.

Anyway, all of the unmuted channels are at 100, both sides. I'm not sure about this, "sync button" though. Do you mind telling me how to use it?

---

### Post by nikefalcon on 2011-01-01
My 0.5 cents:
Might be a hardware problem.I have a set of old altec lansing speakers which exhibit the same problem. There's no sound through the left speaker unless the volume knob is rotated into a certain position. Have had similar problems with headphones too.....

---

### Post by Giraffemonster on 2011-01-01
> **nikefalcon said:**
> My 0.5 cents:
Might be a hardware problem.I have a set of old altec lansing speakers which exhibit the same problem. There's no sound through the left speaker unless the volume knob is rotated into a certain position. Have had similar problems with headphones too.....

Interesting. However, I don't think it's a hardware problem. I've tested the speakers out with the output from my iPod, and it works just fine.

As of right now, my left speaker is working again for some reason. I'm sure it won't last for long though, as this happened before once and then the speaker stopped working again. I didn't even install any packages this time, nor did I reboot my computer. Weird.

And thanks for posting, it helps. :)

---

### Post by diablo75 on 2011-01-01
> **Giraffemonster said:**
> I'm not sure about this, "sync button" though. Do you mind telling me how to use it?

"Sync" simply means "Lock both channels (left and right) together, so they move as one when I adjust a level."

As for the problem you are having, I would tend to think it's a hardware issue, but with your card (the jack) itself, and not software or your speakers, as you've tested them with your iPod.

I would open the case and check for heavy dust buildup.  Take a can of air and blow the system out while the machine is off.  You might, just for experimentation, enable your onboard audio and plug your speakers into the sound jacks on the motherboard.  PulseAudio should detect and use both cards at the same time (or if it doesn't, you can easily tell it to by messing with your hardware output settings).

One other thought:

If your sound card is surround sound, that means you have:

1 Jack for Front Speakres
1 Jack for Rear Speakers
1 Jack for "Surround" speakers
1 Jack for Center/Subwoofer
1 Jack for Line In
1 Jack for Mic In

It is possible you are plugging into the Center/Subwoofer jack instead of the Front Speakers out, which would explain why you only hear sound coming from one side.

---

### Post by Giraffemonster on 2011-01-02
I've been thinking that maybe you're right, and that the sound card itself may be at fault. The left speaker has been working though, when I was using Windows XP Professional 32-bit (about 2-3 months ago).

As for heavy dust buildup, I agree that it can be a problem. I've used an air compressor to clean it out really well right before I switched to Ubuntu ( again, 2-3 months ago), which is pretty recent considering I don't do that so often. My computer attracts a ton of dust though, so it still may be the problem.

My sound card is surround sound, I can see 6 ports, and it's an 8 channel card. I have tried all the ports though, the only one which works is the one I'm using right now (Front). I forgot to mention that I'm using 2.0 speakers as well, because maybe that may help for future reference.

Anyways, switching back to onboard audio might be a good idea because I miss my left channel, however, the main reason I bought a sound card was to free system resources. I really hope there's an alternative. I might switch back though if nothing works.

Happy late new year too. :)

---

### Post by HermanAB on 2011-01-02
Howdy,

I also have one laptop where the right speaker refuses to work.  It used to work when I installed the system and it still works when I boot a different system off a USB stick, but no amount of coaxing will make the darn speaker work on the installed system.

So yeah, it happens.

---

### Post by Giraffemonster on 2011-01-05
Just going to give some more information that may be useful. I used to have this problem, in which occasionally I would have no audio at all, despite PulseAudio Volume Control and alsamixer saying that my sound is functioning. Again, no luck with the Comprehensive Sound Problem Solutions Guide. The way to solve that problem, would be to reboot and hope it works. I would have a 2/5 chance of having no audio.

It isn't really a problem now though, as it doesn't happen as often as it does now. Anyways, what that has to do with the problem in this thread, is that I was rebooting my computer, hoping I would get audio in my left speaker again like I had yesterday, and two/three days ago.

I think I had no audio twice, only audio from my right speaker twice, and then the final time I rebooted, I had audio in both speakers. Right now, I'm listening to music with both speakers. It sounds great to have that second channel.

Whenever I'm on the computer, I'm almost always listening to music whenever I'm not watching a video or playing a game. That's partially why I really want to get that left speaker functioning.

Anyway, the point of this post is to say that I can also get my left speaker working from rebooting, which is relevant to another problem I used to have, but still have occasionally. Still, I would prefer not having to reboot my computer several times in the morning to get my left speaker to work. At least we're getting somewhere though, thanks again.

Link to my thread with the old problem for reference:
[http://ubuntuforums.org/showthread.php?t=1635530](http://ubuntuforums.org/showthread.php?t=1635530)

---

### Post by Giraffemonster on 2011-01-08
So yesterday, the day before that, and the day before that, I think I may have restarted, three, maybe four times in total to get my left speaker to work. Today, eight tries and no luck.  Some days, my left speaker is functioning properly, whereas some days are like this.

Does anyone know any sort of terminal command to "restart" sound drivers? I don't really know how to restart a process. It's something I've never really had to do. Not only that, but I don't know what sort of process/program I should be looking at in the first place. If there's a quick command to do, I would look forward to trying it out. It would make things a lot quicker.

Even if there isn't a one line command to do so, I would still be interested in trying something larger, or a bit more complex. Anything helps. :)

---

### Post by Giraffemonster on 2011-01-25
Found out that it was the card, perhaps the hardware of the card to be more specific, but I'm not exactly sure. What happened was, for about a week after my last post, I've only been receiving audio from my right speaker despite being able to get audio from both speakers 50% of the time.

At the end of the week, I noticed that all of a sudden after hibernation, my left speaker was working again. With that however, all sound output was in a higher pitch. That was sort of awkward. I rebooted to see if that would help, and then, my sound wasn't working, nor was it being recognised in the graphical frontends for ubuntu. I could identify it through terminal, but nothing would really work. The card was useless.

I went into the BIOS after and enable my integrated audio again. It works just fine, 100% chance of getting sound from both speakers. Delayed posting this for a week to make sure that there wouldn't be any problems. I still have my old card inside my computer, but I'm probably going to remove it later. Don't feel like opening up my computer right now though. To conclude, it was probably just the sound card manufacturer's lack of attention to the linux kernel instead of alsa being incompatible with my sound card. I don't really think any sound card manufacturer natively supports Linux operating systems and says that it does. I marked this thread as solved, because the issue was, "fixed". Thanks for the help while it lasted.

---

