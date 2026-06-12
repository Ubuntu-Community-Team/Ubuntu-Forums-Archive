---
title: "Can't set Static IP Address on Beaglebone Black"
date: 2015-07-25
forum: Networking &amp; Wireless
---

### Post by webusr1 on 2015-07-25
All,
I've tried changing dhcp to static in the "interfaces" file from dhcp to static as follows:

```

iface eth0 inet static     
address 10.168.1.2     
netmask 255.255.255.0     
gateway 10.168.1.1

```

However, after I reboot then original dhcp addresses stay configured. Are they other files that need to change?

Your help is appreciated.

---

### Post by ajgreeny on 2015-07-26
Have a look at 
[http://ubuntuforums.org/showthread.php?t=1665089](http://ubuntuforums.org/showthread.php?t=1665089)
[http://askubuntu.com/questions/7079/how-do-you-configure-desktop-for-a-static-ip-address](http://askubuntu.com/questions/7079/how-do-you-configure-desktop-for-a-static-ip-address)
which seems to answer your question.

---

### Post by webusr1 on 2015-08-02
In case some has the same issue here's the solution: Look at "am335x_evm.sh"

I think I found the issue with the BeagleBone Black network configuration here:  [http://bugs.elinux.org/issues/91](http://bugs.elinux.org/issues/91)
The fix is:
Disable these 3 lines:
/etc/init.d/udhcpd restart
/sbin/ifconfig usb0 192.168.7.2 netmask 255.255.255.252
/usr/sbin/udhcpd -S /etc/udhcpd.conf
and comment out the stuff for usb0 in /etc/network/interfaces

Now you should be able to configure static IPv4 addresses with interfaces.

---

