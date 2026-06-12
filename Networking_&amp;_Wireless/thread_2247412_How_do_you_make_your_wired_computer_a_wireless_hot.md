---
title: "How do you make your wired computer a wireless hotspot? [Connectify Alternative]"
date: 2014-10-07
forum: Networking &amp; Wireless
---

### Post by Wayne_Crasta on 2014-10-07
I live in a dorm where there is no wifi in rooms but just a wired connection and I want wifi for my iPhone. In Windows, I used [Connectify]("http://www.connectify.me/"), however, I'm not sure what to do for windows. I tried to add a new connection via network manager however, on my phone the network came under the "devices" tab and said it wasn't connected to the internet.

---

### Post by jeremy31 on 2014-10-07
In Ubuntu 14.04 under Network Manager you can select to use as hotspot but not all wifi cards support this from what I have heard

---

### Post by Wayne_Crasta on 2014-10-07
Seems like the same thing happens:
[IMG]http://i.imgur.com/0XQtgcV.png[/IMG]

---

### Post by jeremy31 on 2014-10-07
So what happens if you choose to connect anyway and enter 91.189.94.12 in your iphone browser?

---

### Post by Wayne_Crasta on 2014-10-07
> **jeremy31 said:**
> So what happens if you choose to connect anyway and enter 91.189.94.12 in your iphone browser?
It seems to work but how do I change the network name from Wayne-Linux?

---

### Post by jeremy31 on 2014-10-08
> **Wayne_Crasta said:**
> It seems to work but how do I change the network name from Wayne-Linux?

You should be able to edit the name using network manager, edit connections, hotspot and change the SSID
Or you can probably edit the SSID in this file ```
sudo gedit /etc/NetworkManager/system-connections/Hotspot
```

---

