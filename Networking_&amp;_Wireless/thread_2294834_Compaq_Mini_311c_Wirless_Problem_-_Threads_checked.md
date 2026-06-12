---
title: "Compaq Mini 311c Wirless Problem - Threads checked!"
date: 2015-09-13
forum: Networking &amp; Wireless
---

### Post by ahmed39 on 2015-09-13
Dear Ubunto experts,

I'm a new comer to Ubunto where I liked its  simplicity but unfortunately the wireless was working before making the  update but afterwards the button wasn't working anymore!

I hate waiting and that's why writing the thread was my last option after I checked the article with the same topic before here:
[http://ubuntuforums.org/showthread.php?t=2138489](http://ubuntuforums.org/showthread.php?t=2138489)

I followed the steps and the update but the scan failed as well, then I referred to the guidelines here:
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

Unfortunately  with no clue as well, where I found that the recognized wireless card  for my compaq should be usb but the one I have is PCI so I found some  geegs recommendation stating I should install ndiswrapper but I couldn't  install it at all as I'm used to the exe format in windows for  installing programs but here i don't know the way of installing programs  after extracting them where it always involves the commands through  terminal, so I will be eagerly waiting for your help and you can find in  the following link as well the wireless info of my pc which resulted  during the performed last steps, it was larger than the limit of 19 kb,  it's around 25k!
[http://www.mediafire.com/view/qx6fz2d2lx2i656/wireless-info.txt](http://www.mediafire.com/view/qx6fz2d2lx2i656/wireless-info.txt)

Regards
Ahmad

---

### Post by chili555 on 2015-09-13
> b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not foundLet's install the firmware. Please obtain a temporary internet connection by ethernet, tethered or whatever means possible, open a terminal and do:```
sudo apt-get install firmware-b43-installer
```After it is finished, detach the connection, reboot and tell us if the wireless is working.

---

### Post by ahmed39 on 2015-09-20
Now it works, Thanks a lot, it was a nightmare!

---

