---
title: "gnokii with Nokia 6235 via DKU-2"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by gray380 on 2006-09-22
Hi All!

Is there any possibility to make life better? I mean can I use gnokii with Nokia 6235 via DKU-2 cable?

I have made following attempt:

Some settings from my .gnokiirc

```
port = /dev/ttyACM0
model = 6510
connection = dku2
```

Some results:

```
~$ gnokii --identify
GNOKII Version 0.6.12
IMEI         : (unknown)
Manufacturer : Nokia
Model        : (unknown)
Revision     : (unknown)

```

```
~$ gnokii --monitor
GNOKII Version 0.6.12
Entering monitor mode...
Timeout: aborting command ``/usr/lib/gnokii/gnokii'' with signal 9
/usr/bin/gnokii: line 16:  7864 Killed                  timeout $TIMEOUT $BINARY "$@"
```

Any thoughts?

brg,
Serhiy.

PS I have made a question in a correct forum?

---

### Post by lxop on 2007-05-17
Hi, I have the exact same phone, did you have any luck connecting it?

---

### Post by dannystaple on 2007-06-27
Do not use the dku2 driver, but rather the dku2libusb. Read here for more info: [http://www.gnokii.org/docs.shtml#dku2](http://www.gnokii.org/docs.shtml#dku2)

My phone (a 6320i) was at /dev/ttyACM0 when connected. 
I am finding I have to run gnokii with sudo, even though my user is part of the daillout group - annoying.

---

