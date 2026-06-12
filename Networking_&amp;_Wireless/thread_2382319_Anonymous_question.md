---
title: "Anonymous question"
date: 2018-01-11
forum: Networking &amp; Wireless
---

### Post by genericvii143 on 2018-01-11
Hello, Linux users

I have small questions when comes to VPN and Mac-changer, I am currently use VPN  and it's working just fine but when i change my MAC address it's not really do anything.
Here is the commands i put into the terminal:

JInx ~ # macchanger -s wlo1
Current MAC:   f0:03:8c:71:51:e7 (unknown)
Permanent MAC: f0:03:8c:71:51:e7 (unknown)

JInx ~ # macchanger -A wlo1 
Current MAC:   f0:03:8c:71:51:e7 (unknown)
Permanent MAC: f0:03:8c:71:51:e7 (unknown)
New MAC:       00:05:de:b2:38:ca (Gi Fone Korea, Inc.)

JInx ~ # expressvpn connect itmi
Connecting to Italy - Milan...  100.0%

Connected.
 
Okay, so far so good but when i crosscheck my MAC its going back to normal 

JInx ~ # macchanger -s wlo1
Current MAC:   f0:03:8c:71:51:e7 (unknown)
Permanent MAC: f0:03:8c:71:51:e7 (unknown)

So how that works even tho before i put all those commands  i take ifconfig wl01 down  and they after i did the MAC changer i brought  it back up and then i used the VPA commands  but i guess the MAC is remaining   the same. What em I doing wrong?

Best regards,

---

### Post by TheFu on 2018-01-12
Not all hardware/firmware support changing MACs.  Does yours?

IME, changing of a MAC can only happen when the device is unused.  
```
sudo ifdown {device}
sudo change MAC
sudo ifup {new-device}
```

I haven't looked at this since systemd/udev started changing the device names based on the MAC (arrrrgggggg!!!!!).  Gone are the days of using eth0 for everything. ;)  sniff, sniff.

I cannot test this, sorry. My network setup is a little more complex than just a single device.

Whether wifi NICs are supported in this way or not is a question I cannot answer.  wifi has different CLI management tools at the lower levels.

Anyway, hope this provides some leads for a solution.

---

### Post by genericvii143 on 2018-01-13
Hmmm that's so weird but when i do some pentesting actually its changes so so so weird. If anybody know and have any ideas I'm open to hear it

---

