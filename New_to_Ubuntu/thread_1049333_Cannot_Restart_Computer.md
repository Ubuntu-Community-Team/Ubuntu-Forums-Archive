---
title: "Cannot Restart Computer"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by abah01 on 2009-01-24
Hi Everyone,

Would appreciate some assistance on my problem; I am using Ubuntu with Acer Aspire One (8Gb SSD). After some work (I know next to nothing abt Ubuntu) I managed to get Ubuntu running with Virtualbox hosting Windows XP in the AA1.

Two weeks later, after smooth performance of Ubuntu (I even got the mic working), I then set up a wireless connection in my home upon which I tested a wireless connection with my AA1 for the first time, but failed to get a connection. I then turned off the AA1.

After that, I have not been able to turn on my computer anymore. The message on the computer mentions (there are many lines but these are the main ones)
1. Unexpected inconsistency; run fcsk manually
2. fcsk died with exit status 4
3. Then it recommends to peform fcsk oin maintenance mode with the root system mounted in read-only mode

I get into maintenance mode as requested (by keying in root password) however a string of messages appear 'bash: no job control in this shell', and bashes with 'command not found' at the end.

I am then stuck in root directory and unable to move on. Typing in control-D restarts the system and the same thing happens all over again. So I am perpetually stuck in the start-up cycle.

I hope my explanation is clear; can anybody help please??? I truly hope I do not have to reinstall..thank you.

---

### Post by cmnorton on 2009-01-24
I would boot with a live Ubuntu or recovery CD (like Knoppix), and then run fsck on the unmounted hard-drive on which you installed. 

I still cannot remember what to answer fsck on an in-boot recovery. Better to do it the long way. A live CD will usually list out the hard-drives as icons you can mount. From that you'll know what parameters to give to fsck at an X-term (command line).

---

### Post by abah01 on 2009-01-24
Thanks for the reply. I will decipher what you have suggested to do and try to execute accordingly. Will keep this line open for now...thank you

---

### Post by butch616 on 2009-01-25
My laptop is doing the axact same thing as you described,same messages.I am completely new to linux and ubuntu so i'm not touching anything till I'm sure.What worked for you if anything?

---

