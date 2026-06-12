---
title: "Ndiswrapper is almost working, but it's not quite there yet..."
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by jerseyboy91 on 2007-03-10
I have decided to install a wireless connection for my Xubuntu computer with ndiswrapper. I have followed all the steps (but I've had to use my own driver, since there aren't any similar ones to mine). I've gotten all the way to typing in:

  sudo depmod -a
  sudo modprobe ndiswrapper

The computer recognized the driver and the hardware, but it isn't showing up in the Networking control panel, so that's where I'm stuck.

If any of you need to know this, I'm running a Samsung wireless USB card (ID 055d:a230) on Xubuntu 6.06. If anyone needs any more info, I'll be glad to give it (but I may have to answer in a couple of hours, I'm starting to feel sleepy).

---

### Post by teaker1s on 2007-03-10
try this
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8
```

---

### Post by jerseyboy91 on 2007-03-10
Here's what I got..

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper-common

Maybe if someone could post a link to this package, so I can transfer it to my computer. Thanks for helping out, but without this, I probably can't figure out the problem.

EDIT: Nevermind, I found a download link to the package, so what do I do next? Do I put it on the desktop and run it again?

---

### Post by Condoulo on 2007-03-10
As far as I know, the SWL-2300U I used to use didn't work with ndiswrapper. But using linux-wlan-NG with a patch can get it to detect it in the network manager.... but not as a wrieless device though, which is where my problem is, editing the configuration file for the device to connect to my network.

---

