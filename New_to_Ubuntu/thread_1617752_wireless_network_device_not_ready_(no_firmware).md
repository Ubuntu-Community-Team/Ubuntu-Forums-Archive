---
title: "wireless network device not ready (no firmware)"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by shadowgodd on 2010-11-09
ok i dont know how to fix this and im pretty much giving up i got other crap to do today and no time to screw with this... im running Ubuntu 10.10 maverick meercat on a HP mini 110 i have no clue what my driver is or how to find it thru Ubuntu i know i will most likely need that info too plz tell me how to find it and i will let you know exactly what it is ive tried activating both Broadcom B43 and STA they dont work please im getn really sick of computers!!!

---

### Post by walt.smith1960 on 2010-11-09
I have a Broadcom based PCMCIA adapter (AirForce One/Linksys). I just clicked system ->administration -> additional drivers and installed the offered choice.  It didn't work right away but did after a restart.  If you've already tried this sorry to waste your time.

---

### Post by lkraemer on 2010-11-09
Well, this shouldn't be hard.  

You need to first find out how/where the Wifi is toggled ON/OFF.
By a Switch, or CNTL F2, or some other method.  Make sure it is "ON".
(If it is working in Windows, leave it on and exit.)

Then go here and read the tutorial.
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=Howto%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=Howto%3A+Broadcom)

The first thing to try is in Posting #6.  Connect via Ethernet Cable,
and Update the system.  Then go to your Hardware Drivers and Enable
B43.  That should get the firmware, and you should be able to use the
Wifi.

If that fails start down the Tutorial and post the output of each
Terminal Window (Console) command.

lk

---

### Post by anewguy on 2010-11-09
Ok, I don't know squat about the HP mini 110, so I have to ask a dump question - are we sure this is a Broadcom adapter?  From the no firmware message it sounds like it, but I wouldn't know without seeing the device list from the PC.

Dave ;)

---

### Post by okudasai on 2010-12-02
I have the exact same problem. I beilive im running  dell inspirion, not sure of the model number. The OS was wiped by some idiot so I decided to install UBuntu (as I did not have the Vista CD, and had heard good things about Ubuntu as it is). Wired connections work, but the wireless does not. I have decided to install the Additional Drivers that one of the posters was talking about. Hopefully It will work as said.

---

