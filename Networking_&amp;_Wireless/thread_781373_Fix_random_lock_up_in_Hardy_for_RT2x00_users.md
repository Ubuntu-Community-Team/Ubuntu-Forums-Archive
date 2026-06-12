---
title: "Fix random lock up in Hardy for RT2x00 users"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by ResetReboot on 2008-05-04
If you experience a lock up, your Caps Lock key blinks, when you're using your rt2x00 based card (for example, a Conceptronics wireless card) there are high chances that the problem is the driver included with the new kernel.

Fortunately, we still have the legacy drivers. They don't integrate as good as the native kernel ones, but they work and shouldn't crash so often.

How do we get them? It's easy:

1) Open a terminal and do:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
(Just copy the line and paste it and it should work straight from there)

2) Go to [serialmonkeys]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads") webpage and download the enhanced legacy drivers. If you don't know which one to get, go to System -> Preferences -> Hardware Information. Look for your wireless card and click on its name or look for something like rt2xxx/rtxx based Wireless Card, then click on advanced and in the first line, you'll read something like "info.linux.driver    string  rtxxxxpci" Note the name, that is the driver you need. I used the CVS version, and for now I've got only some minor annoyances and looks stable.

3) Unpack the tarball, open a console and enter the folder. Then get into the folder "Module"

4) Do in the console:
```
make
sudo make install
sudo echo blacklist (the driver name you saw in the info.linux.driver line) >> /etc/modprobe.d/blacklist 
```

5) Restart and enjoy!

---

