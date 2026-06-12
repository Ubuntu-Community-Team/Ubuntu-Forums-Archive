---
title: "wireless will not connect"
date: 2015-09-23
forum: Networking &amp; Wireless
---

### Post by Daniel_Devor on 2015-09-23
Ubuntu 14.10 The wireless 'button' indicates that the system is trying to connect and the names of several access points are shown. Connection is never completed and I need help in running down the problem. The only clue that I have at this time is when going into  recovery mode and then 'enable networking ' I get "modem manager [915] <warn> could not find support for device at '/sys/devices/pci . . . not supported by any plugin". That may or may not be much of a lead to problem solving. Suggestions will be greatly appreciated.

---

### Post by nknwn on 2015-09-23
Have you tried to connect via the terminal?
Try:
sudo nmcli dev wifi connect **yournetworknameSSID** password **yourPassword**

---

