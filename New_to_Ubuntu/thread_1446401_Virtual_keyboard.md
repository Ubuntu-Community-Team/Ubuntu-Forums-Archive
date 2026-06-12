---
title: "Virtual keyboard"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by itsvan on 2010-04-04
HI im trying to get virtual keyboard working,,but I have no idea how to get all the sounds going,,,im rather a noob to all this midi stuff so any clear and easy steps would be helpfull...:guitar:

---

### Post by abeisgreat on 2010-04-04
You'll *probably need JACK sound server running, you should be able to install it with
```

sudo apt-get install jack qjackctl

```
QJackctl is a utility to manage/configure Jackd, and I know it is needed when using an external midi keyboard, so i'd guess that since virtual keyboard is just a virtual midi keyboard you'd need to use it. 

Again, I'm not sure about this, but I'd also think you'd need a synthesizer, as I don't think virtual keyboard has one built in. 
```

sudo apt-get install zynaddsubfx

```
Once you get that installed, you'll need to load up qjackctl, the keyboard, and the synth, then connect the keyboard to the synth (it's in one of qjackctl's windows), and you should have audio.

This is only a guess, it's what I had to do to get an actual midi keyboard working. Hope this helps.

---

### Post by itsvan on 2010-04-04
HI thank you very muhc,,wel so far i haven't gotten VIRTUAL KEYBOARD to work,,i got ZYNaddsubfx to work,,and its pretty awsome i must say,,but i still cant find how to connect virtual with JACK,,if anyone can add on to this to help thank you

---

### Post by itsvan on 2010-04-04
Also if anyone knows a Program that lets me play real sounding files,,like real Piano, real organ etc..that be very helpfull too

---

### Post by mechro on 2010-04-04
> **itsvan said:**
> HI thank you very muhc,,wel so far i haven't gotten VIRTUAL KEYBOARD to work,,i got ZYNaddsubfx to work,,and its pretty awsome i must say,,but i still cant find how to connect virtual with JACK,,if anyone can add on to this to help thank you

Try this howto...

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

---

