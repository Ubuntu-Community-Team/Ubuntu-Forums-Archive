---
title: "wifi not working with Dell inspiron 1501"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by christoforever on 2006-12-05
hey guys i just installed edgy eft on this new inspiron 1501 amd dualcore i just got. Only it doesent recognize the dell card. Has anyone else had these problems, or know of a workaround to fix it?

---

### Post by jlapier on 2006-12-06
Hey Chris - you need to use ndiswrapper to get the wireless to work in the 1501 - try these instructions for the e1505 (uses same drivers, worked for me) [http://ubuntuforums.org/showthread.php?t=297092&highlight=1501](http://ubuntuforums.org/showthread.php?t=297092&highlight=1501)

- Jason

---

### Post by wool on 2006-12-06
i just changed the driver to be used R140747.EXE or what is applicable to you 1501

---

### Post by redDEADresolve on 2007-01-22
I made an easy to follow visual guide for setting up wireless and what not on the Dell 1501


[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)
or use the link in my signature

---

### Post by Ronirvol on 2007-02-04
I followed the proceedure for wifi on Dell 1501 with 6.10.   Everything seemed to be going well until I was near the end at "sudo ndiswrapper -m".   I then got an error- Couldn't add module alias at line 720.  I completed the last couple of steps but didn't get a light.

I'm afraid that if I completely reinstall 6.10 and repeat the proceedure I will make what ever mistake I made again.   Could I recover by repeating certain steps?  Are there any suggestions for how to check if everything has been done correctly at some mid-point?   Any suggestions would be appreciated.

---

### Post by Ronirvol on 2007-02-07
My wifi light is now on, and my browser works wirelessly.  I suspect that I resolved some problems by entering the three ndiswrapper commands which I copied from another post.

ndiswrapper -ma
ndiswrapper -mi
ndiswrapper -m


When I enter: ndiswrapper -l
It now returns:
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

Oddly, however, my light never came on util I went back in Windows and accessed my wireless network.  When I returned to Linux, I was surprised that my light was on, and I was able to access.  When I enter "sudo iwlist scanning" it still returns that it doesn't support scanning, and no scan results.  I suspect that the ndiswrapper, or something else is able to read some of the setup that was done in Windows.  I would be interested in any comments about this.

---

### Post by redDEADresolve on 2007-02-16
Function button Fn and F2 turn on and off your wifi card.

---

