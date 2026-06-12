---
title: "[SOLVED] I Ruined NdisWrapped can some one help me get it going again?"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by E_K on 2007-09-21
Well i was trying to use the native linux driver for my dell 1390 wireless card, 

so i was following [this]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated") how to...

when i got to this part   ....   sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb

i got an error saying

```
(Reading database ... 105445 files and directories currently installed.)
Preparing to replace bcm43xx-firmware 1.3-1ubuntu2 (using .../bcm43xx-firmware_1.3-1ubuntu2_all.deb) ...

Unpacking replacement bcm43xx-firmware ...
Setting up bcm43xx-firmware (1.3-1ubuntu2) ...
Note that you need to DISABLE ndiswrapper and wifi-radar for this driver
to work properly! You can do this by removing the ndiswrapper driver.
Use `sudo ndiswrapper -l' to identify the driver.
Then run `sudo ndiswrapper -e <driver>' to remove it. You may also need
to remove the file /etc/modprobe.d/ndiswrapper
```

So i followed what it asked me to do.....

and not to my amazement what-so-ever the wireless stopped working

so now it keeps giving me this error, so i cant install those drivers, and i can install the old ones again.. im a bit of a noob when it comes to this

i tried the original howto that got it working [here]("http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1390") 

Please can some one help me, i have no wireless connection any more, and I really dont want to reinstall like i did last time...... [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

