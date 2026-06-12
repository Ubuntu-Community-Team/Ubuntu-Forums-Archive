---
title: "How to set up Internet Connection Sharing over USB..?"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by KingNeil on 2016-09-14
Is there any way to set up Internet Connection Sharing using USB..?

For example, with an Android phone, you can share its connection with a computer using so-called "tethering".

But I want to "tether" my laptop's internet connection to another computer, using USB.

How do I do this..?

Thanks

---

### Post by SeijiSensei on 2016-09-14
I don't think that's possible. We've owned four or five Android phones in my home; none of them offered network services via the USB port, only wifi or cell services.

On rereading your post, it sounds like you want to connect one PC to your laptop then "masquerade" it out to the Internet.  You can do this if you connect the computers together with an Ethernet cable.  (USB won't help here.)  I use this trick to send my television's network connection out to the Internet via a PC.  On the PC I run this script:
```

#!/bin/sh

EXT_INT=wlan0
IN_INT=eth0
IN_IP=192.168.101.1
IN_MASK=255.255.255.0
IN_BC=192.168.101.255

# ==========

# determine the IP address of this machine via the EXT_INT interface
EXT_IP=$(ifconfig $EXT_INT | grep 'inet addr' | awk '{print $2}' | sed 's/addr://g')
#echo "EXT_IP=$EXT_IP"
if [ "$EXT_IP" = "" ] 
then
     # bring down IN_INT if unassigned and flush the iptables rules
     ifconfig $IN_INT down
     /sbin/iptables -t nat -F
fi    

# configure the Ethernet adapter
ifconfig $IN_INT $IN_IP netmask $IN_MASK broadcast $IN_BC

# masquerade traffic arriving on eth0 out to the Internet
/sbin/iptables -t nat -A POSTROUTING -o $EXT_INT -j SNAT --to $EXT_IP

```
This assigns the address 192.168.101.1 to the PC's Ethernet port.  The TV  is configured as 192.168.101.2 with 192.168.101.1 as its "gateway."

This script runs at startup via an entry in /etc/rc.local.

---

### Post by RobGoss on 2016-09-14
Using Android devices there are a few apps in the Play-store one come to mind is Foxfi, [https://play.google.com/store/apps/details?id=com.foxfi&hl=en](https://play.google.com/store/apps/details?id=com.foxfi&hl=en) it allow you to share your devices  internet connection with other devices or even a PC. I use it when I net is down in my house for any reason.

---

