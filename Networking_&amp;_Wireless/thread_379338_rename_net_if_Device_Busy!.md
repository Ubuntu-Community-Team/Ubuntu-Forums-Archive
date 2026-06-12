---
title: "rename_net_if: Device Busy!"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by Aikon- on 2007-03-08
Well, I'm back.. surprise surprise ;)

Something's been kind of bugging me recently.. When I boot Ubuntu, the splash screen seems to hang for 10 or 15 seconds at "Configuring network interfaces...", then the boot procedure continues without flaw, I login, and I can access the network fine.

I disabled the splash screen so I could see detailed output, and at the same stage what seems to be causing the hang is the following:

```
udevd-event[XXXX]: rename_net_if: error changing net interface name: Device or resource busy
```

Any ideas? I'm using a Linksys wireless card with the particularly annoying Broadcom chipset (the one that requires ndiswrapper).

-Aikon

---

### Post by Mr. C. on 2007-03-08
This is a problem with udev.

```

$ sudo rm -f /etc/udev/rules.d/z25_persistent-net.rules
$ sudo update-initramfs -u
```

---

### Post by Aikon- on 2007-03-09
Thanks; I'm at work now and heading straight up North for the weekend from here, but I'll give it a try when I get back home on Sunday.

-Aikon

---

### Post by Mr. C. on 2007-03-09
Great, have a nice trip.

Please report back if this solution resolved your issues.

MrC

---

### Post by Aikon- on 2007-03-13
Well, I entered the commands you gave above, no errors, then I rebooted my machine.. It still hung at "Configuring network interfaces" and then gave the same device busy error =(

Any other suggestions?

---

### Post by Mr. C. on 2007-03-13
I'm not certain.  You might need to perform the steps without udev running.

At a terminal window, type:

init 1

this will kill all the processes.  You will see a dialog asking you to enter the root password to enter maintenance mode.  Enter the password, and then once logged in, use the commads I gave 
```

rm /etc/udev/rules.d/z25_persistent-net.rules
update-initramfs -u

```

No need for sudo this time.  Once those are done, restart.

If this doesn't work, I'm not sure what the answer is.

Hopeful,
MrC

---

