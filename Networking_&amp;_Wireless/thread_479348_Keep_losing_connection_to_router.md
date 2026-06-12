---
title: "Keep losing connection to router"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2007-06-20
Since upgrading to Feisty I keep losing connection to my router and thus the internet. I've tried ifup and ifdown but get a message about not having access to some file (forgotten to write down which) even with sudo.
Rebooting the PC is the only working solution I have. 

I'd like to figure out why this is happening and thus prevent it but failing that how to fix it without having to reboot. 

Is there any other way of resetting the network connection from the command line?
I reckon /var/log/messages might have some useful info, (ACPI problems perhaps?) but don't really know how to read it.

---

### Post by mikesignguy on 2007-06-20
sudo /etc/init.d/networking restart 

restarts the networking daemon

---

### Post by pickarooney on 2007-06-20
Excellent. Thanks :)

---

### Post by pickarooney on 2007-06-22
This has been happening a couple of times a day now since installing Feisty. What could be causing this?

---

### Post by gerkin on 2007-07-12
Your not alone I have been having the same problem so I'll try the 

"sudo /etc/init.d/networking restart" solution as well, many thanks

---

### Post by gerkin on 2007-07-16
There are many posted that appear related to this problem, 

I have had this problem on Ubuntu 7.04 Feisty only and it doesn't occur on Kubuntu 7.04 on the same machine.

As far as I can tell this has begun only in the last couple of weeks, since something was upgraded?

I have tried several posted solutions, including:

 "sudo /etc/init.d/networking restart" ... I get the following output:

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 14122
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:ea:e2:45:ed
Sending on   LPF/eth0/00:0f:ea:e2:45:ed
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:ea:e2:45:ed
Sending on   LPF/eth0/00:0f:ea:e2:45:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 37838 seconds.

I tried deleting the "/var/run/dhclient.eth0.pid" file and recreating it - no luck
 
"sudo ifconfig eth0" up & "sudo ifconfig eth0 down" didn't help, as did powering off, resetting etc. the routrer

SOLUTION:

for me the only reliable way to get my network connection back up was to eaither reboot back into Kububtu 7.04 (which always worked) or reboot dbus with:

code:  "sudo /etc/init.d/dbus restart"

output:

 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 

then the wired network immediately comes back up

Hope this helps someone

---

### Post by whoami1988 on 2007-08-02
Thank you sooooo much!

---

### Post by slioch on 2007-08-03
This is exactly the problem I've been running into with. I have an ASUS P5K-VM board that after installing ubuntu 7.04 (and flashing the bios), my nic dies. I'll try the suggested dbus restart. 

But what would be a permanent solution so that I don't have to restart dbus each time my nic dies?

---

### Post by walkerk on 2007-08-03
I had a similar problem in Ubuntu using network-manager. This is a known issue. My fix was to install [WICD]("http://wicd.sourceforge.net")

---

### Post by gerkin on 2007-08-05
I tried installing the new kernel, as per the thread:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

The thread instructions  and scripts work very well, thanks for your efforts

I spent quite a bit of time reinstalling nvidia, vmware (which required new gcc & cpp to be installed)  but unfortunatley the new kernel has not fixed the original network problem for me.

Now I'm considering downgrading to the original 2.6.15 Feisty kernel to see if that is more reliable, but that unfortunately requires the reinstall again (above) 

Hopefully others will have more luck

cheers ....

---

### Post by DavidFourer on 2007-08-08
> **walkerk said:**
> I had a similar problem in Ubuntu using network-manager. This is a known issue. My fix was to install [WICD]("http://wicd.sourceforge.net")
This worked for me, after months of trials and tribulations.  Thread: [2960591]("http://ubuntuforums.org/showthread.php?p=2960591#poststop")

---

