---
title: "hp-setup can't find my wireless printer"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by Image0fman on 2009-12-22
Printer = HP Officejet J6480, wireless capable

I can install with a usb connection but when I go to setup and wireless connection hp-setup doesn't even detect that my J6480 is wireless capable. I updated hplib and ran the setup correctly. Does anyone know what the issue may be? Thanks in advance

---

### Post by Image0fman on 2009-12-22
> **Image0fman said:**
> Printer = HP Officejet J6480, wireless capable

I can install with a usb connection but when I go to setup and wireless connection hp-setup doesn't even detect that my J6480 is wireless capable. I updated hplib and ran the setup correctly. Does anyone know what the issue may be? Thanks in advance



see attachment

---

### Post by mapes12 on 2009-12-23
There's a GUI front end that lets you manage hplip graphically. In Synpatic select hplip-gui and mark it for installation. Once installed you will have a blue, round HP icon on your task bar. Right click it then select HP Device Manager. When the window opens up select Device>Setup Device. Then the Discovery window opens up to configure the connection type, including wireless.

Good luck.

---

