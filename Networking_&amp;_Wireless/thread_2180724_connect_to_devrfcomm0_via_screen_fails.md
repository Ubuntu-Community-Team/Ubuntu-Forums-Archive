---
title: "connect to /dev/rfcomm0 via screen fails"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by jimbolaya on 2013-10-14
I am trying to connect to an HC-06 bluetooth serial port.

I've set up my /etc/bluetooth/rfcomm.conf with the appropriate (bluetooth) MAC address and set "bind no".

To get the device connected, I run:

```
bluetooth-agent <PIN> &
```

where <PIN> is the pin I've set up for the device.

Then I run:

```
rfcomm bind rfcomm0
```

If I then try to connect using screen:

```
screen /dev/rfcomm0
```

it sometimes connects without complaint, but often will complain:

```
Cannot open line '/dev/rfcomm0' for R/W: open() blocked, aborted.
Sorry, could not find a PTY.
```

If I use minicom to connect, it doesn't normally complain. I've also found that if I connect via minicom first, then usually connecting via screen will work after that. Does anyone have any ideas on what the issue is?

James

---

