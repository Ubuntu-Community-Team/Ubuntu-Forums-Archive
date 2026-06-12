---
title: "Is there room for improvement for my WiFi ?"
date: 2019-06-05
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2019-06-05
I am using a 4G hotspot. I connect to the hotspot using WiFi.

I am getting max speed of 2MBPS

I am not sure if my ISP is offering max of 2MBPS or is it something wrong at my end.


Is there room for improvement for my WiFi ?

[http://paste.ubuntu.com/p/sMPnP9Ygpd/](http://paste.ubuntu.com/p/sMPnP9Ygpd/)

---

### Post by TheFu on 2019-06-05
One way to see if it is the wifi or the 4G would be to use the wired connection to the 4G device and see how fast it is.  If it is 2Mbps, then you know it is the 4G doing the limits.  If you see 90 Mbps, then you know the wifi is the issue.

In a dense wifi environment, determining the exact issue is very difficult, thanks to all the other networks and RF in the area.  Concrete walls, floors, buildings are also an huge problem for RF signals.

---

### Post by jeremy31 on 2019-06-05
Can you change the channel of the hotspot to channel 1?  Also see chili555's tips at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)

---

### Post by TheFu on 2019-06-05
> **jeremy31 said:**
> Can you change the channel of the hotspot to channel 1?  Also see chili555's tips at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)

Good catch!  Channel 1 should help.  And if you could get the guy using Channel 2 to move to 6 or higher, that would help too, though ch2 seems weak.

For 2.4Ghz wifi, prefer channels 1, 6, 11 and if you are in Japan, channel 14.  None of those overlap and impact the other channels.

---

### Post by linuxyogi on 2019-06-06
@TheFu

There is no Ethernet port on the hotspot.

@Jeremy31

There is no option to change the channel of the hotspot.

I have done the following

```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

```
sudo nano /etc/default/crda
```

```
REGDOMAIN=IN
```

Disable IPV6 in Network Manager.

Then I disconnected and reconnected using NM speed is still 1.90 Mbps.

---

