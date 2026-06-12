---
title: "Switching access points from command line?"
date: 2015-02-12
forum: Networking &amp; Wireless
---

### Post by jimford on 2015-02-12
I'm using a Transcend WiFi SD card in a camera, which behaves as an access point (essid WIFISD).

I've been switching from my router (essid dd-wrt) to the WiFi card using the network manager applet so I can download images, but would like to do it from a command line, so I can automate the procedure.

I've had a fiddle with iwconfig without any success, and I'm not even sure if this is the way to go.

Does anyone have a suggestion of how I can switch between the access points from a command line, please?

Jim

---

### Post by steeldriver on 2015-02-12
You can try

```

nmcli con down id "*OLD CONNECTION NAME*" && nmcli con up id "*NEW CONNECTION NAME*"

```
or
```

nmcli con down uuid *UUID1* && nmcli con up uuid *UUID2*

```

where the connection NAMEs and/or UUIDs are obtained from

```

nmcli con list

```

---

### Post by jimford on 2015-02-12
Looks good!

I'm not familiar with nmcli, so I'm going to give it a try.

Many thanks for the reply!

Jim

---

