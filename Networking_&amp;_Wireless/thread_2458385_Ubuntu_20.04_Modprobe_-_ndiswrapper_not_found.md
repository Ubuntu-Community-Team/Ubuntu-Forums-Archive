---
title: "Ubuntu 20.04 Modprobe - ndiswrapper not found"
date: 2021-02-23
forum: Networking &amp; Wireless
---

### Post by easutherland on 2021-02-23
os Ubuntu 20.04
ndiswrapper 1.60-8ubuntu3
wireless dongle Netgear n-300 (wna3100)

I have been able to install the above ndiswrapper and ndiswrapper -l displays "bcmwlhigh5: driver installed; device (0846:9020) present. When I run "sudo modprobe ndiswrapper" I get

modprobe: FATAL: module ndswrapper not found in directory /lib/modules/5.8.0-43-generic.

I have not found any information on the above version combination. Any suggestions?

---

### Post by QIII on 2021-02-23
First things first:  Are you sure that the kernel will not drive that adapter natively?  Do you need NDISWrapper?

---

### Post by easutherland on 2021-02-23
> **QIII said:**
> First things first:  Are you sure that the kernel will not drive that adapter natively?  Do you need NDISWrapper?

I am not certain but I did not see any indication that it knew about wireless (no options in network settings).

---

### Post by QIII on 2021-02-23
Most wireless devices have driver modules already in the kernel, making NDISWrapper unnecessary.  Unfortunately, I have not found good news for you with regard to yours.

In 2015 [this]("https://ubuntuforums.org/showthread.php?t=2264020") was posted on the forums.  Having searched a number of other forums and AskUbuntu, it does not seem that the news has gotten any better for that hardware even up to now.  The general gist seems to be that even using NDISWrapper (Which is deprecated, by the way.  Deprecated does not mean eliminated, just "not recommended because there are better things"), your chances of getting that hardware to work are slim to none.

---

### Post by easutherland on 2021-02-23
update; /etc/modprobe.d/ndiswrapper.conf shows the wlan0 alias. Do I need to copy that over to the folder where modprobe say itis not finding and, if so, exactly what is the path?

---

### Post by chili555 on 2021-02-23
> In 2015 this was posted on the forums. Having searched a number of other forums and AskUbuntu, it does not seem that the news has gotten any better for that hardware even up to now. The general gist seems to be that even using NDISWrapper (Which is deprecated, by the way. Deprecated does not mean eliminated, just "not recommended because there are better things"), your chances of getting that hardware to work are slim to none.
Correct. I have not seen a single case of ndiswrapper working correctly either here or at askubuntu in many years.I suggest that you get a different device. [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

---

