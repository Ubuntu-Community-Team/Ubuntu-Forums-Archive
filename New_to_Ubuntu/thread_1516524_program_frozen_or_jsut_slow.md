---
title: "program frozen? or jsut slow?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by MatthewVC on 2010-06-23
I'm running a bioinformatics program, Cufflinks.  It's been running for roughly 24 hours, analyzing sequence data.  I expect it to take a while, but I think it may be frozen.  At first, the program was using nearly all my CPU time, according to system monitor.  Now, it's not using any CPU, and the status is "sleeping".  Additionally, the system keeps hanging up for a second every couple of seconds.  Ie: the mouse/keyboard freezes... etc...  very annoying. :mad:     
Also, in the system monitor, under waiting channel, it says hrtimer_nanosleep.  

Is this program frozen, or is it just still going?

Thanks,

Annoyed at pausing my typing every word

---

### Post by Windows Nerd on 2010-06-23
Did it slow down your computer when you first started the program, or after it had been running roughly a day? 

Did it slow down now that the process "went to sleep" (when it changed to the sleeping status from active or whatever) ? 

Scott

---

### Post by MatthewVC on 2010-06-24
It was fine at first.  It's just gotten slow since sleeping (and yes, it's still running..... grr)

Thanks,
Matt

---

### Post by sanderd17 on 2010-06-24
How is your memory used? If it uses a lot of swap, it's possible that the CPU activity just falls down and the only activity left is writing thing from swap to ram and back.

Just a possibility but I had this a couple of times with some calculations.

---

### Post by MatthewVC on 2010-06-24
So my computer crashed, and when i started it back up, everything was still open and cufflinks was still running???  That seems odd to me, but this is my first Ubuntu crash.

Before the crash, I was using about 90% of my RAM (5.8GiB), and 50% of my swap.  Since the reboot, It's running ~25% (and rising slowly) of my RAM and 12 GiB (70% of my swap).

---

### Post by MatthewVC on 2010-06-24
any thoughts?

---

