---
title: "Kaffeine - no picture"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Jack Campbell on 2009-03-08
I've managed to install Kaffeine, it tuned the channels on my Haupauge OK, I can select channel and get sound - but no picture. Blundering around (and not sure what I clicked) I get an error panel saying "Cant Bind info Socket"

As a raw beginner in Linux, can anyone tell me what to do next?

(I've tried searching the forum for a Kaffeine how to, but so far no luck)

---

### Post by cariboo on 2009-03-08
I would suggest you use Tvtime, it is available in the repositories, as I have never had any luck getting Kaffeine to play nice with my tv tuner card.

Jim

---

### Post by Jack Campbell on 2009-03-08
Thanks Jim, I'll give it a whirl.

---

### Post by Jack Campbell on 2009-03-08
No Joy with TV Time either, Jim.
I found it, installed with Synaptic, it appears under applications>Sound & Video but when I try to run it I get a very brief app panel with a black centre that immediately shuts down again.

---

### Post by odnalro on 2009-03-08
What is the model of your TV card? How did you install Kaffeine, did you use Synaptic?

---

### Post by Jack Campbell on 2009-03-08
It's the Hauppauge 1300, Kaff installed with Synaptic.
Card has worked on an earlier computer.
This is a home build. AMD 64 Bit Dual Core.
Hauppauge Program works fine on this computer under Win XP (dual boot - Intrepid/Windows

---

### Post by Jack Campbell on 2009-03-09
Bump

---

### Post by odnalro on 2009-03-12
I have been out of ideas, but lets try some other things.
Did yout put the firmware in the "/lib/firmware" directory?
Also if you have a webcam connected to your computer try unpluging it.
Are you using the 32 bit or 64 bit of Ubuntu?, if your are using the 64 bit version of Ubuntu that might be the problem.

---

### Post by Jack Campbell on 2009-03-12
Thanks for the response, odnalro, you could well be correct about the 64 bit issue.
This particular box used to run a Pentium with Gutsy and under that config. Kaff worked fine. But I had a problem with a mem stick socket and upgraded the Mother Board to an AMD 64 Dual Core and loaded the 64 Bit version of Ibex.
I think I'll try and run Hauppauge WinTV6 in Wine. (The Haupp prog works fine under XP or Vista on this machine). Don't want to be messing about with Dual boots into Windas just for TV when everything else I want is in Linux.

---

### Post by odnalro on 2009-03-15
Jack, you can also try Me-TV. You can install it with Synaptic.
More info on [https://launchpad.net/me-tv](https://launchpad.net/me-tv)

---

