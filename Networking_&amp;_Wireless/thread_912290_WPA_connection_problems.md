---
title: "WPA connection problems"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by redneck1980wi on 2008-09-06
I bought a new wireless N router to replace my old G one and now I cannot connect when using WPA of any kind. WEP works fine, as does an open connection. The same laptop works with WPA through Vista so it isnt the router. I can see the WPA connection throught NetworkApplet but cannot connect. Any ideas?

---

### Post by spd106 on 2008-09-06
It's usually a good idea to check the /var/log/syslog for error messages in order to narrow down the search.

If you're averse to the terminal then you can also see the log through System -> Admin -> System Log.  Scroll down to the bottom to seee the latest message. This viewer will also update with more messages as you try to re-connect.

Feel free to post anything here that you don't understand.

It might also be a good idea to post a bit more information about your hardware type/brand and driver.

---

### Post by redneck1980wi on 2008-09-06
here's what I have

Sep  6 15:39:05 jacob-laptop kernel: [   49.645648] bridge-eth0: already up
Sep  6 15:39:05 jacob-laptop kernel: [   50.000603] bridge-wlan0: already up
Sep  6 15:39:19 jacob-laptop kernel: [   56.520993] NET: Registered protocol family 10
Sep  6 15:39:19 jacob-laptop kernel: [   56.521273] lo: Disabled Privacy Extensions
Sep  6 15:39:19 jacob-laptop kernel: [   56.521963] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  6 15:39:19 jacob-laptop kernel: [   56.522293] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  6 15:39:19 jacob-laptop pulseaudio[6137]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Sep  6 15:39:19 jacob-laptop pulseaudio[6137]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Sep  6 15:39:19 jacob-laptop pulseaudio[6137]: alsa-util.c: Cannot find fallback mixer control "Mic".
Sep  6 15:39:30 jacob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Sep  6 15:39:32 jacob-laptop kernel: [   63.982605] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Sep  6 15:39:32 jacob-laptop kernel: [   63.982633] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Sep  6 15:39:33 jacob-laptop kernel: [   64.481039] NET: Registered protocol family 17
Sep  6 15:39:37 jacob-laptop kernel: [   67.602346] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Sep  6 15:39:37 jacob-laptop kernel: [   67.602375] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Sep  6 15:39:37 jacob-laptop kernel: [   67.634513] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Sep  6 15:39:37 jacob-laptop kernel: [   67.634689] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Sep  6 15:40:52 jacob-laptop kernel: [  104.316336] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


it is a HP laptop with a broadcom wireless card, using ndiswrapper

---

### Post by redneck1980wi on 2008-09-08
Bump

---

