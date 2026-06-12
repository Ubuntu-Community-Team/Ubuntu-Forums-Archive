---
title: "Ubuntu Network Bridge in VMware"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by sackbj on 2008-04-23
I am running Ubuntu 7.10 as a VM.  I am connected to my university's wireless network on Win XP.  I have the VM set to bridge the network connection.  However, the VM is never able to connect to the internet.

Here are some of the setting I had to use to get on the network (hope this helps):
Network Authentication: Open
Data Encryption: WEP
The key is provided for me automatically
PEAP protection

I am able to log on to the network when I accept their security certificate and provide my username and a password.

I am not sure whether this is an issue with my network's security not letting me assign multiple IP's, or if I have some setting wrong in my VMware host.  Can anyone point me in the right direction here?

---

### Post by sackbj on 2008-04-23
I guess I should also ask which settings I should have configured in the Internet Connection Settings.

Currently I have "VMware Network Adapter VMnet1" allowed to share my connection.

---

### Post by dmizer on 2008-04-23
what vmware product are you running your virtual machine in?

is there a listing for vmnet1 in start > control panel > networking?  if so, does it list vmnet1 as being bridged (not just shared, but bridged)?  if the connections are not bridged in windows, take a look here: [http://www.windowsnetworking.com/articles_tutorials/wxpbrdge.html](http://www.windowsnetworking.com/articles_tutorials/wxpbrdge.html)

you say you're able to log in to the network?  are you getting an ip address in your ubuntu virtual machine?

to find out, post the output of:
```
ifconfig
```
from terminal

---

### Post by sackbj on 2008-04-24
I am using VMware Server.  I created a virtual machine with the 7.10 install disk.

There is indeed a listing for "VMware Network Adapter VMnet1" in my network connections folder.  It is not bridged.  When I try to bridge it with my wireless network connection, I get an error message saying that VMnet1 is not able to be part of the bridged connection.

I can not connect to the network in my VM, I am logging in through Windows.  I do not have an IP address in my Ubuntu virtual machine.

Hope that info helps.

---

### Post by sackbj on 2008-04-24
Note: I switched the virtual machine network settings to VMnet8 (NAT) and this is working for me.  I can now access the internet in my Ubuntu virtual machine.

---

### Post by Paris Heng on 2008-10-12
> **sackbj said:**
> Note: I switched the virtual machine network settings to VMnet8 (NAT) and this is working for me.  I can now access the internet in my Ubuntu virtual machine.

hi, i having the problems as well. Did you set the IP address in VMnet8 (NAT)? It is the the IP address need to be in the same segment with the local address (e.g. LAN)? I using ADSL to the Internet.

---

### Post by Paris Heng on 2008-10-12
Solved.

---

