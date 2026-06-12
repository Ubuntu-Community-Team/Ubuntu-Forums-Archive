---
title: "Can't Get WiFi Workng On 14.04?"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by rayj00 on 2014-06-21
So, I have this Toshiba laptop that did have Windows 7.  The WiFi interface worked fine.
Well, I blew Windows 7 away by loading Ubuntu 14.04.  Eth0 wire line works fine but
I can't get the wlan0 up for anything.

Is there a decent tutorial available?  Or, if you are a wifi expert, maybe you can help?

I actually tried two different 14.04 builds...amd64 and i386. Same results.

Since server has no GUI, I have to configure manually.  So, what exactly do
I have to create/modify?

Here is just about all of the Wireless info on the system, attached:  I'd appreciate your help!

---

### Post by chili555 on 2014-06-22
> interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The primary wireless interface
auto wlan0
iface wlan0 inet dhcpThe wireless interface will not connect without an SSID and WPA2 password given. Moreover, I suggest a static IP address on a server so you can ssh and ftp into it.  Therefor, I suggest you modify /etc/network/intefaces to look like:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet dhcp

# The primary wireless interface
auto wlan0
iface wlan0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
wpa-ssid <your_network>
wpa-psk <your_password>
```I suggested 192.168.1.125 because you want an address outside the range used for DHCP in the router.

Now restart the interface:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```The -v makes the process verbose so you can tell if it connects. Check:```
ping -c3 192.168.1.1
ping -c3 www.google.com
```

---

### Post by rayj00 on 2014-06-22
Thanks chili555.  That pretty much did the trick.  I had to make a change in my router for the static IP.

Ray

---

### Post by chili555 on 2014-06-22
Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by rayj00 on 2014-06-22
I don't see where to mark the thread solved?

---

### Post by rayj00 on 2014-06-23
Actually I am still having issues.  

During a reboot, when it's going through the starting/stopping sequence, it stops
for seconds at "Waiting for network configuration"  then another message 
"Waiting up to 60 seconds for network configuration".

Once I log in, the wlan0 is up and works.   However, for some reason, I lose WiFi connectivity.
Not sure if it's after a certain length of in activity or what, but it has happened 3 times.

I'm about to hit the sack, but I will check in the morning and if it lost WiFi,  check out the log
files.

---

