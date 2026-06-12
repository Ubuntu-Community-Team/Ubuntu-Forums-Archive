---
title: "Unable to Connect via Ethernet"
date: 2016-01-01
forum: Networking &amp; Wireless
---

### Post by robo731 on 2016-01-01
I'm new to Ubuntu and am running Ubuntu Server. I've been able to connect via WIFI, but in the future I will likely want a wired connection instead. Here's my [/etc/network/interfaces]("http://paste.ubuntu.com/14359351/"). I have commented out the p2p1 settings for the time being so that I can connect and post any helpful info to pastebin for the time being.

---

### Post by bab1 on 2016-01-01
> **robo731 said:**
> I'm new to Ubuntu and am running Ubuntu Server. I've been able to connect via WIFI, but in the future I will likely want a wired connection instead. Here's my [/etc/network/interfaces]("http://paste.ubuntu.com/14359351/"). I have commented out the p2p1 settings for the time being so that I can connect and post any helpful info to pastebin for the time being. If you uncomment the p2p1 settings what happens?  What, if any, error messages do you get?  Post the out put of this terminal command```
ifconfig -a 
```

I would not have active the wireless interface while I was using the wired interface.  What happens if you comment out the wireless in favor of the wired connection?  I would reboot the system after making the changes while testing.

---

### Post by robo731 on 2016-01-02
I think I was a little unclear. With my setting the way they are posted above (p2p1 uncommented, wlan0 commented), I am unable to connect at all and the output of ```
ifconfig -a
``` is [this]("http://paste.ubuntu.com/14370531/"). I do not get any error messages, but if I try to do something like ```
ping google.com
``` it gives me an error.

[COLOR=#0000ff][/COLOR][COLOR=#0000ff][/COLOR]I just tested it again now however and it is working fine. I'm not sure what happened. I haven't changed any settings or anything at all, but it's working now.

---

### Post by bab1 on 2016-01-02
> **robo731 said:**
> I think I was a little unclear. With my setting the way they are posted above (p2p1 uncommented, wlan0 commented), I am unable to connect at all and the output of ```
ifconfig -a
``` is [this]("http://paste.ubuntu.com/14370531/"). I do not get any error messages, but if I try to do something like ```
ping google.com
``` it gives me an error.

[COLOR=#0000ff][/COLOR][COLOR=#0000ff][/COLOR]I just tested it again now however and it is working fine. I'm not sure what happened. I haven't changed any settings or anything at all, but it's working now.
When you change the settings you need to force the system to re-read the configuration.  Did you reboot the system like I told you to?  The other way to do this is to restart the networking services after making the change.

---

### Post by robo731 on 2016-01-02
Yeah I rebooted and it's working, but I did the same thing yesterday and it wasn't. I don't know why it's working now when it wouldn't work at all yesterday, considering that nothing has changed.

---

