---
title: "Loose Internet on every boot"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by IndyBob on 2007-03-10
I just started playing with Ubuntu this past week so I have a lot to learn.  To get onto the internet every time I log into Ubuntu 6.10 I have to go to the terminal do sudo modprobe ne and reset my network/ethernet card and then I can get Firefox to work.  If I go into Administration-Networking when I first log in it no longer shows my wired connection, but once I do the Modprobe ne then it shows.  Do I need to get a new network card?  Mine is old and came from Comcast back about 8 years ago and is a generic Windows card.  Any suggestions would be appreciated!

---

### Post by yabbadabbadont on 2007-03-11
You might try adding the module you are loading to /etc/modules so that it gets loaded automatically at boot time.

---

### Post by Mr. C. on 2007-03-11
Or even:

```
alias eth0 ne
```

to /etc/modprobe.conf

MrC

---

### Post by IndyBob on 2007-03-11
Thank you both for your info, however since I am a real newbie to this, could you go into more details on how to do either response.  I know I would go into the terminal, but what from there?  I really get confused on the commands at this point.

---

### Post by yabbadabbadont on 2007-03-11
Open a terminal window.  Then either "sudo gedit /etc/modules" and make the change I suggested, or "sudo gedit /etc/modprob.conf" and make Mr C's suggested change.  (or both ;))

---

### Post by IndyBob on 2007-03-11
Thanks for the info.  I tried doing both and it still will not recognize the card at boot and I have to go to the terminal and do the modprobe ne then I check dhclient and all is well, so I guess my best bet is to go get a new network card as an easy fix.  Should I go back in and take out those entries I just put in?

---

### Post by Mr. C. on 2007-03-11
I don't think you need to get a new card, but that's your call.  Either of the suggestions should have worked.

Can you show the output of dmesg, as a file attachment here?

MrC

---

### Post by IndyBob on 2007-03-11
Will try posting info from dmesg in a few, on XP system now.  Have new card ready to install, but will pass on info first to see if that would help.  I might not have done everything correctly as earlier suggested, but I think I did.  Will post results in just a few.

---

### Post by IndyBob on 2007-03-11
Well, since I am new to Linux, I tried to make results of dmesg as a PDF file and it's too big to send per forum.  How do I make it a zip file?

---

### Post by Mr. C. on 2007-03-11
```
dmesg > dmesg.out
gzip dmesg.out
```

---

### Post by IndyBob on 2007-03-11
Thanks, someday I may learn all this with everyone's help.

Here's results of dmesg

I think it's attached.

---

### Post by Mr. C. on 2007-03-11
The card is being recognized:

```
[  177.360048] ne.c: ISAPnP reports Generic PNP at i/o 0x220, irq 5.
[  177.360471] ne.c:v1.10 9/23/94 Donald Becker (becker@scyld.com)
[  177.360475] Last modified Nov 1, 2000 by Paul Gortmaker
[  177.360483] NE*000 ethercard probe at 0x220: 00 e0 29 4a eb 84
[  177.360960] eth%d: NE2000 found at 0x220, using IRQ 5.
[  187.286487] NET: Registered protocol family 17
[  187.822038] eth0: no IPv6 routers present
```

It looks like it is being detected after about 177 seconds post boot. I would have expected this to have occurred nearer to the 99 second time frame, which is the last of the messages prior to those above.
```

[   99.455212] NET: Registered protocol family 10
[   99.455436] lo: Disabled Privacy Extensions
[   99.455642] IPv6 over IPv4 tunneling driver
```

 Was this the result of a modprobe? 

MrC

---

### Post by IndyBob on 2007-03-11
The only way I can get onto the internet is to do a modprobe ne first thing I log on or it's dead in the water.  Do you want me to run the same test without first doing modprobe?

---

### Post by Mr. C. on 2007-03-11
Something doesn't make sense.  Your /etc/modules file  should look like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ne
```

This will cause the ne to be loaded upon startup.  This happens very early in the boot stage.

Can you confirm that your file looks like the above?

MrC

---

### Post by IndyBob on 2007-03-12
For now I think I have the problem solved.  I went out and bought a new network card and it works on boot that I can get onto the net without doing modprobe ne everytime.

Thank you all for all your assistance.  I am sure I will be asking more questions later for another problem.

---

