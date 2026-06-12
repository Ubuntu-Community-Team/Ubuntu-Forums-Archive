---
title: "Of onboard sound and cpu usage issue."
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Mortus Pryde on 2009-09-04
Been a while since I was around these parts, but I have a few questions.

First of all I have a sound question. My computer is currently running on the onboard Intel 82801 High Definition Audio Controller, I regularly run Skype, Exaile and SecondLife together and experience very high CPU load, and poor quality sound in the SecondLife client program among lag issues. Could this be due to the onboard audio controller? Would it be worth my while to run a stand alone controller? Also what would you recommend if this is the case that would be equal or better quality? I have 2 open PCI slots and a 1X PCI-E slot open, What would you recommend as a good replacement? I also have a spare old Creative Labs Audigy 1 X-Gamer PCI card I could put in. Would I have compatibility issues if I do this?

As an aside question, if using the onboard sound controller is causing my high CPU usage issue, could this also be true under Vista? My girlfriend uses Vista with a more modern machine, hers is a Core2 Duo where mine is only a P4-HT, and also commonly has her CPU slammed to 100% as well.

---

### Post by LowSky on 2009-09-04
Why are you running skype, exaile, and Secondlife all together? thats alot of multitasking.

But you should post the results of you PC running all three aps.

its a simple command from terminal

```
top
```

to end the program type CTRL+C, then paste the data here for us to review. Something tells me it your using of secondlife without a graphics card (do you have a graphics card)... sound takes up very little CPU bandwidth.

---

### Post by Mortus Pryde on 2009-09-04
My graphics card is a GeForce 8800GT, and yes it is quite a bit of multitasking but here are our reasons, or at least mine, my Girlfriend used a spare laptop to play her music. We use Skype so that we can talk privately to each other while we are in SecondLife, or just working on other tasks. We also like to listen to our music to in the background while we talk.

Will follow your recomendation when I get home and see what comes up.

None the less some reading I have been doing seems to indicate that onboard audio controllers may use significantly more CPU resources than a stand alone card. This ofcourse was true back a ways because onboard sound would use the CPU to do alot of the digital processing then route it to the DAC and output, though it may well be that more modern boards are able to do this entirely within the audio controller.

---

### Post by NoaHall on 2009-09-04
Skype always takes up a lot of cpu, so I doubt it's something to do with the onboard sound card.

---

### Post by kostkon on 2009-09-04
You could try installing the new beta version of Skype, if you haven't done it already.

---

### Post by CatKiller on 2009-09-04
If you're using Pulse Audio, you could try changing its resampling method to something less demanding. Unless you've got good ears *and* good speakers, you probably won't notice the difference, although your processor might.

```
gksudo gedit /etc/pulse/daemon.conf
```

Find the *resample-method* line and change the value to *src-linear*. You may need to uncomment that line, too. There are lots of different methods you could use; *trivial* will probably make the most difference. See **man pulse-daemon.conf** for all the options.

---

