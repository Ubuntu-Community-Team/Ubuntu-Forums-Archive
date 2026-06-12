---
title: "Any better way to get drivers for rtl8192du?"
date: 2015-01-13
forum: Networking &amp; Wireless
---

### Post by knarf-musique on 2015-01-13
I have been using the kernel version of 
**rtl8192du**

from github. But evertime there is a kernel update the driver is a nightmare to reinstall. 

Is there anyway to install this without having to recompile as often?

I'm a n00b, so any input would help. I wish ubuntu supported more usb wireless chipsets. =p

This is what i use:
```

wget https://github.com/lwfinger/rtl8192du/archive/kernel-version.zip
unzip kernel-version.zip
cd rtl8192du-kernel-version
make 
sudo make install
sudo modprobe 8192du
```

thanks to [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar35909_21.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=35909")                                                                                     [**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=35909")
for showing me the kernel version!

---

