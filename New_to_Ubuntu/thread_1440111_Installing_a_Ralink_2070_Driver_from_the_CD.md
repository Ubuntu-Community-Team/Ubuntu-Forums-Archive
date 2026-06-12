---
title: "Installing a Ralink 2070 Driver from the CD??"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by waltersfield on 2010-03-27
Hi, I'm a newbee to Ubuntu 9.10 and I need to install a Ralink 2070 wireless driver. I have the CD, but obviously the install process is not like Windows. Can anyone tell me how to install a driver from a CD in Ubuntu?

Many thanks!

---

### Post by Gixxy on 2010-03-27
Does this help?

[http://ubuntuforums.org/showthread.php?t=1285828]("http://ubuntuforums.org/showthread.php?t=1285828")

---

### Post by readycarpenter on 2010-03-27
as of 9.10 I have never needed to do anything special to get wireless drivers working, ubuntu does not come with proprietary drivers, as most wireless cards use, so as a work around, they have under system>admin>hardware drivers, a way for you to install the drivers without bundling with ubuntu. but you need to be online via a wired network, run hardware drivers, and your card should show there, install and reboot

hope this help
cheers

---

### Post by 3rdalbum on 2010-03-27
> **readycarpenter said:**
> as of 9.10 I have never needed to do anything special to get wireless drivers working, ubuntu does not come with proprietary drivers, as most wireless cards use, so as a work around, they have under system>admin>hardware drivers, a way for you to install the drivers without bundling with ubuntu. but you need to be online via a wired network, run hardware drivers, and your card should show there, install and reboot

hope this help
cheers

It doesn't help for this particular card, because it is rather new and isn't in Ubuntu's 2.6.32 kernel. (a minute of Googling told me this)

waltersfield, what you'll have to do is:

a. If it comes inside a .tar.gz or .tar.bzip2 file, extract it to somewhere on your computer. Preferably the desktop.
b. Get an internet connection by plugging your computer into your router with an Ethernet cable.
c. Use Synaptic Package Manager to install the "linux-headers-generic" and "build-essential" packages.
d. Reboot. (the linux-headers-generic package might have caused a new kernel to be downloaded).
e. Open the terminal (Applications > Accessories > Terminal) and type in the word 'cd', followed by a space, and then drag the extracted folder into the terminal. This will put the path of the folder into the terminal. Press Enter to run this command.
f. Put in the following commands:

```
make
sudo make install
```

At the 'sudo make install' part, you'll be asked for your password. Enter it in - it won't show any stars or anything while you're typing.

g. Reboot and you should be able to connect to your wifi using the Network Manager applet, on your top panel to the left of the clock.

You will need to do E, F, and G every time your kernel gets updated.

Sorry that it was a bit of a pain to install. Most wireless cards are supported by Ubuntu out-of-the-box, but this card is a bit too new to have its driver included in Ubuntu 9.10.

---

