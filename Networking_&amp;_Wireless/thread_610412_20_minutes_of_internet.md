---
title: "20 minutes of internet"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by rustyslacker on 2007-11-12
First time on XUbuntu, but I've been an on-and-off Linux user for a couple years. 

I've got a WUSB54GC wireless USB adapter on my Pentium 2 450mhz / 448 MB / Radeon 7000 Compaq Deskpro. I'm using ndiswrapper and everything works great, including internet, for about 20 minutes.

After that, everything quits. The package manager times out, Firefox times out, and Pidgin disconnects. Upon rebooting, everything works for 20 more minutes.

Here is some console output. 
```
connor@deathstar:~$ sudo dhclient wlan0
[sudo] password for connor:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:50:18:35:f8:84
Sending on   LPF/wlan0/00:50:18:35:f8:84
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
connor@deathstar:~$ ndiswrapper -l
rt73 : driver installed
        device (13B1:0020) present (alternate driver: rt73usb)

```

How can I make the connection last?

---

### Post by daengbo on 2007-11-12
I have a similar problem with RALink wireless under installed Gutsy. The cards work fine in Feisty and under the Gutsy live CD. Hmmm.

---

### Post by gb5uqx on 2007-11-12
Just as a matter of interest try this. It works for me and on two other machines I have tried it on. So far no feedback from the forum.

Right click the panel and select add to panel. In the system hardware section select network monitor, add then close. You have to add this as clicking the normal network icon doesn't offer the right settings.

Now left click the new icon and you will see network properties. Click the dropdown and change the setting to loopback device (lo) and close.

---

### Post by rustyslacker on 2007-11-12
It appears to be working. Thanks, gb5uqx. :)

---

### Post by NHaGa on 2007-11-13
This works!!! thank you so much!!

---

### Post by jmw86069 on 2008-05-22
Sorry, but I've searched and tried to install what I thought would work (and it hasn't so far.)

I'm running Mythbuntu with the Xfce desktop. I don't see that panel option, nor have I been able to add it. Can you describe what you're checking for "lo" and what it does? Maybe I can try to do the same by commandline, or try to install something else that will?

Thank you!

---

