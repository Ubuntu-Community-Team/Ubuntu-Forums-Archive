---
title: "connects to network but wont pull ip address"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by jaggedseven on 2008-03-15
i just installed 7.10 on my notebook last night. when i was running the install cd i was able to connect to a network and surf. after i did the restart and booted in to the installed copy of Linux i am no longer able to  surf. i can connect to a wired or wireless network but it does not pull an ip address. can someone please help? i am a bit of a newbie. thank you all for take the time to read this.


also if this helps i booted back to the cd and get the same prob. if i format and load windows i can connect with out a prob.

---

### Post by handydan918 on 2008-03-15
Open a terminal and try ```
sudo dhclient
```

---

### Post by jaggedseven on 2008-03-15
there you go. hope this gives you some in site.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:e0:88:4a:67
Sending on   LPF/ath0/00:19:e0:88:4a:67
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:0d:56:38:2a:48
Sending on   LPF/eth0/00:0d:56:38:2a:48
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ubuntu@ubuntu:~$

---

### Post by handydan918 on 2008-03-16
You originally posted > i can connect to a wired or wireless network but it does not pull an ip address

Why do you think you can connect? What does the system tell you?
What does networkmanager list?

---

### Post by jaggedseven on 2008-03-17
it shows me connected but when i try the net it does not load, i go and check what ip i am pulling and i get 0.0.0.0

---

### Post by superprash2003 on 2008-03-17
check this out .. [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html) read the ROAMING MODE part

---

### Post by jaggedseven on 2008-03-28
well thanks all for the help. i found out my prob, it was on the router. i did not have it handing out enough leases.

---

### Post by maljaros on 2008-03-29
> **superprash2003 said:**
> check this out .. [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html) read the ROAMING MODE part

I have searched the blogspot for ROAMING and could only find, under Internet Connection Problems in Ubuntu, that one should start by disabling Roaming Mode.
Hopefully there is more, but where?

---

