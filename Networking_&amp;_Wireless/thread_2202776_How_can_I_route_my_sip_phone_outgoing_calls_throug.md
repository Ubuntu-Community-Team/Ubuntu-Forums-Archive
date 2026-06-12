---
title: "How can I route my sip phone outgoing calls through a usb attached mobile phone?"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by nigelclegg on 2014-01-31
Hi,

I have a Grandstream DP715 dect phone which is attached to my Ubuntu PC and is set up for incoming calls through Sipgate. What I would like to do is route outgoing calls through my usb attached mobile phone which has an unlimited call plan.

Is this possible?

---

### Post by ian-weisser on 2014-01-31
Depends on the phone. Some phone USB ports are data only. You may not be able to send your audio streams over USB.

Once you get your phone figured out, the Ubuntu side is pretty easy. You merely need to create Pulseaudio sinks for USB devices (one each direction) for your SIP application to connect the audio streams to.

---

### Post by nigelclegg on 2014-01-31
Hi Ian,

I have a Nokia N8 connected. I found [this]("http://symbianism.blogspot.co.uk/2008/10/linux-and-symbian-pc-suite-alternatives.html") information which I'm hopeful means that the phone can communicate with Ubuntu no problem.

---

