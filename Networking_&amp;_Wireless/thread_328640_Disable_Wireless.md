---
title: "Disable Wireless"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by FlashOmega on 2006-12-31
Alright well this is a weird one... but before I begin I want to thank everyone who takes the time to read this.  I am not exactly a noob to linux but im by no means an expert and I try to help everyone I can (currently my annoying roomate which is the reason for this post... well not annoying roomate but his computer is annoying me) all that being said I really like using linux and would still be using it if it wasnt for the on going help from people on this forum...

MOVING ON....
Got a really crappy annoying disconnecting (in windows as well) wireless card in my roomates computer... lets call him carl (cause its his name).

So I ran a big *** cat5 to his room and thought my pains would be over... but i cannot disable the card.. its a pci card.. of unknown origin... and I dont feel like taking it out and storing it properly incase they want it in the future.  So whats happening is in the System>Networking it shows wireless/eth/dialup... makes sense... but the wireless if already off... but its still connecting wireless to random networks around.

I dont mind pulling the module for it all together... but dont know how.

Any thoughts cause im out of ideas (yes tried kicking it)

---

### Post by ritalin_kid on 2006-12-31
if you want to remove the module for your wireless, try:

```
sudo modprobe -r <module name>
```

---

### Post by W3ird_N3rd on 2006-12-31
I'd suggest opening /etc/modprobe.d/blacklist and add the module the card uses instead of removing it.

---

### Post by FlashOmega on 2007-01-01
So you are saying if I add the proper module for the wireless card it will seperate it from the wired ethernet connection so that I may disable it seperatly?

If so .. or either way... how would I identify which module to add or remove depending on what I end up doing.

---

### Post by W3ird_N3rd on 2007-01-01
No, you add it to the blacklist so it can't be used anymore, that way you could disable the wireless card.

What module? Euhm, good question :p. What chip does the wireless card have?

---

### Post by FlashOmega on 2007-01-01
I have vitually no information on this card lol.... I do know that the ethernet card is integrated into the motherboard... and I know the motherboards specs so maybe I can eliminate all other options.... ill get back to you on how I fair out

oh wait... for that I would need to find out how to get the module list.  So that I could figure it out


Thanks for the help


40 minutes later:
Thanks everyone for your help... I got angry and just pulled the dam card out.... cause I couldnt disable atho0 properly
didnt know how to make 

ifconfig ath0 down

permanent... the card sucks anyway and its a desktop pc so it doesnt need wireless

---

### Post by W3ird_N3rd on 2007-01-02
Ah, atheros, if you would have said that immediately..

Hmmm.. What about opening up the device manager, look for the wireless card and check "info.linux.driver" in the advanced tab?

---

