---
title: "Intel 4965 Issues"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by ootz0rz on 2007-10-14
Hello all,

I have just installed Ubuntu 7.10 (Gutsy) on my laptop (Asus G1S-A1, or just G1S, doesn't matter) and have got most everything working that I've tested so far except for one major thing keeping me back from using it as my main operating system - my wireless network card.

Now, the weird thing about it is this:
When I originally booted Ubuntu as a LiveCD to install, the wireless worked flawlessly out of the box. I went ahead and then installed Ubuntu, and booted into it. It was still working fine. So I decided to begin installing some programs and such that I like/needed. One of which was the nvidia drivers (so I could get compiz fusion and all that good stuff going.) And of course, the nvidia drivers require a restart. So, I restarted my laptop, but the wireless was no longer working. I tried to enable and disable networking, but that didn't help. I know that the wireless is on, and tried cycling through the different wireless modes with the built in wireless button on the laptop, but that didn't help either.

Looking at lsmod, I could see that the modules WERE running and active. iwconfig also seemed to confirm this. Running ifconfig, it would also see wlan0 there. I tried ifdown and ifup on the interface but that didn't seem to do anything either.

So, I decided to then try to install the windows drivers using ndiswrapper. So, I went ahead and got ndiswrapper properly installed. Then, downloaded the windows xp drivers from the official intel website. Installed that, set it up with modprobe, and started up the module. Once again, no errors, and lsmod showed ndiswrapper running. But still no wireless functionality.

I'm really not sure what else to do. Any help would be VERY much appreciated, thanks!

---

