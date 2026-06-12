---
title: "No sound in Intrepid in VirtualBox"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by metasolaris on 2009-04-04
Hi
The loudspeaker icon on my desktop has a no entry symbol on in. I have no sound at all.
Thanks

---

### Post by billgoldberg on 2009-04-04
> **metasolaris said:**
> Hi
The loudspeaker icon on my desktop has a no entry symbol on in. I have no sound at all.
Thanks

You need to install the guest additions.

---

### Post by mikemac on 2009-04-05
> **billgoldberg said:**
> You need to install the guest additions.

I have the same problem, and my Guest Additions are installed. I'm running a Dell Inspiron 1721 (AMD). On LSPCI, the audio device is listed as an ATI Technoligies Inc SBx00 Azalia (Intel HDA).  Have sound working fine on Ubuntu (8.10).

---

### Post by RedSingularity on 2009-04-05
In virtualbox right click your OS and go to the audio tab.  In there check off "enable audio".

---

### Post by mikemac on 2009-04-05
That's been done. Have tried using the Host Audio Driver ALSA and OSS. Tried both Audio Controllers AC97 and SB16,with no change.

---

### Post by mikemac on 2009-04-07
Bump:confused:

---

### Post by Cybie257 on 2009-04-07
> **mikemac said:**
> That's been done. Have tried using the Host Audio Driver ALSA and OSS. Tried both Audio Controllers AC97 and SB16,with no change.

Host and Guest are Linux? If so, you may be having an issue with shared audio. I'm sure there's a better term for it, but the only way I have been able to successfully get audio in both guest and Host is to set the Host computer to use PulseAudio. Seems to be the only true multi-tasking audio system that I have used. Without Pulse Audio, I would always get a "can't load audio, something something..."

Pulse Audio, when working correctly, works really good. Updates lately seemed to have fixed a lot of issues with crackling noise and such. 

give that a try and see what happens. :)

-Cybie

EDIT: PS-> I've had best luck using the AC97 Vbox Audio Driver

---

