---
title: "ALSA and pulseaudio"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by tweaktolive on 2011-04-09
is alsa and pulseaudio present in kubuntu ?

if yes then why dont they conflict and can i also select between both the drivers ?

Please enlighten me !!

---

### Post by sandyd on 2011-04-09
> **tweaktolive said:**
> is alsa and pulseaudio present in kubuntu ?

if yes then why dont they conflict and can i also select between both the drivers ?

Please enlighten me !!

Alsa is a sound server, in fact, its the main sound server in the system. 
Pulseaudio is a sound server that mixes all the streams and routes it towards alsa. 
The main use of pulseaudio is to prevent improperly coded applications from accessing the alsa sinks directly (which will cause all other applications to be unable to use alsa).
As a result, they do not conflict, because pulseaudio feeds sound into alsa

---

### Post by tweaktolive on 2011-04-09
now what does port mean ?

please dont be technical !!

I m a newbie

---

### Post by tweaktolive on 2011-04-09
sorry i was meaning what is sound server ?

---

### Post by sandyd on 2011-04-09
> **tweaktolive said:**
> sorry i was meaning what is sound server ?
a sound server is what manages your sound (i.e. what applications output their sound to)

---

### Post by SeijiSensei on 2011-04-09
Applications don't talk to the sound hardware directly.  That would require every application to include code for all the different possible audio systems you might find on a PC.  Rather the applications send their outputs to a "sound server" which sits between them and the hardware.  The server uses the appropriate driver to talk to the hardware.

---

