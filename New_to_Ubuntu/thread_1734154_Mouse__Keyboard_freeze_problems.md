---
title: "Mouse / Keyboard freeze problems"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Bakerconspiracy on 2011-04-19
Hey,

I'm having problems with my mouse and keyboard on pretty standard ubuntu install of Ubuntu 10.10 AMD64. It seems to work fine with three harddrives running, but as soon as I add a fourth the OS goes frugal. Basically, the mouse and keyboard just don't work at all, but other processes continue running. What log files do I check for this?

I did a 
```
dmesg | egrep mouse
```
with nothing prevalent towards the hang up. Also the xorg log didn't seem to have any errors with the mouse and keyboard. Just some initialization

Do you think this could have anything to do power consumption of the last drive? 

Let me know if you want to see any logs to help!

Thanks in advance

[P.S. - I'm ssh-ing into the stalled machine right now.]

---

### Post by mörgæs on 2011-04-19
Yes, power consumption is a possible explanation. 

Does the machine work with the new drive and two of the old ones?

---

### Post by Bakerconspiracy on 2011-04-20
I haven't tried that combination yet. I could try it, but how can I determine quickly if it is stable? I think there is a stress test in System->Administration; gotta wait a bit before I restart the server though.


The keyboard/mouse start out working fine with all the drives connected, then eventually (without fail) moves into the key board / mouse lock. Sometimes it takes 15 minutes other times overnight.

---

