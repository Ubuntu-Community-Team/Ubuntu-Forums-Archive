---
title: "Drivers"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by baguahsing on 2010-06-05
Network Manager reports that I am using the rtl8187 driver.  Where exactly is that file located?  If I do a search, many files and folders show up.  Can I modify a driver file?  Two small things, one my data rate is 36M at best instead of 54M.  Second, I can't walk out my office without loosing my connection.  I have a 2wire router which is set at max power, 54M, channel 6, WPA/WPA2, 802.11b/g.  Iwlist reports that the txpower on the laptop is 500mW, which I think is the max setting.  I think the issue could be sensitivity but I don't know what an acceptable value would be.  The best stable data rate is 48M, not 54M.  Can anyone help me?

---

### Post by 3rdalbum on 2010-06-05
No, you wouldn't modify the driver itself. It's a compiled file and not human-readable; besides, you don't need to modify the driver anyway.

The iwconfig command can change parameters of your wireless device on-the-fly. For more information, see:

```
man iwconfig
```

The RTL8187 cards shouldn't be that fragile. I'm assuming you're using Ubuntu 9.10 or 10.04? If you are still on 9.04, then install the Linux Backports package from Synaptic (linux-generic-modules-jaunty-backports?) because the driver that ships with Ubuntu 9.04 is weak, and the driver in the backports package is better.

---

### Post by baguahsing on 2010-06-05
I'm using 10.04 netbook remix.  I have seen alot of posts about wifi problems.  I can maintain a connection throughout my whole house using windows so, I figure it has to be the setup (driver) being used in linux.  Using iwconfig will change settings but are they permanent or just for the current session?

---

