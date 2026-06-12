---
title: "disable wifi?"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by onlythetim on 2006-09-07
Hi, I'm using ubuntu on a Dell latitude D820.  When I'm using the ethernet port (eth0) I like to disable wireless, so as not to waste my battery.  I do this by going into the network monitor, and disabling eth1 (wireless).  However, even after I do this, the wifi light no my computer continues to flash.  Does this mean its still scanning the wireless?  Is there a way to disable it?

---

### Post by newlinux on 2006-09-07
I'm not too familiar with Dell notebooks, but lots of laptops have hardware switches to disable the wireless card (mine does). Perhaps there is a function key combination or other key that disables the wireless card. Check the manual.

Hope that helps.

---

### Post by onlythetim on 2006-09-07
it has a hardware switch for the cellular card, but that's not the wifi.  I know I can switch it off in the bios, but I don't want to have to restart the computer in order to enable/disable it.

I no that it appears in ifconfig if it is active.  Is there a way to remove something from the ifconfig list?  Like tell the system not to use it?

Thanks.

---

### Post by newlinux on 2006-09-07
[http://support.dell.com/support/edocs/systems/latd820/en/ug/about.htm](http://support.dell.com/support/edocs/systems/latd820/en/ug/about.htm)

says the 820 has a switch to disable the wifi. If that doesn't exist, I believe you can do echo -n 3 to turn it's power state off and echo -n 0 to turn it on. e.g.

```

echo -n 3 > /sys/class/net/[wireless device]/device/power/state

```

```

echo -n 0 > /sys/class/net/[wireless device]/device/power/state

```

where wireless device is whatever your wireless device is (eth0, eth1, etc.). You can look in /sys/class/net and find the device that has a "wireless" subdirectory.

That should work...

---

