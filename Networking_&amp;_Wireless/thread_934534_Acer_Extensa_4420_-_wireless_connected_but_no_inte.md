---
title: "Acer Extensa 4420 - wireless connected but no internet?"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by tone33 on 2008-09-30
Just got an Acer Extensa 4420 laptop.  I can connect to my wired connection just fine, and seem to connect to the wireless - it says I'm connected and i get the bars in the top right task bar.  But I can't get to the internet.  I get a timeout on a ping to any major url.  I've updated everything, rebooted.  Any ideas?

My wireless card is a Broadcom BCM4312

I found this site: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old)

which has what I think I need to do.  But I look for the .sh file in the folder specified below but that folder doesn't exist.

> 2 Ubuntu (all flavors) and Debian use the following command:
      sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh 



and then below that it says

> Note: If you cannot use your distribution's packages, you need to have a compiler and headers for libc installed. The reason for this requirement is that you will have to build fwcutter.

I'm assuming this means if the above folder and file were not found then do this??  But I'm not sure which compiler I need and how and what the header for libc are.  I write .net code for work so I'm not afraid to recompile whatever I need to, just not sure where to start for this particular issue.

Can someone point me in the right direction?

---

### Post by tone33 on 2008-09-30
Seems that if I disable the WPA encryption that I'm using it works fine.  so it's something with the encryption...

---

### Post by tone33 on 2008-09-30
ok so i'm now using WPA2 w/TKIP+AES and it works.  I really couldn't go back to WEP so this is acceptable to me.  For anyone else looking I found several how tos involving kernel recompile among other things.

[http://ubuntuforums.org/showthread.php?t=765448](http://ubuntuforums.org/showthread.php?t=765448)

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old)

[https://answers.launchpad.net/ubuntu/+question/30908](https://answers.launchpad.net/ubuntu/+question/30908)

---

