---
title: "Fiesty bcm4311 issue"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by matt_risi on 2007-04-20
Had connection working properly using guide found here:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29#head-f744e28e6c78eb83d22be77819b130016a8e51f3](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29#head-f744e28e6c78eb83d22be77819b130016a8e51f3)

With use of the "sudo ifup wlan0" and "sudo ifdown wlan0", I was able to use my Broadcom 4311 to access the internet, just as I was in Edgy. However, after a little time, my laptop seems to have "forgotten" what wlan0 is. Here is the output when I use "sudo ifup wlan0":

```
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

Also to be noted is that using the network settings manager, I'm able to both see and connect to my house's wireless connection (shows signal strength), but not get an IP address. Also of interest is that under "Connection Information", my wireless card is listed as (eth0), which does not exist in my "/etc/network/interfaces" list.

Can anyone help me, I'm stuck in Windows until I can get this working.

---

### Post by bdogg64 on 2007-04-20
Great guide here. I have a Broadcom 4311 and this works great. I can help with setup also, if necessary.

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

Hope it helps you too.

B

---

### Post by Kobalt on 2007-04-20
What does this command return : 
```
sudo ndiswrapper -l
```

---

### Post by matt_risi on 2007-04-21
I fixed the problem by editing /etc/iftab to say "wlan0" rather than "eth0", and internet is back up. Anyone have a solution for this "ifup wlan0" "ifdown wlan0" mess?

---

### Post by bdogg64 on 2007-04-21
> **matt_risi said:**
> I fixed the problem by editing /etc/iftab to say "wlan0" rather than "eth0", and internet is back up. Anyone have a solution for this "ifup wlan0" "ifdown wlan0" mess?

Yep, install network manager

Ubuntu
```
sudo apt-get install network-manager-gnome
```

Kubuntu
```
sudo apt-get install network-manager-kde
```

---

### Post by matt_risi on 2007-04-21
Says I already have it installed.

---

### Post by bdogg64 on 2007-04-21
> **matt_risi said:**
> Says I already have it installed.

There should be an network icon in the right corner that you can use to connect to wireless or wired networks. If not you can run

```
nm-applet --sm-disable
```

You can also add that to your session startup programs

---

### Post by matt_risi on 2007-04-21
There is such an icon, but all it does is serve to display what networks are available to me. When I tell it to connect to one, it's unable to. It even shows signal strength and everything, it'd be so nice to get this working.

---

### Post by bdogg64 on 2007-04-21
> **matt_risi said:**
> There is such an icon, but all it does is serve to display what networks are available to me. When I tell it to connect to one, it's unable to. It even shows signal strength and everything, it'd be so nice to get this working.

Does it prompt you for the network key after you click on the network you want to connect to? Or are you trying to connect to an open access point?

---

### Post by matt_risi on 2007-04-21
Always open-access. I always have to do the above commands a few times just to get the internet up, sometimes it takes upwards of 2 minutes, very irritating. Thanks for your continued support bdogg64!

---

### Post by matt_risi on 2007-04-23
Bumpitty-bump.

---

### Post by bdogg64 on 2007-04-23
I have had trouble with open access points also, so I don't really have a solution for you there. I had success if i attempted to connect to an encrypted network (which i had no access to), then trying to connect to an open network with some success.  You could try using the manual configuration instead of the network manager to connect also.

---

### Post by matt_risi on 2007-04-25
Thanks for the help anyway bdogg. It just seems kinda weird that this same wireless card worked (albeit still a pain in the a**) in Edgy, but without nearly as much of the drama.

---

