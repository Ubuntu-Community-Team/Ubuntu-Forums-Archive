---
title: "wire or wireless internet not working"
date: 2015-07-20
forum: Networking &amp; Wireless
---

### Post by Dukenukemx on 2015-07-20
Have a HP zv6000 that I put Ubuntu 15.04 on it and no internet through wire or wireless.  It's connected but can't go online.  I can ping local network devices and even access my router's webpage but no internet.  The wifi is a BCM4318 that I got the driver from using my cell phones usb tether.  The ethernet adapter is a realtek.  Anyone have any idea what this is?

---

### Post by Dukenukemx on 2015-07-21
I fixed the ethernet by manually entering the IP info instead of DHCP but that means Ubuntu 15.04 isn't getting the DHCP from my router.  I haven't done this to my wireless cause I feel wireless really shouldn't.  What's wrong with my DHCP?

**UPDATE**

My Open-WRT router is giving Ubuntu 15.04 IP6 address.  I tried to disable it by editing "/etc/sysctl.conf" and adding these lines.  

```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1 
```

I'm not sure but I feel like it's IPv6 that's causing this problem but I can't disable it.

---

### Post by Bucky Ball on 2015-07-21
Why shouldn't your wireless? There are definite advantages to a static IP, particularly if you are running a home network. :)

If you want to fix wireless, unplug ethernet. You can't have them both active at once. Are you sure your wireless access point/router is set up to serve DHCP IP addresses? Get into the router config page and have a good check in there. You may find an anomaly. 

Another thing you could try: unplug the cable, activate wireless, choose your network and connect to it, click the Network manager icon> edit> check wireless connection and take a note of the IP and other details it has set up there. Are you being asked to authenticate the wireless network when you log on to it on your local machine?

Also, give the output of this command from a terminal, please, between code tags (see the last link in my signature):

```
sudo lshw -C network
```

Thanks.

---

### Post by Dukenukemx on 2015-07-21
> **Bucky Ball said:**
> Why shouldn't your wireless? There are definite advantages to a static IP, particularly if you are running a home network. :)

If you want to fix wireless, unplug ethernet. You can't have them both active at once. Are you sure your wireless access point/router is set up to serve DHCP IP addresses? Get into the router config page and have a good check in there. You may find an anomaly. 

Another thing you could try: unplug the cable, activate wireless, choose your network and connect to it, click the Network manager icon> edit> check wireless connection and take a note of the IP and other details it has set up there. Are you being asked to authenticate the wireless network when you log on to it on your local machine?

Also, give the output of this command from a terminal, please, between code tags (see the last link in my signature):

```
sudo lshw -C network
```

Thanks.
Nevermind I think I fixed the problem.  The router must have been acting up so I unplugged it and plugged it back in and wireless works now.  In fact I'm sending this message wireless through the laptop.  Thanks anyway.

---

### Post by Bucky Ball on 2015-07-21
All good, well done, and please mark the thread as solved. See first link in my signature. Good luck. :)

---

