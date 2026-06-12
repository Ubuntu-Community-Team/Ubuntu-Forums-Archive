---
title: "ADSL USB Router"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by pointabhishek on 2006-09-30
plz tell me how to use ADSL USB Router for internet using ubuntu
6.06 Dapper
i dont have ethernet

---

### Post by dmizer on 2006-10-03
i think you mean an adsl usb modem rather than adsl usb router.

need lots more information.  what brand of modem is it?  does it have a model number?  post the output of:
```
dmesg | grep USB
```

don't expect much though.  usb modem's are quite a challenge, and as far as i'm concerned ... worthless.  if you can, your absolute best bet is to go out and get a real ethernet modem and use it instead.  then there will be no need to make sure you have the drivers for your modem.

also, sometimes you can pester your internet provider into giving  you a real modem.

usb was never designed to carry internet traffic.  it's too slow, and unstable in any operating system including windows.

---

