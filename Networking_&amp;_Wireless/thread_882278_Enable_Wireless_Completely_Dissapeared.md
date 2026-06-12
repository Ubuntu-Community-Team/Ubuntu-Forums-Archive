---
title: "Enable Wireless Completely Dissapeared"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by wirelessless on 2008-08-06
I have read various threads about wireless disappearing from the Network Manager, and most of these ended up being fixed by commenting out various lines from /etc/network/interfaces . I have tried this numerous times and it's not working for me still.

I have been running ubuntu on my dell for about 6 months and using wireless the whole time with no problem. Recently, I unchecked the "enable wireless" box in the Network Manager because I didn't want it to auto-connect one day. After that, it completely disappeared, not only from the Network Manager, but also from Network Settings,so I basically see no wireless options anywhere where they should be. And, as stated above I commented out everything in the /etc/network/interfaces.

Any ideas?

---

### Post by Lori700698 on 2008-08-06
what kind of driver were you using?

---

### Post by mrsteveman1 on 2008-08-06
Is the kernel module for the chip loaded? Check with lsmod and look for it if you know what module/chip it is.

Next, does ifconfig or iwconfig list the interface? Probably will be eth1 or wlan0.

Is networkmanager (the background daemon) running? Check with ps ax in a terminal.

If those things are all ok, is the networkmanager GUI running? Is this a laptop with a switch that turns off wireless?

---

### Post by wirelessless on 2008-08-07
Oooof!!! Well, sometimes (usually) it's the most obvious solutions that end up fixing the problem. My previous Dell laptop had a wireless on/off switch located near the top of the keyboard and was much more obvious. This Dell D630 laptop has a wireless on/off switch on the left side near the wireless card slot, i didn't even know it was there. looks like it got switched into the off position.

Thanks for the idea! And thanks for making me feel smart! ;)

---

### Post by s_dub757 on 2008-08-09
> **mrsteveman1 said:**
> Is the kernel module for the chip loaded? Check with lsmod and look for it if you know what module/chip it is.

Next, does ifconfig or iwconfig list the interface? Probably will be eth1 or wlan0.

Is networkmanager (the background daemon) running? Check with ps ax in a terminal.

If those things are all ok, is the networkmanager GUI running? Is this a laptop with a switch that turns off wireless?

I am Having A Problem With My Sierra Wireless Aircard 595U Not showing up. do you think that you can help me out with this?

---

### Post by mrsteveman1 on 2008-08-10
s_dub: make a new thread and post the URL for it here.

---

