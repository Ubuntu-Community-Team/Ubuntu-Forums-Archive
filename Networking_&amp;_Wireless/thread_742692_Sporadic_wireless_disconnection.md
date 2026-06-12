---
title: "Sporadic wireless disconnection"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by greybit on 2008-04-01
Seemingly randomly I lose my wireless connection.  A reboot fixes the problem every time, but I'm wondering if there are any commands to use in the terminal to restart my NIC (or whatever might be appropriate) instead.  I'd rather not be forced to reboot.  Or... maybe somebody knows the root of the problem?

Thanks!

---

### Post by mrsteveman1 on 2008-04-02
Reloading the network scripts should fix a lot of things:

```
sudo /etc/init.d/networking restart
```

If not, you can always reload the driver for your chipset. What chipset is this?

---

### Post by greybit on 2008-04-02
Thanks!

Since I lose the connection randomly I won't be able to check this right away, but I'll post back here the next time it happens.

Oh, and my NIC's chipset is:
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Thanks again!

---

### Post by chris82543 on 2008-04-02
might be your wifi router, maybe not but that was my problem

---

### Post by greybit on 2008-04-06
> **mrsteveman1 said:**
> Reloading the network scripts should fix a lot of things:

```
sudo /etc/init.d/networking restart
```

If not, you can always reload the driver for your chipset. What chipset is this?

Hi,

My connection failed again today.  In the init.d folder I restarted networking but I still had no connection.  I also tried restarting anything network related in that folder.  In the end, I had to reboot to regain my connection.  :(  How would I go about reloading the driver for my nic's chipset?

Thanks!

---

### Post by mrsteveman1 on 2008-04-07
If you are using gutsy and haven't installed your own ndiswrapper driver, reloading the module alone should fix most things as it reinitializes the chip, and i believe it reloads the firmware, which should reset a lot of things.

```

sudo rmmod bcm43xx
sudo modprobe bcm43xx
```

Then reload the network script again.

If that doesn't fix it, perhaps the entire 80211 stack needs to be reloaded, but thats unlikely

---

### Post by greybit on 2008-04-13
Uh oh.  I *am* using gutsy and I *have* installed my own ndiswrapper driver.  Could this be the problem?  I also don't know how to go about reloading the 80211 stack...

Thanks again for your help!

---

### Post by mrsteveman1 on 2008-04-13
Ok, so which one are you using, the ndiswrapper driver or bcm43xx?

Usually ndiswrapper works better than bcm43xx.

If thats what you are going to use, blacklist bcm43xx by adding the following line to /etc/modprobe.d/blacklist

```
blacklist bcm43xx
```

---

### Post by greybit on 2008-04-14
So, I am using the ndiswrapper driver and I have already blacklisted bcm43xx...

---

### Post by mrsteveman1 on 2008-04-14
Yea you can just reload ndiswrapper and that should reset everything

```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

that should reload the driver, reload the firmware and reset the nic. the networkmanager GUI should also detect the card reloading and connect again for you.

I would be interested to know what the problem is but its hard to say.

---

### Post by wieman01 on 2008-04-14
Also try out another wireless channel as interference with other networks might be the culprit. This so happened in my case.

---

