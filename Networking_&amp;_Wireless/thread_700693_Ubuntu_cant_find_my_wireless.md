---
title: "Ubuntu cant find my wireless"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Ub2daUntu on 2008-02-18
So i finally installed a sucessful vista/ubuntu dual boot. Buy my joy was cut short because when i logged in to ubuntu, I couldn't find my network.  As I am a complete noob, could someone please post any info they might need to help me, and how I am to obtain this info.

---

### Post by erginemr on 2008-02-18
Please refer to this post on **ndiswrapper-gtk**:
[http://ubuntuforums.org/showpost.php?p=4271829&postcount=5](http://ubuntuforums.org/showpost.php?p=4271829&postcount=5)

You should also give a shot to **wifi-radar**.

---

### Post by Ub2daUntu on 2008-02-18
hey thanks. the wrapper doesn't seem to match what im using. so could u go into a little more detail about the wifi-radar. what is does. how can i get it without access to the internet?

---

### Post by erginemr on 2008-02-18
No problem, but I am not a wireless modem user so can only guess. Anyway, do you have the windows installer for your modem? The wrapper uses windows setup files, esp."*.inf" file to make it recognized by the Linux system.

Wifi-radar is not a replacement for ndiswrapper. It is, AFAIK, a tool to catch existing wifi networks in the vicinity. But you need to have a laptop which has a receiver for wifi networks for it to work.

If you are currently using Windows, all you need to do is to download necessary debian packages. Go to:
[http://packages.ubuntu.com/gutsy/net/](http://packages.ubuntu.com/gutsy/net/)

and download:
**ndisgtk**, **ndiswrapper-utils** and **wifi-radar** debian packages. Also download any given dependencies in the corresponding download pages for these packages. Find the Windows driver (but it should be XP, not Vista) for your modem with an *.inf / *.sys file from the web.

Then, take all of them to a USB pen drive, boot into Ubuntu. Install Debian packages one by one. Skip the ones if it says it is already installed. Finally run ndiswrapper-gtk to install the Windows driver for your modem.

You should read the following manual thoroughly:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
It explains all those steps in detail.

---

