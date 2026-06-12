---
title: "Ubuntu 16.04 - Wireless NIC Drivers"
date: 2016-08-19
forum: Networking &amp; Wireless
---

### Post by jedrabe on 2016-08-19
Hello,

I am a wireless network engineer who is in need of a system that can sniff 802.11 frames. Windows won't cut it since it does not allow you to change your WNIC into monitor mode. The other options to me were Mac OSX or a Linux distro. As I do not have money for a Macbook Pro I decided to give Ubuntu a try as I do have some familiarity with it. I am currently trying to setup Ubuntu 16.04 with Wireshark in order to sniff the 802.11 frames. However, I have run into a few issues which are outlined below:

1) When opening Wireshark I do not see the option to place the WNIC into monitor mode.
2) When attempting to place the WNIC into monitor mode, it does not seem to change the mode.

I am trying to change the mode of the WNIC by issuing the following command:

sudo ifconfig wlp8s0 down
sudo iwconfig wlp8s0 mode monitor
sudo ifconfig wlp8s0 up

I'm not sure why wlp8s0 is the name of the wlan card. I was actually expecting it to wlan0

I am pretty sure the wlan card is able to be placed in monitor mode. The driver I am using is below:

 description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlp8s0
       version: 73
       serial: fc:f8:ae:c2:dd:dc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-31-generic firmware=16.242414.0 ip=10.0.30.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:34 memory:c2400000-c2401fff


If you have any suggestions or a guide to setup Ubuntu in order to use Wireshark and the WLAN card in monitor mode, I would appreciate it a lot!

Thank you,

Jed

---

### Post by chili555 on 2016-08-20
I know little to nothing about wireshark, except that I can get it to work on my own Intel 7260. But I know a fair bit about wireless and Intel devices. Perhaps I can help you a bit.> I'm not sure why wlp8s0 is the name of the wlan card. I was actually expecting it to wlan0It is so because of persistent naming: [http://askubuntu.com/questions/760196/why-is-enps-in-stead-of-eth-whats-the-meaning-of-enps/760243#760243](http://askubuntu.com/questions/760196/why-is-enps-in-stead-of-eth-whats-the-meaning-of-enps/760243#760243)> I am pretty sure the wlan card is able to be placed in monitor mode. I'm quite confident that it is; you can verify it with:```
iwconfig
```If the commands you listed were successful, it will report "Mode: Monitor" instead of the usual "Mode: Managed" when the wireless card is being, in effect, managed, by connection to the router or access point.

That's it! That's all I know.

---

