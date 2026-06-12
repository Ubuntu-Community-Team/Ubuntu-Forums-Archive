---
title: "Wlan conected, not working?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by mormor on 2008-08-10
Possibly a very easy fix.

Leaching Wlan from landlord, got passfrase and all.

Got connected, full signal strenght.

But cant get on internet through that connection. :( And dont know why.

help apriciated.

---

### Post by Mytth on 2008-08-10
Check your password for wlan, you may have selected the wrong security settings.

---

### Post by mormor on 2008-08-11
As you can see I get connected to the network.

But I can not connect to internet even though i am conected to the network. I am a bit lost here tbh. ANd I think its a matter of a small fix.

Here is a screen
[IMG]http://www.b3ta.cr3ation.co.uk/data/png/6703.screenshot1.png[/IMG]

---

### Post by mormor on 2008-08-11
Anyone please?

[IMG]http://www.b3ta.cr3ation.co.uk/data/png/0055.screenshot.png[/IMG]

---

### Post by Mytth on 2008-08-11
Perhaps you must connect your router to the internet through the web portal, I suggested that as i had a friend with a simmillar problem on mac, who could connect but not to the internet, it was because his connection was set to 128 bitt hex instead of ASCII.
PS, you should blur your mac adresse, its not good to give it away on the internet ;)

---

### Post by Crafty Kisses on 2008-08-11
That's weird, post the following output of:
```
iwconfig
```

---

### Post by cariboo on 2008-08-11
Could you post the output of:

```
route -n
```

Your output should look something like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

My gateway is 192.168.1.1, I don't see any gateway in any of the screenshots you've shown us.

Jim

---

