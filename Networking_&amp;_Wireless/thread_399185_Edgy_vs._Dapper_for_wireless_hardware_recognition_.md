---
title: "Edgy vs. Dapper for wireless hardware recognition (laptop)"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by Average_Joe on 2007-04-02
Hello --

I have a Lenovo 3000 n100, which has Intel 3945 802.11g wireless adapter.

Here's what happens when I do a cleam, reformat install on this machine using 6.06 versus 6.10 :

6.06 -- Dapper sets it all up for me.  From install, it sets up ethernet (eth0) and
wireless (eth1) and modem (eth2)

6.10 -- Edgy fails to find the wireless Intel 3945 from fresh install.  It offers only ethernet and modem.

Why is that?

Also, what can I do for getting 6.10 to find, recognize, and make useable the Intel 3945 wireless adapter?  Perhaps there is something easy for me to do first.

---

### Post by chili555 on 2007-04-02
On my Lenovo T60, two fresh installs of Edgy found and installed linux-restricted-modules and my ipw3945 was blinking away waiting for my ESSID and WEP key.

I would be sure linux-restricted-modules is installed. ```
sudo dpkg -l linux-restricted-modules*
```Then I would do:```
sudo modprobe ipw3945
```Look for any errors. Then do:```
iwconfig
```and see if your wireless interface has appeared. Post back and let us know.

---

### Post by Average_Joe on 2007-04-03
Thanks for the reply.  On my Lenovo 3000 N100, upon doing a clean, reformatted install of Ubuntu 6.10 Edgy Eft, here is the output of my command sudo lshw -C network:

$ sudo lshw -C network
Password:
*-network
description: Network controller
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@03:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=ipw3945
resources: iomemory:b0200000-b0200fff irq:169

I had learned about the lshw command in another thread.  Now below, please note the lshw output from another guy's machine after his 6.10 install, and note the differences especially in the line which mentions the driver.  I do not know what the differences mean, except that his has more info:

$ sudo lshw -C network
Password:
*-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@06:00.0
logical name: eth1
version: 02
serial: 00:13:02:c8:d2:75
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11g
resources: iomemory:52000000-52000fff irq:185

---
If you happen to glean any insights by comparison (and by comparison also with your machine) I would be grateful.

Right now, my Lenovo 3000 N100 in question, is being reformatted for a Windows install, and then I am going to put 6.10 onto it for dual-boot, which I hope to have accomplished tonight all.

Thanks!

---

