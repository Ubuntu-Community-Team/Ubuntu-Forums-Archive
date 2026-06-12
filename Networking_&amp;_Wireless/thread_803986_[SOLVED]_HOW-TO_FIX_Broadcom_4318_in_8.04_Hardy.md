---
title: "[SOLVED] HOW-TO FIX: Broadcom 4318 in 8.04 Hardy"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by Steve413z on 2008-05-22
My laptop has a built in internal Intel wireless card, that is supported out of the box with Ubuntu. However I keep an extra PCMCIA wireless card in my laptop bag that has an external antenna for longer range if i need it (In this case, a Buffalo WLI-CB-G54HP)

With Ubuntu 7.10 (and a few version before that) to install support for the wireless card, you pretty much just had to install the package “bcm43xx-fwcutter” and it would start working.

Now Ubuntu 8.04 attempted to make Broadcom support better by using the restricted driver wizard (or whatever they call it) to install Broadcom wireless cards, however this somehow got screwed up in my case.

After much trial and error, and much Google searching, I found a solution.

[SIZE="5"]Step 1:[/SIZE]

Make sure the wireless card is plugged in.
[B]
Completely[/B] Remove Package: “b43-fwcutter” and “bcm43xx-fwcutter”

[SIZE="5"]Step 2:[/SIZE]

use your favorite text editor (as root/sudo) and edit
/etc/modprobe.d/blacklist

Find the line that says “blacklist bcm43xx” a comment it out using a "#" 
[SIZE="5"]
Step 3:[/SIZE]

Install the package “bcm43xx-fwcutter” and allow it to fetch the firmware on install.

Reboot if necessary
[SIZE="6"]
I hope it works! [/SIZE]

---

### Post by Ayuthia on 2008-05-22
Don't you need to blacklist b43 so that ssb does not interfere with the bcm43xx driver?

---

### Post by Steve413z on 2008-05-22
> **Ayuthia said:**
> Don't you need to blacklist b43 so that ssb does not interfere with the bcm43xx driver?

nope, I didn't need to, but I didn't install the b43 driver, I completely removed it, but you probably could if you wanted to, but i've had no conflict yet, and after doing it, it doesn't even show up in the restricted drivers menu anymore.

---

### Post by Ayuthia on 2008-05-22
> **Steve413z said:**
> nope, I didn't need to, but I didn't install the b43 driver, I completely removed it, but you probably could if you wanted to, but i've had no conflict yet, and after doing it, it doesn't even show up in the restricted drivers menu anymore.
By uninstalling b43-fwcutter, all you are doing is taking out the firmware that it needs to make it work.  The module in itself is most likely still there.  If you were to go to a terminal and type "locate b43.ko" and it returns the location of it, then the driver is still there.  The portion of concern is the ssb driver.

Don't get me wrong, I am all for going this route when you can't get b43 to work.  I am just trying to figure out if bcm43xx can live fine with ssb around or if bcm43xx is being loaded before b43 so it is able to run without ssb conflicts.

Can you do me a favor and post the results of:```
lsmod|grep -i -e b43 -e ssb -e bcm43xx
```

Thanks!

---

### Post by brunoscunha on 2008-05-22
I compiled the latest kernel 2.6.25, and there it was. Wireless fully functional.

Because i'm quite new in compiling kernel, I followed all the steps from this website [http://howtoforge.com/kernel_compilation_ubuntu]("http://howtoforge.com/kernel_compilation_ubuntu")

Result of lsmod|grep -i -e b43 -e ssb -e bcm43xx

```
bcm43xx               142184  0 
ieee80211softmac       35328  1 bcm43xx
ieee80211              38600  2 bcm43xx,ieee80211softmac
b43                   156072  0 
rfkill                 10400  3 rfkill_input,b43
mac80211              203156  1 b43
input_polldev           7184  1 b43
led_class               7688  1 b43
ssb                    38020  1 b43
```

---

### Post by Ayuthia on 2008-05-22
> **brunoscunha said:**
> I compiled the latest kernel 2.6.25, and there it was. Wireless fully functional.

Because i'm quite new in compiling kernel, I followed all the steps from this website [http://howtoforge.com/kernel_compilation_ubuntu]("http://howtoforge.com/kernel_compilation_ubuntu")

Result of lsmod|grep -i -e b43 -e ssb -e bcm43xx

```
bcm43xx               142184  0 
ieee80211softmac       35328  1 bcm43xx
ieee80211              38600  2 bcm43xx,ieee80211softmac
b43                   156072  0 
rfkill                 10400  3 rfkill_input,b43
mac80211              203156  1 b43
input_polldev           7184  1 b43
led_class               7688  1 b43
ssb                    38020  1 b43
```

I am assuming that you only have the firmware installed for bcm43xx and not b43?

---

### Post by brunoscunha on 2008-05-22
> **Ayuthia said:**
> I am assuming that you only have the firmware installed for bcm43xx and not b43?

In 7.10 I had the firmware installed and nothing worked. After upgrading to 8.04 still nothing worked.
But in ubuntu irc channel someone told me it was a issue with the kernel. And to solve it, the best way was to compile the latest kernel, and there it was.

Yes I had the firmware for 43xx, not 43

---

