---
title: "urgent help plz"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by baba21 on 2007-05-22
hi there

i am new here  i have btvoyager 2091 router ,connecting to internet trough wire is ok, but when i tried to connect to wireless  the conected status is connected excellent but when i clik on internet keep saying the page cannot be display.

i like you to help me on that plz

---

### Post by codesplice on 2007-05-22
How do you have the router configured?  DHCP?  Wireless security of any sort?

Also, try launching a terminal and pinging your router's IP address.  Then ping your ISP's default gateway (probably listed on the Status screen of the router configuration).  Then ping google.com.  This'll help you to isolate where along the path the issue might be.

---

### Post by baba21 on 2007-05-22
didn't help me ur answer is not clear could u be more specifique i mean more information.

where to find

---

### Post by codesplice on 2007-05-22
**bab21**,
I'm not familiar with that router, so I can't really help you as far as configuring it.  

It would be helpful if you could try pinging a couple of different addresses.

To do that, click Applications-->Accessories-->Terminal.  

Then 
```

ping 192.168.1.1
```
replacing that IP with that of your router.  Then do the same for your ISP's gateway IP address (available from your router configuration status screen), and also for an external webpage.  

Let me know how far you can ping before the packets are lost.

Good luck!

---

### Post by baba21 on 2007-05-22
packet send 4 received 0 lost4 100%

---

### Post by codesplice on 2007-05-22
> **baba21 said:**
> packet send 4 received 0 lost4 100%

to which IP?  If that was your router's IP (make sure you have the right address), then you're not connected to your router.  Double-check your wireless settings.

---

### Post by baba21 on 2007-05-22
address type: manually configure
ip 192.168.1.3
subnetmask 255.255.255.0
default gateway 192.168.11.0
prefered dns server 192.168.11.0

---

### Post by ugm6hr on 2007-05-22
The most likely problem is with the wireless connection, since you can get online using the wired network (I assume via the same router).  If Network Manager thinks its connected, it will most likely be your router's security settings.

Easy to check - connect by wired ethernet and start firefox, then enter:
192.168.1.1
as the web address (assuming this is the correct router IP - which I think most BT routers use).

You should get to your wireless routers setup page (you may be asked for *username* / *password* - the default is often *admin* / *admin)*

Then look for something like Wireless Advanced Settings, Wireless Security, Wireless Authentication, MAC Filter, Wireless Association in the settings, and let us know what's enabled and what's disabled.  I have a strong suspicion that this may be a MAC filtering issue - is this enabled?

EDIT: Just seen new post above - looks like it's 192.168.11.0 for you - not 192.168.1.1 - try that instead (assuming that it's not a misprint).

---

