---
title: "Power management for wifi keeps turning on"
date: 2015-05-03
forum: Networking &amp; Wireless
---

### Post by Thijs_Wouters on 2015-05-03
Hi

I am using ubuntu 15.04.
I have a problem with my wifi. I cannot connect to my network. Now the reason this is happening is that the power management was turned on. So I tried to turn it off.
I tried with

```
sudo iwconfig wlan0 power off
```

 This turns off the power management. Then when I connect to my network, it turns it back on.
I tried creating a service that turns the power management off. Power management is now off, but when I reconnect. It gets turned on again.
Does anybody have a idea why this is happening? If you need more info, ask.

---

### Post by Thijs_Wouters on 2015-05-04
It's getting stranger.
I am at work now. The wifi connects without issue. Power management is turned off.
Is there something in the wireless router that could be turning on the power management?

---

### Post by wildmanne39 on 2015-05-04
Try:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by JMO707 on 2015-05-25
I have exactly the same problem. Using Ubuntu GNOME 15.04. Even with the script given by Wild Man on power.d, Power Management keeps turning on.

---

