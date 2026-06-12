---
title: "IDE conflict?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by nnjond on 2009-12-13
Hi,
I'm not sure what my problem is but I used a stick to install my os on my older IDE drive, running to one IDE socket on my motherboard. I have added a second internal hdd; an SATA with a necessary  converter to a 2nd IDE socket on my motherboard. Thus i keep my important files on a new, separate internal hdd. However with my present connecting cables, my only option is to add my IDE dvd drive to the  ribbon cable running to my 1st hdd. When i attempt this, os load halts at a flashing cursor. I can only use my dvd drive by unplugging my SATA drive and using the 2nd IDE socket.

---

### Post by kansasnoob on 2009-12-13
OK, my guess is that you're connecting the DVD drive to the far end of the ribbon cable which is actually the Master connector. Those ribbon cables have one connector that connects to the MOBO and generally about 10 to 12 inches from it another that is Slave and another 6 inches or so at the very end another that is Master.

The Hard drive must be on the Master! Of course it often looks more "neat & clean" to have the cable "center" connector go to the hard drive then the one on the end go to CD/DVD because in most configurations the optical drive resides above the hard drive, but the hard drive needs to be on the "end" or Master connector.

> Color coding of the connectors is used to make it easier to determine which connector goes with each device:

    * Blue: The blue connector attaches to the host (motherboard or controller).
    * Gray: The gray connector is in the middle of the cable, and goes to any slave (device 1) drive if present on the channel.
    * Black: The black connector is at the opposite end from the host connector and goes to the master drive (device 0), or a single drive if only one is used.


[http://www.storagereview.com/guide2000/ref/hdd/if/ide/confCable80.html](http://www.storagereview.com/guide2000/ref/hdd/if/ide/confCable80.html)

---

### Post by CharlesA on 2009-12-13
Not that it's any help, but I'm so glad I moved away from IDE devices, cable management is a major pain with IDE cables.

Make sure the device is in the correct slot (see above) and that the jumpers are set correctly.

---

