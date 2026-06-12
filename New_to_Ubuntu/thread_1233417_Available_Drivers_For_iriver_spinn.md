---
title: "Available Drivers For iriver spinn?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Howard Roark on 2009-08-06
I want to know, if anyone out there has an iriver spinn; and if you do how did you get around the driver availability issue? (cause I don't believe iriver makes one for Ubuntu).

---

### Post by LowSky on 2009-08-06
from what I'm reading it should connect automatically as a media storage device, in other words, as if its a flash drive, and then you can just dump files into a folder on the device.

[http://www.anythingbutipod.com/archives/2008/10/iriver-spinn-review.php](http://www.anythingbutipod.com/archives/2008/10/iriver-spinn-review.php)

> Transferring Media / Software

The iriver SPINN is user selectable MTP and MSC. MTP is selected by default and what you will use if you are using any music subscription services or MTP based media players like Windows Media Player. MSC on the other hand, will be better if you are using a different OS or if you would like to use the SPINN more like a flash drive, hopping between OSes or running programs directly from the player over USB. 

---

### Post by Howard Roark on 2009-08-06
Thanks, but you know I dont remember either option (MTP or MSC) being presented to me When I pluged iriver in! it just kinda hung there. I still have the mini cd driver in the cd player and of course that isn't recoginized but I cant even get spinn to show up on my desk top!

---

### Post by LowSky on 2009-08-06
with it plugged in open a termnial and type this command and post the outcom back here, thanks

```
lsusb
``` BTW its a lowercase L

---

### Post by Howard Roark on 2009-08-06
Bus 001 Device 002: ID 04f9:01f9 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Howard Roark on 2009-08-06
Bus 001 Device 002: ID 04f9:01f9 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by LowSky on 2009-08-06
found this, it might be a simple user selcted thing from the menu

[http://www.iriverinc.com/support/spinn/spinn_support.aspx](http://www.iriverinc.com/support/spinn/spinn_support.aspx)
> How do I check my connection mode?
**Menu-> Set -> Advanced -> Connection type 

if you can change it to MSC

---

### Post by Howard Roark on 2009-08-06
Sorry I also just realized that MTP or MSC are settings i need to select on spinn. I was thinking that it was something I had to select on Ubuntu. I just realized that was wrong (It does not help much but still)

---

### Post by Howard Roark on 2009-08-06
It (Ubuntu) just does not seem to recognise my spinn and I cant figure out why? but I did switch from MTP to MSC on the spinn unit it-self!

---

### Post by ArseT12 on 2009-10-13
Hi, I have the same problem than you.
Have you find a solution?

---

### Post by Paqman on 2009-10-13
You should be able to connect the Irivier as an MTP device without any hassle. To convert videos for it you can use iriverter (it's in the repos).

---

### Post by ArseT12 on 2009-10-13
it's working!
When it was fully charged, I change the connection type to MSC(UMS) then restart it and plug it again, then I choose Power + Data and it works for me...

(sorry for my english I'm a french speaker..)

---

### Post by sg1efc on 2010-02-28
> **ArseT12 said:**
> it's working!
When it was fully charged, I change the connection type to MSC(UMS) then restart it and plug it again, then I choose Power + Data and it works for me...

(sorry for my english I'm a french speaker..)

This also worked for me, Thank you very much ArseT12, I needed to choose Power + Data.  :D

And your English is fine.  :D

Transferring songs to my Iriver SPINN is soooo much better than the constant crap I put up with for years with my Ipod Nano.   Apple sure could learn something from Iriver.   :p

---

