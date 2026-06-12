---
title: "Internet connection problem under Ethernet-Lan"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by yas2 on 2016-01-26
[COLOR=#222426][FONT=Arial]On a newly installed Ubuntu 14.04 Machine which is connected to the LAN, I cannot connect to the internet and keep receiving the command: "Disconnected. You are now offline". This is a while on the same machine using Windows 10, I am connected to the internet so there should not be something wrong with my network card. I have tried this option:

```
 sudo service network-manager restart
```

However the problem persists and I cannot connect to the internet. How can I resolve this problem?[/FONT][/COLOR]

---

### Post by andrei90 on 2016-01-26
Your Internet cable comes from a Wifi router?

Did setting up your Internet for the first time require a *username* followed by a *password* ?

If so, please check with your Network Provider whether your using the PPPoE connection configuration.

Please show me the output of 
```
$ ifconfig
```
from your terminal/cli

---

