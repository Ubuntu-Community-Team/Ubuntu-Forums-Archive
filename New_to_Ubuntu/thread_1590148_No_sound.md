---
title: "No sound"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by MHC on 2010-10-07
I have just bought a new PC with Ubuntu Lucid pre-installed. I have no sound, either from the internet or saved files. I have checked System>Preferences>Sound to ensure Output volume and Input volume are unmuted, and the speaker icon in the top toolbar is unmuted. What other check can I do to find the setting I have to change to get sound?

---

### Post by Mark_in_Hollywood on 2010-10-07
Does the crescendo play on Ubuntu start up?

If yes, the sound card is good, but other problems need help.

or

If NO, then then is this is dual OS 'puter? That is, can you boot into windows and hear a sound?

If YES, then the problem is in the Ubuntu OS. If NO, the sound card could be bad.

As you say this is a NEW 'puter does the sales outlet provide support? Have you asked their tech support?

Lastly, please give the name of the manufacturer, Dell, Lenovo?

The model number, CPU, name of the sound card/chip makers.

---

### Post by MHC on 2010-10-07
No, the crescendo does not sound, and this is a mono OS PC, so I can't try Windows. 

It sounds like it is more technical than just a few settings I can change - I will contact the vendor. Thanks for your help.

---

### Post by Boring on 2010-10-07
When you look under 
**System** -> **Preferences** -> **Sound** there should be a tab for **Hardware**.  See if there is more than one audio device.

---

### Post by sandyd on 2010-10-07
> **MHC said:**
> No, the crescendo does not sound, and this is a mono OS PC, so I can't try Windows. 

It sounds like it is more technical than just a few settings I can change - I will contact the vendor. Thanks for your help.

run
```

alsamixer
```
in terminal

make sure all sliders are at the top

---

