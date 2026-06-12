---
title: "Kino and /dev/raw1394"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by expatCM on 2009-06-27
I am trying to capture from my video camera.  I get an error message 

“The raw1394 module must be loaded and you must have read and write access to /dev/raw1394”

So I looked in /dev/ but I cannot find raw1394.

I ran lspci and the following was included in the listing so I know that the firewire card is found

01:07.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


If it helps, I am running 64 bit Jaunty. 

Can anyone please tell me how to get the raw1394 module to load?

---

### Post by expatCM on 2009-06-27
I have accidentally solved this one by using a different fireware port. No idea why that should be so effective ........

I also found this link which may help out someone else
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

---

