---
title: "Headphones/Christmas"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by atngplusultra on 2008-12-25
While I'm at this: all who celebrate Christmas, have a great day.

Anyway, relevant question:
I've done ***every reasonable fix*** trying to get PulseAudio and ALSA to cooperate, and I've got sound, but I really want my headphones to work, and they won't. This is 8.10 running on a 1.5-year-old Toshiba Satellite A135-S4677.

Reloading alsa is a bad idea, because then, aplay -l will not find my soundcard at all, and, just, generally, I'm looking for a fix that doesn't involve failing the soundcard altogether, because I've got just about everything working on this computer at the moment. (although I guess I don't really know if I don't have Skype up.)

Editing alsa-base never seems to do anything.

I guess no one really knows any good solutions, seeing as no one works with this computer at all.

---

### Post by Dark Aspect on 2008-12-25
> **atngplusultra said:**
> While I'm at this: all who celebrate Christmas, have a great day.

Anyway, relevant question:
I've done ***every reasonable fix*** trying to get PulseAudio and ALSA to cooperate, and I've got sound, but I really want my headphones to work, and they won't. This is 8.10 running on a 1.5-year-old Toshiba Satellite A135-S4677.

Reloading alsa is a bad idea, because then, aplay -l will not find my soundcard at all, and, just, generally, I'm looking for a fix that doesn't involve failing the soundcard altogether, because I've got just about everything working on this computer at the moment. (although I guess I don't really know if I don't have Skype up.)

Editing alsa-base never seems to do anything.

I guess no one really knows any good solutions, seeing as no one works with this computer at all.

Merry Christmas,

Have you tried OSS? Does it work with any other sound configuration unrelated to ALSA/PulseAudio? Also what kind of Earphones are they?

---

### Post by Raynman37 on 2008-12-25
Hey Merry Christmas to you too!

I know you say you tried all the reasonable fixes, so you may have tried all of these things, but I followed these directions to get my headphones to work:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Who knows, you may have done them all already, but I know I've missed one little step before and the whole operation goes down the tubes.  Let's hope it was something simple like that! :)

---

### Post by Toshibawarrior on 2008-12-25
Well, mostly Toshiba is not very friendly with Linux, at least on some models that use Atheros and Intel hardware. As I’ve stated before I own a Toshiba Satellite A135-S4527, and I must add it is a very nice laptop for the price. But with Ubuntu it tends to get a little freaky.

First off, the sound is extremely low or non-existent, and if you use the common fix found in other blogs and forums, chances are the headphones won’t turn off the internal speakers when playing sound. Well, I have just the thing for you!

Simply fire up a Terminal and type:
```

gksudo gedit /etc/modprobe.d/alsa-base/
```

Once inside that document that will open go to the very bottom and type this in:

```
option snd-hda-intel model=lenovo
```

Remove any other "option" you've added previously and make sure this one sits at the very bottom.

Now hit “Save” and close gedit. Now check that in Sound Control (double click the speaker icon on the notification area) and make sure HDA Intel (Alsa Mixer) is selected as the playback device, and that the PCM and FRONT levels are all the way up. Also check that the Headphones switch (in the Switches tab) is ticked. Reboot and you should have sound!!!…but a very harsh and tinny sounding one though!…

To fix this issue you must play around with PulseAudio…and since I’m gonna reinvent the wheel here you can check [this great tuitorial psyke83 published!]("http://ubuntuforums.org/showthread.php?t=789578&highlight=unnecessary+files")

I hope this helps. I believe both of our laptops have the same hardware, so it should work just fine.

---

### Post by atngplusultra on 2008-12-25
thanks for replying guys.
> **Dark Aspect said:**
> 
Have you tried OSS? Does it work with any other sound configuration unrelated to ALSA/PulseAudio? Also what kind of Earphones are they?

I'm not certain what you mean by "tried"; I mean, the times that I've tried completely purging my system of PulseAudio, I'd try falling back on ALSA, because that's the only other thing that's worked. so, I guess the real answer would be no.
These headphones are a pair of Sony MDR-V150s, so, a good normal 3.5mm jack connection (and the sound through them is really beastly, and they DO work, so I know they're not the problem)

> **Raynman37 said:**
> 
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Who knows, you may have done them all already, but I know I've missed one little step before and the whole operation goes down the tubes.  Let's hope it was something simple like that! :)

We'll see what it is. I *had* tried that guide before, but, it still did nothing. :/ Thanks for your input, though, I'll keep trying all these things, maybe something'll change in the future

> **Toshibawarrior said:**
> Well, mostly Toshiba is not very friendly with Linux, at least on some models that use Atheros and Intel hardware. As I’ve stated before I own a Toshiba Satellite A135-S4527, and I must add it is a very nice laptop for the price. But with Ubuntu it tends to get a little freaky.

....

To fix this issue you must play around with PulseAudio…and since I’m gonna reinvent the wheel here you can check [this great tuitorial psyke83 published!]("http://ubuntuforums.org/showthread.php?t=789578&highlight=unnecessary+files")

I hope this helps. I believe both of our laptops have the same hardware, so it should work just fine.

straight up, I wish it did, but, as I said, I've tried it, and as far as I can tell, it does nothing. Perhaps, though, I've been doing it wrong, and if Toshiba hardware DOES complain with ubuntu as much as you say it does, then that's only more reason to believe that this is not the most profitable fight to be fighting.

---

### Post by Toshibawarrior on 2008-12-25
> straight up, I wish it did, but, as I said, I've tried it, and as far as I can tell, it does nothing. Perhaps, though, I've been doing it wrong, and if Toshiba hardware DOES complain with ubuntu as much as you say it does, then that's only more reason to believe that this is not the most profitable fight to be fighting.

I do have everything working 100% in Ubuntu...including sound. I just had to use the steps I showed you above.

In fact my laptop works better under Ubuntu than under Vista.

Remember to use "model=lenovo" not "3stack" or any other.

I'm sorry this haven't worked out for you, but you might need a break. Relax and do something else then come back and try again...that's what always helps me get through Linux-Toshiba discrepancies.

And if you've fiddled with PulseAudio and or sensitive ALSA files, you may have rendered your audio useless...Make sure you haven't deleted anything important.

---

### Post by atngplusultra on 2008-12-25
> **Toshibawarrior said:**
> I do have everything working 100% in Ubuntu...including sound. I just had to use the steps I showed you above.

In fact my laptop works better under Ubuntu than under Vista.

Remember to use "model=lenovo" not "3stack" or any other.

I'm sorry this haven't worked out for you, but you might need a break. Relax and do something else then come back and try again...that's what always helps me get through Linux-Toshiba discrepancies.

And if you've fiddled with PulseAudio and or sensitive ALSA files, you may have rendered your audio useless...Make sure you haven't deleted anything important.

sorry, I wasn't trying to make you sound wrong or whatnot, and I'm not frustrated, because this problem isn't too annoying. yet. (remember, it's only headphones, my speakers are doing fine.)

oh, but, I absolutely take breaks, really frequently actually. =P case in point, it's Christmas, why am I even on the internet?

---

### Post by Toshibawarrior on 2008-12-25
> **atngplusultra said:**
> sorry, I wasn't trying to make you sound wrong or whatnot, and I'm not frustrated, because this problem isn't too annoying. yet. (remember, it's only headphones, my speakers are doing fine.)

oh, but, I absolutely take breaks, really frequently actually. =P case in point, it's Christmas, why am I even on the internet?

I also remembered. When using the "model=lenovo" thing you should plug your headphones in while the volume is ***_unmuted_***...That way the internal speakers are going to shut up. If you plug them in while the ound is muted then everything will sound in both places...

Just a thought...

---

### Post by atngplusultra on 2008-12-25
Okay, I don't know why it took me forever to notice this, but one of the meters missing in my Volume Control is "FRONT." Ever since I went to Intrepid, it hasn't been there.
Any ideas as to why this is?

---

### Post by Toshibawarrior on 2008-12-25
> **atngplusultra said:**
> Okay, I don't know why it took me forever to notice this, but one of the meters missing in my Volume Control is "FRONT." Ever since I went to Intrepid, it hasn't been there.
Any ideas as to why this is?

Did you upgrade from Hardy?...If you did there's a huge chance that something went missing...Sometimes when you upgrade libraries get mixed up and settings go missing...That's why I always suggest installing a fresh Ubuntu...

:popcorn:

If you did upgrade, report back...and we'll see what we can do.

---

### Post by atngplusultra on 2008-12-25
> **Toshibawarrior said:**
> Did you upgrade from Hardy?...If you did there's a huge chance that something went missing...Sometimes when you upgrade libraries get mixed up and settings go missing...That's why I always suggest installing a fresh Ubuntu...
If you did upgrade, report back...and we'll see what we can do.

Well, that's mostly what this is about; I was using Hardy, where all sound worked after some struggling; after finally switching to Intrepid this month, that's when the sound wasn't right.

I just now did the model=lenovo in alsa-base thing, and that actually took away some more options, and my pavumeter didn't read things right, so I had to remove THAT line and reboot.

I really hope this isn't all a wasted effort; which is to say, hopefully, it'll work soon.

---

### Post by atngplusultra on 2008-12-25
and to amend that, there's actually no sound at all right now.
the pavumeter cannot find any output devices, and of course, can find no applications playing sound.

---

### Post by Toshibawarrior on 2008-12-25
Hmmm...weird...

As I said, I'm not fond of version upgrades...but since you already did, and i believe you don't want to reinstall Ubuntu, we'll need to work around this...

Did you use the line I gave you and removed every other "option" line at the end...If you already added some sort of option-line there you should delete it and leave only the model=lenovo one...

I'm sorry, but I haven't got this deep with ALSA ever before...I really can't tell you how to sink into ALSA's base files and stuff...

I'd really recommend doing a fresh install...but some people don't like it...

Maybe someone here knows more than me about this matter...sorry.

---

### Post by atngplusultra on 2008-12-25
oh well, no, there IS another option line, but, I have a feeling it's a tad important. i'll just keep playing with that.

other than that, it's cool, no worries about not knowing; no one knows it all. I don't think. =D

yeah, I put off upgrading for fear of things like this happening, but, that can only be done for so long, so, in the end, why forestall it and have a REAL overhaul instead of a gradual implementation of better measures? that's my thing.

so, yeah, I'm just gonna have to keep messing around. thanks for your help.

---

### Post by linux_tech on 2008-12-25
You can kill all pulseaudio without uninstalling it, in terminal:

```
killall pulseaudio
```

---

