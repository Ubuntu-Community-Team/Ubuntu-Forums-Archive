---
title: "Maverick freezes more often and for longer"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by frogo on 2011-06-27
Hi, 

I'm starting to have more problems than I have time to try fixing... am a bit worried now. 

I'm running 10.10 on a Dell e4310 laptop. I installed that from deb. Since I installed there's been occasional short freezes. Some applications would stop responding for a few seconds. Sometimes some window would become shaded in grey. This happens a lot with gedit when trying to save or open a file. Firefox windows will become greyed more often, sometimes with Firefox windows that are open in the background. Usually, after a few secs things kick back in motion and then there's a series of keyboard strokes and mouse clicks in rapid succession. 

I usually have a JVM running and I probably have more things than I need running in the background. Until recently, this sort of experience, however, had been very distinctive of a Windows XP experience for me... I had never experienced noticeable lags on this machine with 10.04. 

Anyway, now I just had the first major freeze with the machine just stopping to respond and I had to hard reboot after waiting for a few minutes. 

Is this know and is there something a newbie like me can try doing?

many thanks
p

---

### Post by dFlyer on 2011-06-27
Can you use disk utility and check your hard drive for bad sectors?

---

### Post by frogo on 2011-06-27
> **dFlyer said:**
> Can you use disk utility and check your hard drive for bad sectors?

That's the GUI thing right? 

Well, i tried, apparently I can't copy and paste so here's what I make of it

1. 'Check file system' gives an error, it says the device is busy and the details read "Device is mounted and no online capability in fsck tool for file system"

2. The Smart Data status reads green and says 'Disk has a few bad sectors'. Looking into it, I get:
- Self assessment says passed
- Self-tests all fail, it says: Failed (Read)
- 39 bad sectors

Regarding attributes:
- A warning on 'Reallocated sector count' (ID 5), the value given is 33 (for a 36 threshold) -- honestly I have no clue what this is about
- A warning on 'Current pending sector count', value is 6, threshold 0...

Is the last thing why it won't run the disk check? is it because it already is running it?

3. Could the machine be overheating too? It says 40C, the fan goes on and off regularly though.

---

