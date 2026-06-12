---
title: "startup script"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by scottsanpedro on 2007-03-12
Hi, I have belkin wireless network card running via Ndsiwrapper. It works fine.
Only when I reboot I have to go into networking - Configure network. I then double click wlano, then disabled the connection and then re-enable and the card lights come on and everything works fine.

My question..is there a way I can in effect run that manual procedure via a startup script therefore each time the laptop is rebooted the wireless will come on automatically.

Running 6.10 with Pre-N network adapter.

Thanks
Scott

---

### Post by apjone on 2007-03-13
not sure but you could add the following to /etc/rc.d/rc.local

ifdown wlan0
ifup wlan0

---

