---
title: "ndiswrapper drops internet connection too often"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by fd9_ on 2007-07-19
I'm currently using the latest version of ndiswrapper as a temporary solution for my wifi until I have enough time to actually sit down and figure out how to install the native linux drivers for my Intel 4965 AGN card. But my internet connection seems to drop out every so often...sometimes it's every 30 minutes, while other times it can be every 5 minutes. It's extremely frustrating! So far I've been fooling around with the Network Manager in order to restart the connection, but it doesn't always work. Is there any way I can restart ndiswrapper?

---

### Post by msjones on 2007-07-19
Hi

Are you using the latest version of ndiswrapper, i think its version 1.47 now.

[Click here to download the latest version.]("http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=mesh&filename=ndiswrapper-1.47.tar.gz&71598690")

1. Unzip and untar.
2. cd to the ndiswrapper directory.
3. sudo make uninstall
4. make
5. make install

Then install the driver as you did before.

I had the same trouble as your having, and it turns out I wasnt running the latest stable release.

Hope this works for you.

mj

---

