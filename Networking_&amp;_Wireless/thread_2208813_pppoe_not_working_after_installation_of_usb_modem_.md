---
title: "pppoe not working after installation of usb modem driver"
date: 2014-03-02
forum: Networking &amp; Wireless
---

### Post by Alexander_Orhean on 2014-03-02
Hello,

I am running ubuntu 12.04 lts (64-bit), and I am having difficulty in connecting to a dsl(pppoe) connection. I tried to connect using Network-Manager and pppoeconf but it didn't work. Initialy I managed to connect using Network Manager but after I had installed the software for my usb modem(ZTE mf667), any atempt to connect to the dsl(pppoe) connection failed. The mobile broadband, wireless and wired connections work only the pppoe won't connect. I have searched the forum for a solution but I haven't found one, yet.

I have reinstalled network-manager, wvdial, usb modem driver, dnsmasq, usb-modeswitch; and I have tried resetting network settings, but all in vain...

---

### Post by Alexander_Orhean on 2014-03-05
Problem solved. All I did was to move /etc/ppp/options to /etc/ppp/options.backup, then recreate the dsl connection using network-manager.

---

