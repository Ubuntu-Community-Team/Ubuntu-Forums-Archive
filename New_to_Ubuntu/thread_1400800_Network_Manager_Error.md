---
title: "Network Manager Error"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by New00Folder on 2010-02-07
I'm using Ubuntu 9.10 and I tried to install "wicd network manager" using Ubuntu Software Centre. It was downloaded but something was found lacking in my computer and my system hanged. (Even mouse wouldn't work.) I switched off using the power button after 2 about 2 mins. After restarting I can't find network manager applet. It's also gone from Administration. I had installed "Network Selector" previously and gives error something like- "network-admin: no such file or directory". I can't reinstall network manager applet nor remove wicd using synaptic package manager.(Both result in some error about wicd.) Also, Ubuntu software centre isn't starting. What to do?


In fact a lot of other things like g-debi package manager, main menu option in preferences, etc. aren't working.

---

### Post by New00Folder on 2010-02-10
Since I don't know any better, I decided to format and re-install Ubuntu. I copied all the Debian packages from /var/cache/apt/archives in a USB flash drive and re-installed all of them except the 'wicd' one after re-installing Ubuntu. Some of the packages were broken, so I removed them(not completely). Then I started update manager. After updating, I installed the packages I had removed successfully. Now everything is working in order.

---

### Post by superprash2003 on 2010-02-10
please mark thread as SOLVED

---

