---
title: "'No wifi adapter found' after suspend"
date: 2018-08-03
forum: Networking &amp; Wireless
---

### Post by toadtoad on 2018-08-03
Yes, I know this has been posted several times on this forum, but nothing that I've found has helped.

I'm on an HP Pavilion laptop with a Realtek RTL8723BE wireless card. I am currently running Ubuntu 18.04. As said in the title, whenever I put the computer into suspend, wifi is disabled upon exiting (no wifi adapter found, airplane mode turned on). ```
rfkill list all
``` shows that it is hardblocked, but the airplane mode key (f12 or fn + f12) doesn't work. (I don't think it worked initially anyway so maybe fixing that could fix the problem?) I've tried several fixes over the past couple days with no avail.

These include:
1. ```
sudo service network-manager restart
```
2. looking in BIOS for a useful setting (found none; resetting to factory default doesn't help either)
3. ```
/etc/systemd/system/wifi-resume.service
```
4. ```
sudo rfkill unblock all
```
5. anything with ```
nmcli nm
``` (given ```
Error: argument 'nm' not understood. Try passing --help instead.
```)
6. updating kernel to latest
7. blacklisting drivers (I may have done this incorrectly, so maybe I should try this again?)
8. ```
sudo modprobe -r rtl8723be
``` before suspend and ```
sudo modprobe rtl8723be
``` after suspend

All of these (and probably more) didn't do anything to change the issue. Is there any other fix that I could do?

Attached is my wireless-info.tar.gz.

[ATTACH]280621[/ATTACH]

---

### Post by slickymaster on 2018-08-03
*Thread moved to **Networking & Wireless**.*

Please see this [sticky]("https://ubuntuforums.org/showthread.php?t=370108") and proceed accordingly

---

### Post by praseodym on 2018-08-03
Looks like Airplane mode?! Button, switch, key or key combo? What about
```

sudo rmmod hp_wmi
```

---

### Post by toadtoad on 2018-08-03
> **slickymaster said:**
> *Thread moved to **Networking & Wireless**.*

Please see this [sticky]("https://ubuntuforums.org/showthread.php?t=370108") and proceed accordingly
I have already attached the output into the original post.

> **praseodym said:**
> Looks like Airplane mode?! Button, switch, key or key combo? What about
```

sudo rmmod hp_wmi
```
It's key/key combo. The key combo/key hasn't worked at all as far as I know. Tried and it ddin't work, even after restart.

---

### Post by toadtoad on 2018-08-03
Is there any other way I could find help?

---

### Post by toadtoad on 2018-09-02
I know users like @chili555 have helped others in the past. Can he help?

---

### Post by MisterPi on 2018-09-03
Sounds a bit like a problem I'm having at [https://ubuntuforums.org/showthread.php?t=2400034](https://ubuntuforums.org/showthread.php?t=2400034), except my wifi and driver are different, and mine dies only after the *second* suspend/wakeup.  Could it be a problem with the network manager and how it interacts with the driver?

---

### Post by toadtoad on 2018-09-03
Hopefully not, as then I'll have to wait for an update.

---

