---
title: "Ubuntu 10.10 and modeswitch not working"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by bill.denbigh on 2010-10-11
I use a ZTE 626 USB modem to connect to the internet (and yes, i am in the wilds of nowhere!) which using USB-modeswitch 1.1.0-2 and ubuntu 10.04 works well.

I just upgraded one machine to 10.10 and it included the new modeswitch 1.1.4 which does not work, the modem is never discovered. I searched around and found that this is a bug in the latest modeswitch and if you back down to version 1.1.3 it works.

So, i have two questions, 

first, where can i find version 1.1.3 of modeswitch. I have searched and cannot find older version than 1.1.4 as a .DEB file.

second, i do have a really old version of modeswitch on my hard-drive and have been trying to load my older 1.1.0-2 version and am having real problems with it. I remove the 1.1.4 version and its data using the ubuntu software centre and it looks like it properly is removed. I then click on the .DEB file that contains 1.1.0-2 and it opens the software centre and installs it (the data seems to be automatically loaded as i never have to install that). I then search for modeswitch and the version that has been installed is the newer 1.1.4 one, not the older one i clicked on. I am confused as this computer is not attached to the internet but it seems to find the newer version from somewhere, uses it and therefore does not work.

Any suggestions or help would be gratefully accepted.

Thanks, Bill

Incidentally, the source of the information that i have so far is here:

[https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/626568](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/626568)

From reading this, i do understand that there is a problem, what was done to work around it i have no comprehension as i am a total noob, sorry...

---

### Post by Luke2891 on 2010-10-24
This isn't helpful, but I am having the same problem with an external hard drive (HP 320)

---

