---
title: "MT7610U 0e8d:7610 MediaTek USB Wireless adapter not working in Ubuntu 17.10"
date: 2018-01-03
forum: Networking &amp; Wireless
---

### Post by ilbuonme on 2018-01-03
I am trying to get my MediaTek USB Wireless adapter to work in Ubuntu "Artful" 17.10.

lsusb output:     Bus 002 Device 019: ID 0e8d:7610 MediaTek Inc.
ID:                   0e8d:7610
Chipset:           MT7610U

I tried the following guides/howtos, to no avail:

[LIST]
[*] [http://lugscandiano.org/index.php/Installazione_wireless_usb_chipset_ralink_RT2870](http://lugscandiano.org/index.php/Installazione_wireless_usb_chipset_ralink_RT2870)
[*] The 3rd post in [https://forum.ubuntu-it.org/viewtopic.php?t=216885](https://forum.ubuntu-it.org/viewtopic.php?t=216885)
[*] [https://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card/168046#168046](https://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card/168046#168046)
(I edited  /etc/network/interfaces and added the row "iface wlp2s0 inet manual" to it).
[*] [https://askubuntu.com/questions/965555/ralink-bluetooth-adapter-is-not-detecting-ubuntu-17-10](https://askubuntu.com/questions/965555/ralink-bluetooth-adapter-is-not-detecting-ubuntu-17-10)
which applies to Ubuntu 17.10, my distro.
[*] Through [https://askubuntu.com/questions/874366/usb-wifi-adapter-lsusb-0e8d7610-mediatek#874373](https://askubuntu.com/questions/874366/usb-wifi-adapter-lsusb-0e8d7610-mediatek#874373) I found
[https://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u](https://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u)
... also not working.
[*] [https://ubuntuforums.org/showthread.php?t=2325350](https://ubuntuforums.org/showthread.php?t=2325350)
which directed me to
[http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/](http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/)
which pointed me to [https://bitbucket.org/sanrath/mediatek_mt7610u_sta_driver_linux-64bit/downloads/](https://bitbucket.org/sanrath/mediatek_mt7610u_sta_driver_linux-64bit/downloads/)
But also those drivers did not work (though they had been also recommended by [https://askubuntu.com/questions/716656/how-to-install-driver-for-linksys-ae6000-wireless-usb-adapter](https://askubuntu.com/questions/716656/how-to-install-driver-for-linksys-ae6000-wireless-usb-adapter) and 
[https://www.lffl.org/2016/06/aukey-wf-r2-comodo-adattatore-wireless-pc.html](https://www.lffl.org/2016/06/aukey-wf-r2-comodo-adattatore-wireless-pc.html))
[*] [https://superuser.com/questions/738096/how-to-install-mediatek-mt7610u-rt2860-driver](https://superuser.com/questions/738096/how-to-install-mediatek-mt7610u-rt2860-driver)
which made me edit
~/voluminosi/wireless_adapter/edited-sanrath/sanrath-mediatek_mt7610u_sta_driver_linux-64bit-95fd2aa84ad7/os/linux$ vim config.mk
[/LIST]

If I add
```

blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb

```
to /etc/modprobe.d/blacklist.conf, my internal default wifi card is de-activated, but I am left with no working wireless.

Can anyone please help? Thank you!

---

### Post by chili555 on 2018-01-03
Please see: [https://askubuntu.com/questions/975464/mt7610u-unable-to-install-wifi-driver/975504#975504](https://askubuntu.com/questions/975464/mt7610u-unable-to-install-wifi-driver/975504#975504)

---

### Post by ilbuonme on 2018-01-06
Thank you, sorry for not finding those replies before asking.

---

### Post by chili555 on 2018-01-06
No apology needed. The only reason that I could find and link it quickly is that this device has been one of the very few that my colleagues and I have worked on that won't work at all in any recent kernel. It has haunted me.

---

