---
title: "How to reconfigure networking for Ubuntu 7.10"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by calif99x on 2007-11-12
Hi:

I have a working Ubuntu 7.10 setup that I need to reconfigure the networking.

Background:

I had originally installed 7.04 which for some reason did not recongnize/ enable the built in networking on the motherboard.  No problem, I used a PCI networking card and was off and running as eth0.

Now, after the 7.10 I noted that the motherboard network connection is listed as eth1, so I do not need the PCI card, which I then removed.

When the system comes up, it still sees the motherboard as eth1.  A colleague at work suggested that there may be the equivalent of the Solaris sys-unconfigure command that will let me reset networking.

I basically need to go down this path as I am using VMware Workstation 6, and the software expects to use eth0 (for some other reason I am not getting the options to change the network connections.... sigh), so my existing workstation and VMs keep looking for a live eth0 network connection.

Is there any way to resolve this short of doing a "repair" using a 7.10 live CD?

Thanks

---

### Post by R00t3rMan on 2007-11-12
How about disabling the onboard card in BIOS at bootup, then reboot and re-enable?  Just a thought, and something easy to try.

---

### Post by calif99x on 2007-11-13
I tried this.  No change to the network connection naming; current one is still labeled eth1.

---

### Post by R00t3rMan on 2007-11-13
Hmmm...I'll try to check around a little more.  It must be something to do with how the Kernel recognizes the hardware at bootup.  I'm pretty sure this is similar to how a Juniper router recognizes a particular slot (Junipers are BSD-based); eth0 would be the equivalent to slot 0.  Fooling the system into recognizing slot 1 as slot 0 will be an interesting hack.

---

### Post by noob12 on 2007-11-13
Check this file
```

cat /etc/udev/rules.d/70-persistent-net.rules

```

Remove or comment out the eth0 line and replace the eth1 with eth0.

---

### Post by calif99x on 2007-11-13
hmmm; something else is also apparently needed.  I saved a copy then edited the 70-persistent-net.rules file.

Commenting out eth0 and renaming eth1 to eth0 just seems to break the networking; by which I mean that the network connection shows a failure for eth1.  error message:

Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Anyone have a guess if there is a compiled file or other config that is also consulted since just a simple rename of the network connection does not work?

I am almost to the point of reinstalling the OS, but chickened out when the liveCD wanted to repartition my system since I couldn't remember what was where...  Man, I really just need a way to force the networking and other basic setup information to be redone.  The solaris sys-unconfigure command or a "Repair" option would really do the trick.

Some information from the 70-persistent-net.rules (modified & original) files is below in case something stands out:


modified 70-persistent-net.rules looks like:

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:c9:69:6e:0f", ATTRS{type}=="2", NAME="eth1"


# PCI device 0x8086:0x294c (e1000-ich9)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d1:eb:3d:40", ATTRS{type}=="1", NAME="eth0"

++++++++++++++++++++++++++++++++++++++++++++++++
I made the changes to ATTRS{type} 1 & 2 since from the man page it suggested this might be the sequence number, but that could easily be a mis-understanding on my part.

Original file looked like:
++++++++++++++++++++++++++++++++++++++++++++++++

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:c9:69:6e:0f", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x8086:0x294c (e1000-ich9)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d1:eb:3d:40", NAME="eth1"

Thanks in advance

---

### Post by noob12 on 2007-11-14
You have to reboot after that change.  Make sure the address in the rule matches that of the card which you want to be eth0.

---

### Post by calif99x on 2007-11-14
Hello noob12:

Thanks for your advice, it has been quite helpful.

I have rebooted after each change to the rules file, but if the eth1 is changed to anything else, I get an error message and no connection to the network.

This makes me think there might be a compiled file somewhere since the /etc/iftab file is not used any longer with 7.10.

Any other thoughts?

Cheers

---

### Post by noob12 on 2007-11-14
OK. Try these step by step.  If it doesn't work, I'm stumped and better help is needed.

(1) Make the change to **/etc/udev/rules.d/70-persistent-net.rules**.  Starting with the original file, swap only the names eth0 and eth1 and do not change any of the  **ATTRS** matching conditions at all.  (I noticed in your posting that you had.)  These refer to attributes of the devices and if you change them, they may not match any more.

(2) Reboot and check that the device names and addresses shown by running **ifconfig -a** match those that you configured in **/etc/udev/rules.d/70-persistent-net.rules**.  (If so, then your device naming is taking effect.)

(3) Now edit **/etc/network/interfaces** and make sure any device names you use in the configuration there match your new device naming.

(4) Now **sudo /etc/init.d/networking restart** or reboot.

---

### Post by calif99x on 2007-11-15
Hello noob12:

This is what I got, the eth1 still will not move to eth0:

Start with /etc/udev/rules.d/70-persistent-net.rules

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:c9:69:6e:0f", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x8086:0x294c (e1000-ich9)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d1:eb:3d:40", NAME="eth1"

-----------------------------------------------
Run ifconfig -a to check before making changes:

eth1      Link encap:Ethernet  HWaddr 00:19:D1:EB:3D:40  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:955800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1623544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:71531910 (68.2 MB)  TX bytes:2346946488 (2.1 GB)
          Base address:0x3100 Memory:e0380000-e03a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6293 (6.1 KB)  TX bytes:6293 (6.1 KB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.149.1  Bcast:192.168.149.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
-----------------------------------------------
Swap eth0 and eth1, leaving everything else the same:

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:c9:69:6e:0f", ATTRS{type}=="1", NAME="eth1"


# PCI device 0x8086:0x294c (e1000-ich9)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d1:eb:3d:40", NAME="eth0"

-------------------------------------------------------------------
reboot the system

------------------------------------------------------------------
ifconfig -a now shows:

eth0      Link encap:Ethernet  HWaddr 00:19:D1:EB:3D:40  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7799 (7.6 KB)  TX bytes:64 (64.0 b)
          Base address:0x3100 Memory:e0380000-e03a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5676 (5.5 KB)  TX bytes:5676 (5.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.149.1  Bcast:192.168.149.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

-------------------------------------------------------------------------------------------------------
check the /etc/network/interfaces file:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp
auto eth1

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

--------------------------------------------------
Make no changes since eth0 is already there.

---------------------------------------------------


sk@homeserv:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6189
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:d1:eb:3d:40
Sending on   LPF/eth0/00:19:d1:eb:3d:40
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:d1:eb:3d:40
Sending on   LPF/eth0/00:19:d1:eb:3d:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
SIOCADDRT: No such process
bound to 192.168.1.107 -- renewal in 36789 seconds.

--------------------------------------------------------------------
Firefox now fails to connect, samba fails, etc.

----------------------------------------------------------------

Putting everything back in the 70-persistent-net.rules file give the following network restart messages in comparison:

sk@homeserv:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d1:eb:3d:40
Sending on   LPF/eth1/00:19:d1:eb:3d:40
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
SIOCADDRT: No such process
bound to 192.168.1.107 -- renewal in 37317 seconds.

sk@homeserv:~$ 

-------------------------------------------------------------------------------

This is seriously not fun; the file edits and ifconfig show the interface should move over, but broken networking is just not practical.

Regards

---

### Post by noob12 on 2007-11-15
Based on the ifconfig after the change, the renaming worked just as expected.  Also the output of your networking restart showed that the newly named eth0 interface apparently also did get a new DHCP address 192.168.1.107 assigned.  Everything looks just fine.

It's not clear why you have failures after that but I don't think it is related to the interface naming.  You might need to look further at the situation to determine what's failing.

For starters, make sure there is a single default gateway and that it is your router
```

route -n

```
Look for a single line with UG in the Flags column and 0.0.0.0 in the destination column.
Check that the gateway column is 192.168.1.1.

Check that you got nameservers from the DHCP
```

cat /etc/resolv.conf

```

Verify that you can ping your router and that you aren't seeing errors in the kernel log
```

ping -c 5 192.168.1.1

tail /var/log/kern.log

```

Try a hostname resolution
```

host www.google.com

```

---

### Post by calif99x on 2007-11-18
Hello noob12:

I wanted to say thanks; the networking is now working as expected.  I wish I could say exactly what did it, but not quite clear yet.

Steps I did (in addition to your guidance above) were:

Uninstall VMware workstation software before making the network changes

Made the changes, confirmed they worked by using firefox to access the internet, host comment, etc.

Re-installed the VMware workstation software, which includes several recompilations of binaries.  My suspicion is that part of the recompilation process may be hard-coding network label such as eth0 with the MAC address, possibly to allow for the full type of network access that VMware uses.  This would mean that even if you change the Ubuntu level config files, the undesired state information still exists in the workstation software or config files.  

On Windows the workstation is supposed to give you a network configuration option (if you have administrator privileges), but you need to run as root on Ubuntu to get the same options.  Since by default Ubuntu the user runs as a limited access user, the options don't show up, nor does there appear to be a way to have it prompt for the administrator password to make the network changes.

I do want to thank you for your advice, you have expanded my knowledge of Linux network hugely; I might have not figured this out on my own for a long time.

Cheers

---

### Post by noob12 on 2007-11-18
Glad to hear you got it working.  Not sure how much I helped, but seems like you picked out what you needed.  Cheers.

---

