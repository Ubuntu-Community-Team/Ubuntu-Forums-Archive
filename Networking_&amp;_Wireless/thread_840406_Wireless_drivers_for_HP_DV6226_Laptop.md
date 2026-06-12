---
title: "Wireless drivers for HP DV6226 Laptop"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by pratikpoddar on 2008-06-25
I have an HP DV6626 laptop. It came installed with windows vista. I have now installed Ubuntu and uninstalled Vista. I am not able to find wireless drivers for my laptop. I asked HP guys and they have just one line - "HP does not recommend its users to use Linux". What should I do?

Help!!!
Thanx in advance.


--
Pratik

---

### Post by secondstage on 2008-06-25
Please post the output of these two commands. You can dothis by going to Applications > Accessories > Terminal. Then typing in what is writen, and pressing enter.
```
iwconfig
```
```
sudo lshw -C network
```
On the second command, you will need to type the passwork that you login with to be able to have the computer do lshw -C network. The first command shows your configuration for your network. The second command shows the capabilities, and the hardware for your network interfaces.

If you have any other questions, feel free to ask them. I will try my best to answer them to the best of my ability!

--secondstage

---

### Post by pratikpoddar on 2008-06-30
on iwconfig:

lo    no wireless extensions.

eth0  no wireless extensions.
 
on sudo lshw -C network

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:fd:48:44
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 link=no module=e1000 multicast=yes port=twisted pair


thank you... please help

---

### Post by secondstage on 2008-07-04
I think you need to have your backports enabled. Go to System > Administration > Software Sources. And check the box that says "Unsupported Updates(hardy backports)". Close, and You  should get a pop-up saying Reload, or something like that. Click Reload. Next, go to terminal, and type...```
sudo apt-get install linux-backports-modules-hardy-generic
```
Now reboot, and see if your wireless works now.

--secondstage

---

