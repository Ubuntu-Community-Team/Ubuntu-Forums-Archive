---
title: "Connecting to Internet Dialup"
date: 2005-08-12
forum: Networking &amp; Wireless
---

### Post by pink_guitar on 2005-08-12
I have the live cd and can't get on the internet using dial up. wvdial command complains it can't find the modem. I have an external modem.

---

### Post by jasmuz on 2005-08-12
use pppconfig, and make sure to point the port the external modem is using.

---

### Post by pink_guitar on 2005-08-13
Jasmuz,

Thanks for taking an interest in my issue.

I tried sudo pppconfig. I also added a symbolic link using the following command

sudo ln -s /dev/ttyS0 /dev/modem.

then wvdial gave a new message

warning section [dialer defaults] does not exist in wvdial.conf

sorry no modem was detected is it in use by another program did you configure it properly with setserial.

---

