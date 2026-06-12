---
title: "Help!wifi doens't work!!"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by stamatiou on 2010-12-27
Hey guys, I have been changing several distros lately, I had installed OpenSuse and everything were ok I rebooted but the driver wasn't there, the networks dissapeared....
Then I tried to reinstall OpenSuse but when I installed again the driver nothing happened. Then I installed Fedora(two times) Linux Mint but the same....
I have the laptop HP Compaq 615 and in every distro I had to install some special packages....
I did the same in Ubuntu with th "broadcom-sta-common" package but nnothing happened:frown:](*,)](*,)

---

### Post by davidmohammed on 2010-12-27
I presume you've tried using System - Administration - Hardware drivers and enabling the recommended package there.

If you are using broadcom there is very likely to be a firmware you need to install.  Using that Hardware drivers option above, the firmware is downloaded and installed correctly for you.

---

### Post by stamatiou on 2010-12-27
> **davidmohammed said:**
> I presume you've tried using System - Administration - Hardware drivers and enabling the recommended package there.

If you are using broadcom there is very likely to be a firmware you need to install.  Using that Hardware drivers option above, the firmware is downloaded and installed correctly for you.
If you mean th "Additional Drivers", yes it is activated.

---

### Post by iAmNadav on 2010-12-27
Just throwing this out there, might sound stupid but - make sure you didn't disable the wifi with one of your fn keys.. good luck :popcorn:

When you go to your connections under "wireless networks" what does it say?

---

### Post by davidmohammed on 2010-12-27
any obvious looking error messages if you look at your kernel logs?

e.g.

dmesg | grep b43

---

