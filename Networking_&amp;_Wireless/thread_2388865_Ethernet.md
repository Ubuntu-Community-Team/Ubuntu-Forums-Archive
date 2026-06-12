---
title: "Ethernet"
date: 2018-04-08
forum: Networking &amp; Wireless
---

### Post by spoonsy1480 on 2018-04-08
Hi I’m new to unbuntu and have just installed 16.04 lts when I try to connect by Ethernet it tries to connect to 30 different devices that it then says they are not managed, I have dual gigabyte ports not 30, then it bridges them and the connection is poor, I can connect wirelessly

---

### Post by SeijiSensei on 2018-04-08
Disable the wifi before activating the Ethernet connection and see if that helps.

---

### Post by spoonsy1480 on 2018-04-10
I have done that but in the end I did this [https://askubuntu.com/questions/71159/network-manager-says-device-not-managed](https://askubuntu.com/questions/71159/network-manager-says-device-not-managed)
As I’m using a graphical interface and they clash

---

### Post by rsteinmetz70112 on 2018-04-10
> **spoonsy1480 said:**
> I have done that but in the end I did this [https://askubuntu.com/questions/71159/network-manager-says-device-not-managed](https://askubuntu.com/questions/71159/network-manager-says-device-not-managed)
As I’m using a graphical interface and they clash

Which part of the link you posted did you do?

What's does ```
ifconfig -a
``` say?

What's in ```
/etc/network/interfaces
```?

---

