---
title: "wireless drivers"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by Deaia on 2007-12-05
I have a Dell Latitude D600 computer,which currently has a ubuntu 7.10 OS,and an: Intel® PRO/Wireless 2200BG Network Connection wireless card, but i haven't got any drivers to make it work. I tryed to download the driver from Intel, but can't make head or tails of the instructions. So i tried ndiswrapper, got the ipw2200 driver from previous windows documents, but i can't seem to get the wireless conection going... :(

ideas ? :P

---

### Post by csat on 2007-12-05
There are more steps on this...  Check this link and you'll figure it out.

[http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys](http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys)

---

### Post by lvleph on 2007-12-05
ndiswrapper -i driver.inf
ndiswrapper -l (This should tell you that the driver is installed)
modprobe ndiswrapper (activates driver)

sudo echo ndiswrapper /etc/modules
now put ndiswrapper at the bottom of that file. This will allow you to use that driver everytime you start the computer.

Edit: Can you see your wireless and you just can't connect? Sorry should have asked that first.

---

