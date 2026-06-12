---
title: "DHClient glitch"
date: 2016-05-27
forum: Networking &amp; Wireless
---

### Post by warlik-boys on 2016-05-27
Hi,

I'm currently running an Ubuntu 16.04LTS environment as a virtual machine on my windows machine. It was all working fine and dandy until I tried to get it to network with my Arch VM via a static network.

For some reason the Ubuntu box doesn't connect to the network automatically on boot and I have to run ```
systemctl restart networking
``` to connect to the internet.

Here is my /etc/network/interfaces file. The glitchy interface is eth0:
[ATTACH=CONFIG]269336[/ATTACH]

Here are the results of systemctl status networking directly after boot:
[ATTACH=CONFIG]269334[/ATTACH]
It says the service is enabled and I don't see any errors so I don't understand why it won't connect to the internet.


Here are the results of systemctl restart networking:
[ATTACH=CONFIG]269335[/ATTACH]
It appears there are a bunch of errors here that I don't understand but for some reason the internet now works (can ping 8.8.8.8 and google.com).

In the process of troubleshooting this I have removed Network Manager so it wouldn't interfere with anything. 


Thanks in advance for any help

---

### Post by T.J. on 2016-05-28
> **warlik-boys said:**
> Hi,

I'm currently running an Ubuntu 16.04LTS environment as a virtual machine on my windows machine. It was all working fine and dandy until I tried to get it to network with my Arch VM via a static network.

For some reason the Ubuntu box doesn't connect to the network automatically on boot and I have to run ```
systemctl restart networking
``` to connect to the internet.

It appears there are a bunch of errors here that I don't understand but for some reason the internet now works (can ping 8.8.8.8 and google.com).

In the process of troubleshooting this I have removed Network Manager so it wouldn't interfere with anything. 


Thanks in advance for any help

What are you using for a hypervisor on Windows?  VirtualBox or Hyper-V?

---

### Post by jeremy31 on 2016-05-28
I don't think eth0 or eth1 actually work in Ubuntu 16.04, post ```
ifconfig
``` results as what used to be eth0 on my laptop is now enp2s0

---

### Post by T.J. on 2016-05-28
> **jeremy31 said:**
> I don't think eth0 or eth1 actually work in Ubuntu 16.04, post ```
ifconfig
``` results as what used to be eth0 on my laptop is now enp2s0


Good point!  It might be named enp6s0 or similar instead of eth0 with the new kernels.

---

### Post by warlik-boys on 2016-05-29
Thanks for the replies.

I'm using VirtualBox 5.0.20, and the VM has 2 network adapters connected, one with the default NAT config and another on an internal network.

ifconfig:
[ATTACH=CONFIG]269347[/ATTACH]

---

### Post by warlik-boys on 2016-06-14
Hi all,

I'm still having the same problem, any help would be awesome thanks

---

