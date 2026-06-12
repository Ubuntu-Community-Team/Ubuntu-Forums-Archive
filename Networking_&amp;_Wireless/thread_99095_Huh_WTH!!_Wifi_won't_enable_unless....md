---
title: "Huh? WTH!?! Wifi won't enable unless..."
date: 2005-12-04
forum: Networking &amp; Wireless
---

### Post by MiseryQ on 2005-12-04
I'm a n00b when it comes to linux.
I've had Ubuntu/Kubuntu and Debian at differnet time on a Toshiba and had no network issue with the ORiNCO silver card.

I changed to a Dell and a fresh install of Kubuntu 5.10.

I tried the ORiNCO Silver, the previous Agere (Toshiba) minipci and the Broadcom (Dell) minipci. They all do the same:
I can not get the network interface to enable for more than 1sec, it goes right back down, unless I repeated click the "activate" and/or "autodetect" buttons in the wireless network setting.

I've tried to research, troubleshoot this and figure out why it would have this behavour and can't. But it works everytime.

How would I go about getting this corrected?

):

---

### Post by Lambert on 2005-12-06
try enabling it from the terminal instead of using the gui tool and see if it does the same thing.

```
sudo ifup <wlan0>
```

where <wlan0> = your inteface logical name minus the <>

---

### Post by blaise69 on 2006-01-18
I find this happens to me also, the solution I found was to add the Subnet mask (something like 192.168.1.1), it can be found on the next tab along in the gui.

Hope this helps!

Cheers,

Blaise.

---

### Post by Shonkin57 on 2007-11-19
My experience w/ my new orinoco silver card, using Ubuntu 7.10, was also pretty ragged. I did at last succeed, but am not exactly sure why. My specs are perhaps odd. I'm using a Compaq 2545us laptop, which has one of those delightful (NOT!) windows broadcom wireless cards built in. That card no longer works... even in windows. But it does show up when I boot Ubuntu... still not working. (It likely has nothing to do with anything, but there you are.)

Here is what I (think?) I did:

First, I did a lot that did not work. We'll skip that.

I then typed in (from within an xterm) and without the quote marks:

"sudo modprobe orinoco"

I think. And don't forget the 'sudo' or you'll not be allowed to do this.

Then I typed:

"iwconfig"

Sure enough, my computer was reported to have an orinoco pcmcia wireless card, along with a basic LAN card (wire port) which I ignore, and the broadcom, which I also ignore.

More trouble, though, when I went to use the network applet at upper right hand corner next to the calendar / time. I had set it to "manual" during one of my forays into attempted fixes. BAD idea. Do NOT do this. I still do not know how I backed out of that mess, because there was no simple way (as I wrongly assumed) to tell it to go back to an autodetect setting rather than manual setting. Sheesh. THAT feature will, I hope, be fixed.

Once I did get it to go back to autodetect -- someone else can tell us all how it is done the right way -- and rebooted the machine, I was able to see the orinoco card. It is, however, identified as a "Lucent Technology WAVELAN/IEEE" -- which isn't what I thought it was. When I type iwconfig, it is identified as a "Hermes I".

Well, that isn't much help. And I may have left out important things I did while mucking about. Perhaps my additions to what already was posted about orinoco cards elsewhere here can be consolidated into one post by someone wiser and more informed than I.

Blessings,
jon t

---

