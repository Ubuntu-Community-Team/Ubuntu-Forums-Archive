---
title: "Can not connect to the internet using a patch cable"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Viva on 2010-05-25
I previously used a USB cable to connect to the internet, but decided to try a patch cable instead. Both windows and linux recognise the connection, but throw an authentication failure. I'm currently back using the USB connection, but I don't want to use it too long because I notice a voltage fluctuation and screen flicker with it.

ifconfig:

---

### Post by CharlesA on 2010-05-25
What kind of internet connection do you have?

Sounds like you are using PPP to authenticate to your ISP.

If you are using DSL, you can probably configure the connection using Network Manager or WICD.

---

### Post by Viva on 2010-05-26
It gave me an authentication failure because the MAC address has changed and my ISP checks for it while authenticating. Called them and got my mac address changed in their database. Everything's working fine.

---

### Post by CharlesA on 2010-05-26
Ah. That makes sense then. Simple fixes are the best ones. :-)

---

