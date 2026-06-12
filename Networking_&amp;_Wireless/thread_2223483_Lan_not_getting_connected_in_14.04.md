---
title: "Lan not getting connected in 14.04"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by arka.sharma on 2014-05-11
Hi All,

Today I installed 14.04x86 on my Lenovo G570 laptop and I see that lan port light is always on and it doesn't connect to ethernet if I plug the cable in. However I am able to access Wifi. I doubted that port has gone bad but I have Win 7 dual boot and in Win 7 lan is getting connected.Need some help on this as I need to connect to lan as Wifi is not always available for me.

Regards,
Arka

---

### Post by TheFu on 2014-05-11
What is the output from
* ifconfig
* route

And is the appropriate driver loaded for your ethernet card?

---

### Post by arka.sharma on 2014-05-11
Hi,

I haven't installed any driver separately I just installed 14.04. And I also see that light in the lan port always on. Please find the attached output of route and ifconfig.

Regards,
Arka

---

### Post by arka.sharma on 2014-05-11
One more thing I would add that in connection setting I see IPv4 method is DHCP and IPv6 method is also Automatic

---

### Post by TheFu on 2014-05-11
Looks like the driver is enabled, but not configured. Disable the wifi and configure the LAN side. eth0 is the device you want. I don't use the Ubuntu GUI much, so can't describe how-to do that.  Isn't there a network settings tool somewhere in unity?

If that doesn't work, perhaps it is a bad port, bad cable or bad router port?  None of these are very likely, just something to check.

---

### Post by arka.sharma on 2014-05-11
> If that doesn't work, perhaps it is a bad port, bad cable or bad router  port?  None of these are very likely, just something to check.
But I am able to connect to ethernet in Windows.

---

### Post by TheFu on 2014-05-11
Did you disable the wifi and restart the networking again? What do the wired ethernet settings look like? Which tool is being used to configure them?  Since I work on servers, I usually edit the /etc/network/interfaces file directly.  On laptops, I use wicd-curses .... don't expect these are ideal for your needs, however.

Could the router be out of dhcp reservations?  I limit "guests" to 5 on my network, so with 2 friends over with smartphones and laptops, those are gone quick. Could that be it?

---

### Post by spynappels on 2014-05-11
The simplest way to test this is to disable the Wireless (perhaps using the hardware switch if there is one), plugging the ethernet cable in and assigning a temporary IP address from the command line, to check that the cable, ports and TCP stack are all correct. To do this, run the following from a terminal (will probably need sudo):

```
ip addr add 192.168.1.252/24 dev eth0
```

This should complete with no errors and then you can verify connectivity to the router by pinging it:

```
ping 192.168.1.1
```

If the above works, then its probably a DHCP issue.

---

