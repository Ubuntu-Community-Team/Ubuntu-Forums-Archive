---
title: "Fresh New Dual Boot 17.04 With No Internet"
date: 2017-07-14
forum: Networking &amp; Wireless
---

### Post by GatherYeRosebudsWhileYeMay on 2017-07-14
So I am new to Ubuntu, wanted to try it out alongside my Windows 10 (so I have a choice to load either one when I boot up) but when I load up Ubuntu and log in, there is not any internet connections showing up. Is it because I am using a USB internet adapter. If so, how do I fix it to work?

(i have no internal internet card, and i am using wireless internet)

---

### Post by johndough2 on 2017-07-16
Hi

Without an internet connection whilst using Ubuntu is making things tricky.

Normally you would use apt or apt-get and install some wireless tools or drivers.

# aptitude update && aptitude install wireless-tools

Could they be on another medium, like an install disk?  How did you create the install media?

Maybe you need to find the Network Manager?

Help is here

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

---

