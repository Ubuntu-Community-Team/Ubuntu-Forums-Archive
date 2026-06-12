---
title: "Problems with USB wifi adapter D-Link DWA-171 after installing drivers"
date: 2018-02-25
forum: Networking &amp; Wireless
---

### Post by fabioperez on 2018-02-25
Hello to everyone,
I'm using Ubuntu 12.04 on desktop pc and trying to use usb wifi adapter D-Link DWA-171 for connecting.
Until now i was connected by ethernet cable but, after need to move the pc in another room, I need to go wireless.

After many trying and threads on this forum, I managed to install the correct drivers from [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au) as shown in [this thread]("https://ubuntuforums.org/showthread.php?t=2168426&page=4") doing
```
cd rtl8812au
make clean
make
sudo make install
sudo modprobe 8812au

```
had a "command not found" error for sudo modprobe but the adaptor is now working fine.

The problem is that, on turning on the pc, tha adaptor is not working automatically. I had to put it in ad out the usb port several times in order to make the system recognize it.
Entering settings - network i always have an error, something like "this service is not available in this version" - my translation, and then wireless option appears.

One last thing, I'm not able to enter Bios for disable Ubuntu secure boot and so I have to wait 60 seconds while system tryes to find a network.
Just for the complete situation, I guess I'll open later a new thread about it.


I'm using Ubuntu for some years now, still a newbie but always managed to solve issues by myself.

Any help really appreciated
Cheers

---

### Post by chili555 on 2018-02-25
> I'm using Ubuntu 12.04 on desktop pcI am not surprised that you are having problems. I am quite surprised that the driver package even works in 12.04.

Version 12.04 has been end-of-life for a long, long time. It is no longer receiving security updates. As well, none of us here have 12.04 installed so that we may guide you.

I suggest that you install, at least, Ubuntu 16.04 LTS: [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

We have made a lot of progress in wireless in the last six years!

---

### Post by fabioperez on 2018-02-28
Thanks chili555, I'll try upgrading.
Hope will not get too heavy form my old pc!

Cheers

---

### Post by chili555 on 2018-02-28
> **fabioperez said:**
> Thanks chili555, I'll try upgrading.
Hope will not get too heavy form my old pc!

CheersThe are a couple of lightweight versions of Ubuntu that may be more suitable. I suggest that you look into lubuntu: [https://lubuntu.net/](https://lubuntu.net/) as well as xubuntu: [https://xubuntu.org/](https://xubuntu.org/)

---

