---
title: "ueagle-atm and adsl modem light"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by paul77 on 2009-04-06
Hi,
   I have ueagle-atm (device driver for Sagem Fast 800 (an adsl usb modem)) running in my linux kernel (2.6.22-14) and at startup the modem power light comes on but not the adsl light. I have tried configuring the connection by editing:

/etc/ppp/peers/ueagle-atm
/etc/ppp/chap-secrets
/etc/ppp/pap-secrets

and lauching, via pon ueagle-atm, but firefox cannot access the internet presumably because the adsl is not active. Does anyone
know how to progress this?

---

