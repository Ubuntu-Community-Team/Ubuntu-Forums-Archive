---
title: "Ubuntu came with no wifi connection"
date: 2021-10-17
forum: Networking &amp; Wireless
---

### Post by jorgge on 2021-10-17
I installed ubuntu but I can't connect to wifi because there is no option for that, why? The same thing happend to Mint and PopOs. I wanted to try Linux but I'm about to go to Windows. It's very disappointing.

---

### Post by chili555 on 2021-10-17
Linux will, indeed, always have wireless driver issues, but for several reasons that may not be apparent to all of us. First, new devices are developed and released every day. The manufacturers are in a constant arms race to have a better device with more features and, often, cheaper. In almost every case, they have almost no concern for the 3% or so of Linux users and therefor don't provide a working driver.

Second, most new Linux users come to the party with what they have now that they bought with working Windows drivers. That device may work well or not at all in Linux. In many cases, perhaps most cases, there is a working wireless driver installed for common devices. In a few cases, like yours, there is probably not.

We can identify and fix your wireless with a bit of information. Please open a terminal Ctrl+Alt+t and run:

```
lspci -nnk | grep 0280 -A3
rfkill list all
```

Post the result and we'll proceed.

---

### Post by johnlrose on 2021-12-18
I'm in the middle of bulldozing and repaving a MacBookPro8,1 ("Early 2011") to single-boot with Kubuntu 20.04 and I had a similar problem. No WiFi connection to select that I could find.
Then I poked around in Application Launcher / System Settings /  clicked on Driver Manager / clicked on "Relaunch Driver Manager" (password required)
The one of the tabs in Driver Manager's "Software Sources" window was "Additional Drivers" and from there I selected "Using Broadcom 802.11 ..." etc. (it was originally set to "Do not use the device")
I clicked "Apply" and then all was well. My router showed up in the "Networks" pop-up in the System Tray. \\:D/

---

