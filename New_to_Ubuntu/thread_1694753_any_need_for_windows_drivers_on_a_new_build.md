---
title: "any need for windows drivers on a new build?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-02-24
This may be a supremely dumb question, but I need to ask it...

I was just looking at a motherboard/cpu combo I'd like to buy from a discount computer place. It gives the link for windows xp  drivers (this isn't a cutting edge system by any means, just something for me to play around and practice building with). I wouldn't actual Need the windows drivers would I to run Ubuntu? The drivers are the Nvidia all in one driver, Realtek audio, amd cool and quiet driver and a sata raid driver - the note on the sata driver says (for system to read from floppy diskette during Windows installation).

I've installed Ubuntu on several machines but they were always used ones that had once had Windows installs, never a new, nekkid machine...

thanks

mystmaiden

---

### Post by sandyd on 2011-02-24
> **mystmaiden said:**
> This may be a supremely dumb question, but I need to ask it...

I was just looking at a motherboard/cpu combo I'd like to buy from a discount computer place. It gives the link for windows xp  drivers (this isn't a cutting edge system by any means, just something for me to play around and practice building with). I wouldn't actual Need the windows drivers would I to run Ubuntu? The drivers are the Nvidia all in one driver, Realtek audio, amd cool and quiet driver and a sata raid driver - the note on the sata driver says (for system to read from floppy diskette during Windows installation).

I've installed Ubuntu on several machines but they were always used ones that had once had Windows installs, never a new, nekkid machine...

thanks

mystmaiden
none needed.
unless you want to use RAID (dmraid), it should work out of the box.

---

### Post by seawolf167 on 2011-02-24
You should be fine without any additional drivers, though you may want to install the [Nvidia graphics]("http://www.nvidia.com/Download/index.aspx?lang=en-us") suite if you want to access all the features of your video card.

---

### Post by 3rdalbum on 2011-02-24
> **seawolf167 said:**
> You should be fine without any additional drivers, though you may want to install the [Nvidia graphics]("http://www.nvidia.com/Download/index.aspx?lang=en-us") suite if you want to access all the features of your video card.

Note that you would use the driver from Ubuntu's "additional drivers" program, NOT Windows drivers.

---

### Post by mystmaiden on 2011-02-25
Thanks everyone!

---

### Post by grahammechanical on 2011-02-25
In 2007 I built my own machine specifically because I did not want to buy a machine with Windows pre-installed. I had no problems installing Ubuntu on it. It has a Nvidia graphic card. As someone else has recommended, after installing go to System>Administration>Additional Drivers. It should list a driver for your card. You need an Internet connection to activate it. The program fetches the driver for you and installs it.

Regards.

---

