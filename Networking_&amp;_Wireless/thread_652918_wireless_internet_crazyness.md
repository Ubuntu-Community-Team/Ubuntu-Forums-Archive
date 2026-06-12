---
title: "wireless internet crazyness"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by surferkid993 on 2007-12-29
I have an HP Pavilion ze4500 and I am running Ubuntu 7.10 trying to get the wireless internet working. I got ndiswrapper and wrapped the two .inf files that should make it work. Is there more that I have to do... 
wireless internet still wont work.
I read some more and found I should just use one so I tried each separately with no success.

So i decided to try a different approach I removed the drivers and tried the bcm43xx driver with the restricted drivers in Ubuntu 7.10. I think I did it right be the site I looked at didn't talk much about finding a local file for it so I just used one off the internet. That didn't work either so now I am back to asking you people. Is there something that I could do differently if I used a local file.

---

### Post by spd106 on 2007-12-31
For ndiswrapper you need one .inf and one .sys. The .sys file contains the firmware, whereas the .inf just has installation and setup information.

You can't use just any driver file with the bcm43xx driver. There is a list on the development website and it's also included in the bcm43xx-fwcutter package that the Restricted Drivers Manager installs. 
May I recommend this help wiki page for more information [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

