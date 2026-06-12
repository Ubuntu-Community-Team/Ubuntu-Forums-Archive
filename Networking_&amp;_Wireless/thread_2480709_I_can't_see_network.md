---
title: "I can't see network?"
date: 2022-11-07
forum: Networking &amp; Wireless
---

### Post by geordiejohn on 2022-11-07
Hello I have just installed xbuntu on my mac mini but the network icon has an x on it so I can't find my network.
Any ideas how to find my network please?
Thank you.

---

### Post by chili555 on 2022-11-07
Is your expected method of connecting wired ethernet or wireless? Please clarify. For the moment, let’s assume wireless.

Do you have a working wireless interface? From the terminal:

```
iwconfig
```

Is the Airplane Mode switch set to enable the wireless radio?

```
rfkill list all
```

If there is an interface, let’s see if it scans:

```
nmcli device wifi list
```

If there is an interface but it doesn’t scan, check for interesting clues in the log:

```
sudo dmesg | grep wlp3s0 
```

Of course, substitute the interface you found above in iwconfig if not wlp3s0.

If there is no wireless interface, let’s see what your device is and try to associate a driver:

```
lspci -nnk | grep 0280 -A3
```

If your device is USB, instead, run:

```
lsusb
```

If, as I suspect, the wireless device in your Mac Mini is a Broadcom, please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

Once we know the results of the above, we’ll be in a better position to propose a solution.

---

### Post by geordiejohn on 2022-11-07
Yes wireless.

---

### Post by geordiejohn on 2022-11-07
Iwconfig says no wireless extensions.
Rfkill says soft blocked no
Hard blocked no
Nmcli device WiFi list gives nothing back

---

### Post by chili555 on 2022-11-07
How about:

```
lspci -nnk | grep 0280 -A3
```

Is it a Broadcom?

---

### Post by geordiejohn on 2022-11-07
Yes Broadcom?

---

### Post by chili555 on 2022-11-07
> **geordiejohn said:**
> Yes Broadcom?Here is how you can install the driver: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by geordiejohn on 2022-11-07
Thank you.

---

