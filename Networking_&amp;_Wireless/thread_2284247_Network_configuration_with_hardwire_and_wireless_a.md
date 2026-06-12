---
title: "Network configuration with hardwire and wireless adapters"
date: 2015-06-28
forum: Networking &amp; Wireless
---

### Post by neb8 on 2015-06-28
Hello,

This may be a stupid question and something obvious that I'm overlooking. (I'm fairly new to Linux, have only used and been running for a couple of weeks)
 After installing Ubuntu 15.04, o with a buil-in to mb wired adapter. The hardwired adapter works just fine.
A few days later after installing a wireless pci adapter, the wireless works when initially opening a webpage with web browser, entering a url or search string. 
When any webpage link is clicked it opens a page indicating there is no connection.

---- Firefox

 Unable to connect
Firefox can't establish a connection to the server

---- Chromium

**This webpage is not available**

[COLOR=#777777][FONT=sans]ERR_ADDRESS_UNREACHABLE
[/FONT][/COLOR]

(Behaviour is similar when under Windows, when Window's update agent isn't working correctly.)

ifconfig displays four devices 

eth0 -  Link encap:Ethernet  
lo -     Link encap:Local Loopback 
virbr0  -Link encap:Ethernet
 wlan0 - Link encap:Ethernet

Could this problem be related to the virbr0 (virtual bridge)?
Each adapter was tested separately disabling one and enabling the other.

---

### Post by tgalati4 on 2015-06-28
Typically virbr0 is a virtual network device that is used for virtual machines such as kvm.  Did you install any virtual machines?  You can delete the virbr0, but that may cause issues.  [http://askubuntu.com/questions/246343/what-is-the-virbr0-interface-used-for](http://askubuntu.com/questions/246343/what-is-the-virbr0-interface-used-for)

Open a terminal and post the following after you get a network error:

```
netstat -r
```

---

### Post by neb8 on 2015-06-29
No virtual machines I know of unless one was installed while installing an application.

netstat -r output (eth0 connected)

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         Linksys00488    0.0.0.0         UG        0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.10.0    *               255.255.255.0   U         0 0          0 eth0
192.168.122.0   *               255.255.255.0   U         0 0          0 virbr0

After deleting [COLOR=#000000]virbr0 the browser link problem still exists when using a wireless connection.
__________

netstat -r output (eth0 connection)

[/COLOR]Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         Linksys00488    0.0.0.0         UG        0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.10.0    *               255.255.255.0   U         0 0          0 eth0

ifconfig displays lo and eth0 ..

______________

netstat -r output (wlan0 connection)

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

ifconfig displays lo, eth0 and wlan0
[COLOR=#000000]

[/COLOR]

---

### Post by tgalati4 on 2015-06-30
I would create a LiveUSB of 14.04, boot off of it, and try the wired connection, then the wireless connection.

What is your wireless card?

```
lspci
```

---

### Post by neb8 on 2015-06-30
After booting to a Ubuntu15.04 iso installed on the hd and there was no problem.

I think the problem may be either intermittent or has been eliminated after removing the virtual nic and rebooting.
After rebooting and enabling  both the hardwire and wireless NICs, then disabling the hardwire NIC, the wireless seems to be working as expected. 
I'll keep testing and keep eye on it to make sure there's not an intermittent initialization problem. I could also try removing the wireless NIC and drivers, then re-install.

The virtual nic may somehow effected the wireless nic driver, which I think was installed after the virtual.

---

