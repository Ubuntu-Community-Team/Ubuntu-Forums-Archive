---
title: "Wireless not connecting. Atheros AR5416."
date: 2016-07-21
forum: Networking &amp; Wireless
---

### Post by choaya on 2016-07-21
Hello.

I'm new to Linux and have been throwing my head against the wall trying to figure out how to connect to the internet. The wireless card in question is a Qualcomm Atheros AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] yet when I try to connect to my router which is listed in the network manager thing it either asks me to input the password a half dozen times before failing to connect saying network connection not found or it will simply ask for the password once and do the same thing. It's getting to the point where I'm going to be mumbling my wireless password in my sleep. Meanwhile an ethernet connection simply provides an infinite loop of setting network address then failing with IP configuration was unavailable. As such I have to tether my phone (connected to my router somewhat ironically) to my computer to get internet which isn't ideal of course.

I used the wireless script and have attached it to the post as asked. I hope we can resolve this somewhat annoying problem.

---

### Post by jeremy31 on 2016-07-21
Can you change wifi router settings?  Change encryption to WPA2 only as the script result showed TKIP was being used

---

### Post by choaya on 2016-07-21
Well I went to my router settings and the only 2 options are WPA2-PSK and WPA-PSK/WPA2-PSK. I didn't see anything about TKIP (I don't know what that is either). Anyway nothing changed. I've attached a screenshot of my settings and a new script file in case anything changed on there.

[http://imgur.com/a/muCf9](http://imgur.com/a/muCf9)

---

### Post by jeremy31 on 2016-07-21
TKIP is likely part of WPA, did you restart the router after making the change?

You could also do ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

Can you enable a wireless hotspot from the android phone and see if the laptop can connect?

---

### Post by choaya on 2016-07-22
Yes I restarted the router.
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf


```

Does nothing. Terminal just sits there.

I can't connect to the router with security disabled either. Indeed then only thing working is to tether my phone hotspot doesn't work.

I should note occasionally I get an IP configuration not available error instead of connection not found.

---

