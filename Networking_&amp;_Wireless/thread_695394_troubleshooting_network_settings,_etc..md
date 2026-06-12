---
title: "troubleshooting network settings, etc."
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by worthspending on 2008-02-13
I am trying to install Ubuntu on a brand new ASUS laptop G2S-B2.  I just received the laptop today 02/12/2008.  The installer fails to recognize the network interface card, so, the network is not configured.  After several attempts, I continued the installation after the installer failed to recognize the hardware in hopes that I would be able to manually configure the network interface.  In the past, I have used debootstrap to install remotely and simply configured the network settings without a hitch, so, that leads me to believe that all of the files needed for networking should exist on the drive and that all I need to do is configure.

Here is the onboard hardware:
LAN Port RJ-45 10/100/1000
WLAN 802.11a/g/n

I modified the following files:
/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

/etc/hosts
127.0.0.1 localhost

I can ping localhost.
I can ping my router.
I can ping other machines on my home network via an IP number.
I can ping [www.google.com](www.google.com) via an IP number.
I CAN NOT ping anything using a domain name such as [www.google.com](www.google.com)

So, there is a host lookup problem??  Any ideas to help troubleshoot??  Are there commands I can use to interrogate the system for the existence of hardware??  Are there commands I can use to determine the MAC address??

I'm stuck!

---

### Post by mordox on 2008-02-13
try this .. [http://www.linlap.com/wiki/Asus+G2S](http://www.linlap.com/wiki/Asus+G2S)

check for your ip address by typing ifconfig in the terminal .

---

### Post by mrsteveman1 on 2008-02-13
check your /etc/resolv.conf file

you should have at least one line that says:

```
nameserver 205.xxx.xxx.xxx
```

replace the IP with your DNS server

your hardware is fine, the fact that you can ping your router means the entire network stack is working just fine.

However in the future if you need to, you can use the following commands to find harware in the system:

lspci shows devices attached to the PCI bus (most of the things youd be looking for are)
lsusb (shows usb devices currently plugged in)
dmesg (shows kernel messages which may show errors if something doesn't work)

---

