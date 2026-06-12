---
title: "2 audio cards, only 1 recongnized"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Malalo on 2009-01-26
Hi there,

I'm at a loss here... 
I have 2 audio cards for music recording/mixing. One is a DeltaDiO 2496 and the other an Audiophile 2496, both from M-Audio.

Here is the result of "cat /proc/asound/cards" :

```
 0 [M2496          ]: ICE1712 - M Audio Delta DiO 2496
                      M Audio Delta DiO 2496 at 0xdf80, irq 21

```

The Audiophile isn't recognized at all...

Any ideas ?

---

### Post by Malalo on 2009-01-26
Perhaps if I add the result of "lspci | grep audio" :

```
02:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
02:0a.0 Multimedia audio controller: Device 0001:0000 (rev 01)

```

---

### Post by alzie on 2009-01-26
I didn't know this was possible, however I think this link should help you: [http://www.backports.ubuntuforums.org/showthread.php?t=922860](http://www.backports.ubuntuforums.org/showthread.php?t=922860)

I hope this helps.

---

### Post by Malalo on 2009-01-26
Thanks for that, Alzie. However, I have 2 cards, and one is not recongnized by ALSA, so I can't even start with what the post you gave me is talking about...

---

### Post by Malalo on 2009-01-27
Anyone else has an idea ?

---

### Post by Malalo on 2009-01-27
Bump-bump
I really need these 2 cards working together...

---

