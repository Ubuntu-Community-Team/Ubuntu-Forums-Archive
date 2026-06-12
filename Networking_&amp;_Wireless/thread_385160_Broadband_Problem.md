---
title: "Broadband Problem"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by petroskhan on 2007-03-15
This problem may have been elsewhere; if it has been, I do apologize.  Also, I am sort of new to Ubuntu/Linux, but it's love at first sight, and I am NOT going back to Winblows.

Ok, the problem is this:  I have (just yesterday) installed Ubuntu 6.06 on a friends older machine, for his niece to use for homework, net surfing, etc.  The computer is a Dell Dimension 4100.  The install and everything went great, no problems at all.  Now, she has broadband service from Comcast, and on another computer in the house, the net is working fine, but on the Ubuntu machine, when she plugs in the computer to the modem, no internet service.  I have checked under networking, and it shows that the ethernet connection is active, but still, the browser can't find the net.  

Help?

---

### Post by chili555 on 2007-03-15
Today, I feel lucky! Please let us know what happens when you issue the following commands: ```
sudo ifdown eth0
sudo dhclient eth0
ping -c3 www.google.com
```

If I was not so lucky, please post back the results of: ```
ifconfig
cat /etc/network/interfaces
``` Thanks.

---

### Post by petroskhan on 2007-03-15
Well, keep on feeling lucky.  I don't know what those first two commands do, but after running just the first two, it didn't change anything.  I ran the second one again, then the third (the ping).  I opened the browser, and...voila!...success.  

Today is OUR lucky day.  I have rebooted, to confirm it's working, and it's now, at this moment, downloading updates.

Thanks a LOT for this great advice and help.  You're my hero of the day.

---

### Post by chili555 on 2007-03-15
> I don't know what those first two commands doThe first one shuts down your wireless interface and the second asks your router/modem/whatever for a new (DHCP) lease on life.

Glad it worked. It is good to be the sensai.

---

