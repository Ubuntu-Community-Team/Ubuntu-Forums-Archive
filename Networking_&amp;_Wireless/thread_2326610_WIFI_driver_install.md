---
title: "WIFI driver install"
date: 2016-06-02
forum: Networking &amp; Wireless
---

### Post by thomas110 on 2016-06-02
Hello. Did a post on this a few days back but now there is a new issue. I'm running the latest Ubuntu in a VM with a RTL8812AU Chipset USB wireless adapter. I got Ubuntu to display a list of wifi networks. So The adapter works, but When I go to connect to a network, I sometimes connect, then I am not able to load a website. Weird. Any suggestions. Standby for WIFI Config thing.

---

### Post by jeremy31 on 2016-06-02
Are you still using the first driver from the other post or did you switch to [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

You may have better results allowing the host OS to control the wifi and switch access points from it rather than trying to do it from the Ubuntu guest

---

### Post by thomas110 on 2016-06-02
Good point. I am using a different adapter, but it has a similar chip (RTL8812AU) Not sure if that is the one you are referencing above?

---

### Post by jeremy31 on 2016-06-02
I posted about the alternative in [http://ubuntuforums.org/showthread.php?t=2326056](http://ubuntuforums.org/showthread.php?t=2326056) but that driver from the github site should work.  I would have more faith in the github driver if Ubuntu was installed as a dual boot

---

### Post by thomas110 on 2016-06-02
I installed the new driver without issue. But I still can barely connect to a network and cannot load a webpage when it does connect

---

### Post by jeremy31 on 2016-06-02
See how it does when you allow the host OS to control wireless.  I installed vmware on a Win 7 laptop and installed Ubuntu 16.04 as a guest and internet worked good from the default settings that allowed Ubuntu to use a bridged connection over a virtual ethernet device.

---

