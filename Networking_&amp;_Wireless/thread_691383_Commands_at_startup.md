---
title: "Commands at startup"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by Baylee202 on 2008-02-08
I just as of today got my demon bcm4318 wireless card to run. (Yay for me)

But to use it I have to activate the radio in root with the two lines:

modprobe fsaa1655g

and then use 

iwlist eth1 scan

to get networks.

Is there some way to could make ubuntu do that by it self at startup so I dont have to?
And im a total newbie here so I need it spelled out if you have a solution.

Thanks

---

### Post by dca on 2008-02-08
bcm43xx...  Did you use the 'restricted drivers' provided w/ the Ubuntu install or did you use ndiswrapper and Windows driver?  Well, either way if it's the restricted drivers then it should load at boot time every time.  As far as adding a start-up script...  Lemme' look into this...

---

### Post by andb on 2008-02-08
modules added to /etc/modules will load at boot.
scripts in /etc/rc2.d/ will load at startup. starting with "S" will start, "K" will stop. They are stopped and started in an order based on the two digit number following the letter. If you must, you can put a script here, though these are usually just sym links to proper scripts /etc/init,d/

This is ugly hacking, but it will do what you want, but I'd hope this is going to be just testing and not permanant. Should be a better way. Have you tried the restricted drivers? Good luck!

---

