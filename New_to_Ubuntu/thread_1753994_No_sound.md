---
title: "No sound"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by bupe on 2011-05-09
Hello,

I just installed Ubuntu 10.04.2 32 bit again on my desktop PC and I have no sound however it seems that ubuntu did recognize my soundcards. How can I fix this?

Best regards,
Peter

---

### Post by bupe on 2011-05-09
I'm doing the troubleshooting guide I found [here]("https://help.ubuntu.com/community/SoundTroubleshooting") and the command

```
lspci -v | less
``` 


gives me this:

> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: ASUSTeK Computer Inc. Device 8288
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fe5f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


Which is strange as I have an AMD only system (790FX chipset with SB600 SB + AMD CPU and AMD GPU...). Why would it use Intel HDA if it's an AMD system?

---

### Post by bupe on 2011-05-09
I used the following script to generate the ALSA information package for my card:

```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh
```

I got the following URL:

[http://www.alsa-project.org/db/?f=fcaaef034bf351cefdc9ecdf3998fb7366eee66e]("http://www.alsa-project.org/db/?f=fcaaef034bf351cefdc9ecdf3998fb7366eee66e")

And this is when I realized that my headphones are plugged into my monitor that is connected to the hdmi out on my AMD card... problem solved!

---

