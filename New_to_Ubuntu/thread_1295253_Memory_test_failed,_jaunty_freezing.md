---
title: "Memory test failed, jaunty freezing"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by Viva on 2009-10-19
My jaunty started freezing occasionally today(even the keyboard stopped working after a freeze). I thought it is a kernel problem, so I booted in to windows where even the mouse stopped working(It is working in jaunty). So, I did a memory test and I got thousands of errors after 1024 MB. I'm assuming that one of my RAM failed(I have 2 1024 MB sticks). I can get some new RAM in a few days, but I have some important work to do and I need my computer without freezing. Would removing the damaged RAM help for now? How do I know which one is broken?

---

### Post by mcduck on 2009-10-19
> **Viva said:**
> My jaunty started freezing occasionally today(even the keyboard stopped working after a freeze). I thought it is a kernel problem, so I booted in to windows where even the mouse stopped working(It is working in jaunty). So, I did a memory test and I got thousands of errors after 1024 MB. I'm assuming that one of my RAM failed(I have 2 1024 MB sticks). I can get some new RAM in a few days, but I have some important work to do and I need my computer without freezing. Would removing the damaged RAM help for now? How do I know which one is broken?

Yes, that sounds like you have a faulty RAM (although there's also a small possibility that the problem is in the motherboard itself). And yes, removing the faulty RAM stick should fix the problem.

The only way to find out which one of your two RAM sticks is the problem you should simply remove one, run memtest, and if you get any errors switch to the other stick and try memtest again to find out which one is the problem. If both are producing errors then the problem would be the motherboard.

---

### Post by halitech on 2009-10-19
chances are, if the errors show up after the 1024 mark that it will be the ram in slot 2. Might be slot 1 but I'd more likely guess slot 1

---

### Post by mikechant on 2009-10-19
If things are vaguely logical you should be able to find a diagram for your motherboard online showing the RAM sockets as something like bank1, bank2 etc. and the faulty one should be in the higher numbered bank corresponding to the higher addresses where memtest was reporting the failure.
I'm not very well up on hardware though so this might be rubbish!

It might not seem worth it since just taking out each board in turn will work, but if you pull out and reinsert the working board there's always a possibility you might damage it and then end up with no working RAM at all.

---

### Post by Viva on 2009-10-19
From the look of it, its the dust that caused the problem. I took both the sticks out, cleaned them along with the slots. No errors showed up in the memory test this time. I'll try to play a game or some other resource intensive process to see if it freezes again, after I complete my work obviously;)

---

