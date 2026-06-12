---
title: "Cant connect to the internet with ethernet or wifi"
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by John_Snyper on 2015-12-13
Hi, first time linux user i thought i might try learning how to use it with an old laptop. After i installed the 15.10 desktop, I cant connect to the internet with either Wifi or Ethernet. Here's the list of my network cards when I run lshw -class network:

```
  *-network
       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d3a00000-d3a07fff memory:d3800000-d39fffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: ens5f5
       version: 03
       serial: 48:5b:39:8e:a8:16
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:34 memory:d4c00000-d4c03fff ioport:9100(size=128) ioport:9000(size=256)

```

I think I can do away with wifi, but i just want to get the ethernet to work since theres a lot of posts here in this forum about getting Broadcom drivers to work if you already have wired internet working.

---

### Post by Hadaka on 2015-12-13
Hi,to get the ethernet to work will require internet access. So let's
see if we can get you online with wireless first. please insert the usb
you used to install Ubuntu. open the files of the usb and click on..
```
pool>>restricted>>b >>bcmwl
pool>>main>>d>>dkms
```
 Drag and drop the bcmwl.deb to the Desktop
Drag and drop the dkms.deb to the Desktop
once done,remove the usb
Then open a terminal ctrl/alt/t COPY and paste
```
cd Desktop
sudo dpkg -i dkms*.deb
sudo dpkg -i bcmwl*.deb
```
boot
*If your wireless comes to life then do.
```
sudo apt-get update
sudo apt-get dist-upgrade
```
boot again
hopefully your wired connection will now be working.

---

### Post by John_Snyper on 2015-12-13
Oh wow. BOth the wifi and ethernet are working now and thanks for helping out a new user!

by the way as a follow up, if i run into this problem again but on a machine without WiFi, is there a deb package in the cd that I can download to install generic drivers?

---

### Post by Hadaka on 2015-12-13
Glad that worked,no unfortunatly there are too many drivers and
too many different types of wifi devices to have files for all. Please
take the time and mark your thread SOLVED ,by logging back in and
going to your first post, upper right area,  click TOOLS and then solved.
thanks.

---

### Post by John_Snyper on 2015-12-13
Quick follow up question.

So apparently my ethernet (JMicron) can only utilize 100mbps speed. I did the following command to switch from 1gbps (default) to 100mbps ("ens5f5" is the name of the ethernet, not "eth0" for some reason):
```
sudo ethtool -s ens5f5 speed 100 duplex full autoneg on
```

But when I restart, it goes back to usin 1gbps and I have to type the code above again to get it working.

How do I set the 100mbps to be the default configuration?

---

### Post by Hadaka on 2015-12-13
Hi,In the future,please dont un-solve a thread for a totally different issue
instead, please create a new thread, the solved threads help find answers
to problems for others, now this thread has 2 un-related issues, we wont
put you in the corner with a windows machine this time...but in the future....
please open a Terminal and then COPY and paste.

[LIST]
[*]```
echo "ethtool -s ens5f5 speed 100 duplex full" | sudo tee -a /etc/rc.local
``` 
[*]boot and test. 
[/LIST]
to delete this entry should you choose to do so.
```
sudo sed -i '/^ethtool -s ens5f5 speed 100 duplex full/ d' /etc/rc.local
```

---

### Post by John_Snyper on 2015-12-13
sure thing! ill make a new thread instead next time thanks once more

---

### Post by Hadaka on 2015-12-13
Glad that also worked for you ! and thank you for your understanding.
And...WELCOME to Ubuntu !
p.s.
as of 15.10  eth and wlan are renamed. I didnt bother to keep the link
as to why.

---

