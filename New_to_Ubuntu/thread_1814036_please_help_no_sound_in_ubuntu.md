---
title: "please help no sound in ubuntu"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by cye05 on 2011-07-28
waiting for sound system to respond This is the error i am getting after i updated my 10.04 linus. one thing that may be useful is when i restarted my machine after the update i couldn't load my video card and had to start in safe mode. i then went and manually downloaded my video card as i did when i first installed the system. i now have my video card at the right resolution but now i have no sound. when i click on sound prefences i get this error waiting for sound system to respond. I am running the operating system through an hdmi connection and it was working fine before the update. when i do lspci i get this for my audio.
_________________________________________________________________________
 01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
    Subsystem: nVidia Corporation Device 0828
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fe97c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
________________________________________________________________________
alsamixer doesn't seem to realize the card exists as it only lists defualt and ati. 
please help i cant find any material on this and i really don't want to reinstall lol.

---

### Post by cye05 on 2011-07-28
Well I'm sorry to waste your guys time i was able to trouble shoot it. apparently i just had to go through the same process i went through to get my card to work in the first place. this is the website with the solution to this problem.[http://ubuntuforums.org/showthread.php?t=1668173](http://ubuntuforums.org/showthread.php?t=1668173) thank you slimb:D.

---

