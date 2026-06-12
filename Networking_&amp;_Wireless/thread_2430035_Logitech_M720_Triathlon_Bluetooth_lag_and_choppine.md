---
title: "Logitech M720 Triathlon Bluetooth lag and choppiness on Kubuntu 19.04"
date: 2019-10-26
forum: Networking &amp; Wireless
---

### Post by irradiated on 2019-10-26
Hi,

I recently purchased a Logitech M720 Triathlon to use between two computers, on my desktop off of the usb dongle and on my laptop via Bluetooth. It works fine under Windows on both computers by either USB or Bluetooth, and fine on Pop_OS by USB on my desktop, but it is working very poorly on my Kubuntu 19.04 install on my laptop through Bluetooth. It feels laggy and unresponsive, but it pairs and seems to work okay otherwise, it's just slow and choppy, with a lot of acceleration. I've tried as many solutions as I could find through Google searches, but nothing has affected it so far.

Here's a few of the solutions I remember trying:

[https://askubuntu.com/questions/663500/ubuntu-14-04-bluetooth-mouse-lags-time-by-time](https://askubuntu.com/questions/663500/ubuntu-14-04-bluetooth-mouse-lags-time-by-time)

[https://askubuntu.com/questions/1090149/bluetooth-mouse-lags-after-upgrading-to-18-10-cosmic/1090150](https://askubuntu.com/questions/1090149/bluetooth-mouse-lags-after-upgrading-to-18-10-cosmic/1090150)

I've tested every available mouse polling rate I could by running the commands ```
[FONT=verdana]sudo modprobe -r usbhid && sudo modprobe usbhid mousepoll=x[/FONT]
```

I've tried Bluedevil, Blueman, and purging and reinstalling Bluez.

This mouse is great otherwise, but I really need it to work under Linux or there's not much point in having it. 

Any help is much appreciated, just let me know if you need any diagnostics or further info.

Thank you!

---

### Post by irradiated on 2019-10-26
After a lot of searching and frustration I finally found the answer, so I'll post it in case anyone else has a similar problem with their Bluetooth mouse.

From: [https://wiki.archlinux.org/index.php/Bluetooth_mouse](https://wiki.archlinux.org/index.php/Bluetooth_mouse)

```
[FONT=sans-serif]If you experience mouse lag you can try to increase the polling rate. See [/FONT][Mouse polling rate]("https://wiki.archlinux.org/index.php/Mouse_polling_rate")[FONT=sans-serif] for more information.[/FONT][FONT=sans-serif]You can try to set the minimum/maximum latency for the mouse in BlueZ [[1]]("https://bbs.archlinux.org/viewtopic.php?pid=1860951#p1860951"):[/FONT]
[FONT=sans-serif]Add or modify the following section in /var/lib/bluetooth/<mac-of-your-adapter>/<mac-of-your-mouse>/info (adapt the path accordingly):[/FONT]
[ConnectionParameters]
MinInterval=6
MaxInterval=9
Latency=44
Timeout=216


```

Reboot, and mouse lag is gone. Thanks anyway, and I hope this helps someone avoid the same frustrations I was having!

---

