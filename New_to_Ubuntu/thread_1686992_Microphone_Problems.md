---
title: "Microphone Problems"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by hockeygoalie5 on 2011-02-13
Hello, this is my first post on the forum and hopefully it goes well.

I'm using an HP Pavilion with a built-in microphone. The microphone  worked on first install but stopped. I looked up the problem and edited  gstreamer-properties, after a restart this worked. However, after some  time the microphone had stopped working. It was not detecting any sound,  as if it isn't there at all. Editing gstreamer and putting it back to  what I had then restarting fixes this issue. I've looked everywhere for a  solution and never found one. This problem extends from Mangler, to  Skype, to the sound properties panel so I'm sure it has nothing to do  with the program. I don't know what you would need to help debug the  issue, so post back if you want more information. This seems to happen most whenever I adjust my microphone volume, but not always.

Thanks in advance,
hockeygoalie5

---

### Post by yeats on 2011-02-13
When you open a terminal and do

```
lspci
```

You you see your microphone listed?  You can add details to each device by doing

```
lspci -vv
```

---

### Post by hockeygoalie5 on 2011-02-13
Thanks for the quick reply. Found two audio devices and one I recognised as my speakers, so this must be it.

```
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 3642
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin ? routed to IRQ 16
    Region 0: Memory at f2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

---

### Post by yeats on 2011-02-13
You might try what's suggested in the last post on this thread:

[http://ubuntuforums.org/showthread.php?t=988474](http://ubuntuforums.org/showthread.php?t=988474)

---

### Post by natex on 2011-02-13
Hello,
Before you go about mucking around in /etc/modprobe.d/ I'd recommend you go to System>Preferences>Sound>Input and see if the microphone is recognized there. Perhaps it is muted? Alternatively, open alsamixer from a terminal and see if the microphone is muted there.

natex

---

### Post by hockeygoalie5 on 2011-02-13
That did the trick, yeats, thank you!

---

### Post by Phelixfil on 2011-03-30
I'm having similar problems and have tried entering the commands you suggest in terminal but I'm really not sure what to make of the information that appears.  I see lots of references to ATI technologies but nothing that resembles the Logitech mic I have connected.  Any suggestions gratefully received.

---

