---
title: "Wireless Works: No Signal!"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2008-10-06
I have Hardy on a desktop with a Linksys wireless card.  I got it configured and got it to attach to the wireless router thru the SSID, but the wifi connection icon to the upper right of the screen shows that I have a 0% connection.  I got a new Linksys router with enhanced wireless range, but no good.  My Windows laptop gets a connection (I am using it to write this post while sitting at the Linux box)).  How can one wifi card be getting a signal but the other not?  Is the problem the OS, the driver, the card, what?  HELP!

---

### Post by willca on 2008-10-07
Hello

Never relied much on the gui stuff. But here is how I would verify if thats true.

iwconfig | egrep "Bit Rate|Link"

---

### Post by sjrlaw on 2008-10-07
Thanks, Willca.  I did that and got the following:

```

lo          no wireless extensions
eth0        no wireless extensions
wmaster0    no wireless estensions

Link quality: 0    Signal level: 0   Noise level: 0
```

I get the feeling it is saying the same thing as the GUI icon in GNOME.  No signal.  Doesn't explain why I get one with my Windows laptop.  Any ideas or insights?

---

### Post by willca on 2008-10-07
It normally gives that "0" signal strength or whatever when you are not associated with any AP.

check if your wifi nic is even seeing a wireless network around.

sudo iwlist wlan0 scan

---

### Post by sjrlaw on 2008-10-08
Willca:

I will do that and let you know what happens.  However, I would note that when I mouse over the GUI icon, it does give the SSID for the router with a (0%) connection.

Steve

---

### Post by Kevbert on 2008-10-08
Please post the output of ```
iwconfig
```

---

### Post by sjrlaw on 2008-10-09
Willca:

The output for the scan was;

```
wlan0   Interface doesn't support scanning : Network is down.
```

Keybert:

iwconfig showed:

```

lo        no wireless extensions

eth0      no wireless extensions

wmaster0  no wireless extensions

wlan0     IEEE 802.11g   ESSID:""
          Mode: Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit: 7  RTS thr: off  Fragment thr=2346 B
          Link Quality: 0  Signal Level: 0  Noise Level: 0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0  Missed beacon:0

```

Looks like problem could be unassociated access point?

Again, when I mouse over the GUI icon for the wifi connection, it says: "Wireless network connection to 'exit27' (0%)"

Thanks for your help.

Steve

---

