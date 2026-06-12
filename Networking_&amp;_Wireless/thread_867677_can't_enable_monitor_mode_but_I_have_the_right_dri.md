---
title: "can't enable monitor mode but I have the right driver...?"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by and448 on 2008-07-23
hey guys, a newbie so bare/bear(?) with me.

trying to use Aircrack-ng on latest version of ubuntu.

I'm using the iwl3945 driver, which according to the aircrack-ng website is compatible, and supports all necessary features.

Also, with I do: "sudo iwlist wlan0 scan" I see the wireless networks so the driver is working right?

ok, toruble starts here: "sudo airmon-ng start wlan0"

I get the following:

```
Interface    Chipset        Driver

wlan0            iwl3945 - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)
```

any ideas? would really appreciate any help, am a bit lost

thanks again

andy

---

### Post by ldaves on 2008-07-23
Go download and installa the aircrack-ng 1.0-RC
and it will ask u install a iw-related to fix the problem

---

### Post by and448 on 2008-07-23
hey Idaves, thanks so much for replying, I really appreciate it.

Ok, first off I'm totally new to linux. I installed my current version of aircrack-ng using the packages manager in Ubuntu.

Could you clarify a bit more on the steps i'd need to take to installing this RC-1 version...?

Like, i assume on the website is a source version? and then I download that a compile it...is that right?

any help would be awesome, am really enjoying the challenge on linux!

cheers

---

