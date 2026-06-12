---
title: "connection on wlan failed"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by crew51m on 2010-08-22
I try to logon to my network, it fails to connect, I use the same key on ubuntu and all computers in my house, both windows and ubuntu, but KDE wont let me use it, I also disabled kdewallet. I changed some settings and it still wont log on, also in KDE where do I go to find settings for what loads when kde loads, the printer connect is driving me nuts.

---

### Post by bergfly on 2010-08-23
If you are still using 9.04, then I highly recommend replacing the KDE network manager with WICD. They never really fixed the network manager in that release. Note that this will also affect your gnome install on the same box!

If you are currently on 10.04, it should work now, although it does need the kdewallet to keep your passcode for the network. An empty passcode will work.

As far as what loads on boot, go to System Settings and select the advanced tab. Under the advanced tab in the top section is "autostart" which has what loads on boot.

hope it helps

---

### Post by crew51m on 2010-08-23
Yes thank you.

---

