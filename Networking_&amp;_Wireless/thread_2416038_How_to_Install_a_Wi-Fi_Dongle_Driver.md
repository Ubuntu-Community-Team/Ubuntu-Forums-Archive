---
title: "How to Install a Wi-Fi Dongle Driver"
date: 2019-04-04
forum: Networking &amp; Wireless
---

### Post by mvahedi on 2019-04-04
Hi everybody

                    i have a 802.11n WiFi Dongle


  in the cd there is a driver for linux that i put link bellow


  i want install this driver with ./configure & make & make install BUT [B]I CAN'T
[/B]

  please please please Help me...

---

### Post by TheFu on 2019-04-04
Better to use Ubuntu drivers if they are available. Start by figuring out what chip is actually in the dongle.  I'd use **sudo lshw -C network** to determine that. It shows the device, chip, current driver and driver version.

Also, the specific release of Ubuntu you are running would be helpful. How to handle things like this are very specific to the release and kernel involved.

---

### Post by jeremy31 on 2019-04-08
Moved to Networking and Wireless

---

