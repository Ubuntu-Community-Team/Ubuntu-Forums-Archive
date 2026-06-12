---
title: "First total lockup"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-14
Though I didn't get the "blue screen of death," I had my first total lockup with Ubuntu, for which I can think of no explanation, as I was reading a document while listening to a Fleetwood Mac song when it came to a sudden, screeching halt. The only thing strange was when the CD-ROM drive ran into a bad sector on the Fleetwood Mac CD, where it froze with the classic stuck noise, and the computer totally locked up at the same instant . . . strong evidence for cause and affect? As I could not get any response from the keyboard or mouse, I was forced to shut it down using the manual power switch. I cringed doing it, wondering what disaster would come of it (bad memories from my Windows days). It booted back up again and seems to be okay, but it would really help to know what actually happened. Are there any tests I should run on the OS? Is there a Linux version of "control alt delete" to get to a task manager or something to prevent having to just cut the power?

---

### Post by SteveDee on 2011-04-14
> **TCMGO said:**
> ...As I could not get any response from the keyboard or mouse, I was forced to shut it down using the manual power switch. I cringed doing it, wondering what disaster would come of it (bad memories from my Windows days). ...but it would really help to know what actually happened....

You should avoid stopping a computer by disconnecting the power (if this is what you did) as the hard disk may still be spinning, and the "disconnect" may not be clean. However, pressing (and holding) the front panel power button for about 8 seconds (until you hear the computer stop) is generally quite safe.

Now that you have the computer running again, take a look at the logs for any clues as to what happened around the time of the crash...most likely cause is that your computer hates Fleetwood Mac (...only joking!).


Edit: Useful Link: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by sam123 on 2011-04-14
First try Ctrl+Alt+Bksp. This restarts the x-server.

If that fails to work, while holding down Ctrl+Alt+PrintScreen, press R, E, I, S, U, B one after another. This will do a safe reboot.

For more information, see [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by TCMGO on 2011-04-14
I thank you all for replying.  I held down the front power button until it finally turned off.  I am not sure where the log is, but I will look for it.  I will remember the keyboard steps given.

---

### Post by SteveDee on 2011-04-14
> **TCMGO said:**
> ... I am not sure where the log is, but I will look for it...

On Ubuntu its menu System > Administration > Log File Viewer

---

