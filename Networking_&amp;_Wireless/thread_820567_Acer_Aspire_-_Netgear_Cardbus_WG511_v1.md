---
title: "Acer Aspire - Netgear Cardbus WG511 v1"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Michelexub on 2008-06-06
Hi.
Installed Xubuntu 7.10 on my Acer Aspire 1312.
The Netgear WG511 (cardbus) worked out of the box fine, apart from WPA encryption.

Upgraded to Xubuntu 8.04 and that issue was solved.
And I was a very happy man.

Then I did some updates (now my kernel version is 2.6.24-18 generic and since then the green light on the card is on, but the orange light keeps flickering and the card cannot find any wireless network.

Try to look for solutions on many threads.
Unfortunately i decided to try some of those solutions and now the laptop cannot even see the card (ie the greeen light is off).

Any help?
M.

---

### Post by chili555 on 2008-06-06
> Unfortunately i decided to try some of those solutions and now the laptop cannot even see the cardWhat did you try? You can refresh your memory with:```
history | less
```With the arrow key, you can scroll back through your commands and see what you did.

May we please see:```
sudo lshw -C network
```Thanks.

---

### Post by Michelexub on 2008-06-07
Hi.
The results from the command:
sudo lshw -C network
------------------------
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:22:2d:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half ip=194.1.1.13 latency=128 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 8
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:09:5b:c9:8f:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 driverversion=1.2 latency=80 maxlatency=28 mingnt=10 module=prism54 multicast=yes wireless=NOT READY!

NOTE: when I boot the laptop, now I can see the green light on the card, but as soon as I log in, the green light goes off.

Thanks.
M.

---

### Post by chili555 on 2008-06-07
I'm not sure prism54 is my favorite driver, but there may be other things we can look at first. Please check here: [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager)

Especially see this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themAs long as you have a wired connection:> ip=194.1.1.13 latency=128 link=yes Then Network Manager will 'manage' to not get your wireless going.

What happens when you reboot without the wire attached?

---

### Post by Michelexub on 2008-06-08
I rebooted without network cable attached.
Nothing happened.

See report:
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:22:2d:b8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=128 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 8
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:09:5b:c9:8f:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 driverversion=1.2 latency=80 maxlatency=28 mingnt=10 module=prism54 multicast=yes wireless=NOT READY!

M.

---

### Post by chili555 on 2008-06-08
Did you click the Network Manager icon, select your ESSID and try to connect and fail, or did you:```
sudo iwconfig eth1 essid <ur_router>
sudo iwconfig eth1 key <any_encryption_here?>
sudo dhclient eth1
```What didn't work?

---

### Post by Michelexub on 2008-06-09
I think I miscommunicated.

If I insert the card, unplugged the network cable and boot my laptop then:
1. the green light on the card switch on.
2. I log in with username and password and the green light goes off.

Note that the green light is on when the laptop recognise the card.
Since the light goes off when I log in with my username, my *guess* (I'm absolute beginner with Linux) is that in my configuration I disable the drivers (or part of the kernel or something) that helps Linux to recognise that card and use it.

It is not a problem with the wireless network.
My problem is that the card cannot see any wireless network.

When the card was working the sequence was:
1. I boot Linux - green light on.
2. Login with username and password - green light on.
3. Xubuntu finished, search for wireless network - green light on.
4. I selected the network icon, I can see different wireless networks around and connect to one of them - green light on and orange light on.

I hope that this clarify better my problem.

M.
BTW: really appreciate your help :)

---

### Post by chili555 on 2008-06-09
> I hope that this clarify better my problem.Not really. In post #1, you said:> the card cannot find any wireless network.
Now you say:> I can see different wireless networks around and connect to one of themThe yellow light flickers with network activity; are you saying it flickers or glows all the time, even with no network activity?

I am curious why you are using the prism54 driver. It has been superceded by p54pci. Did that not work for you?

Is your problem that you can connect to unencrypted networks, but not WPA? If so, I'd look at how you are inputting your encryption details in Network Manager.

---

### Post by Michelexub on 2008-06-09
Sorry if I haven't explained properly my problem.

This is my current issue:
I have a green light on when I boot, but as soon as I log in (with username and password) that light switches off.

> I am curious why you are using the prism54 driver. It has been superceded by p54pci. Did that not work for you?
Well, as I said before, I tried to solve my *previous* problem following instructions from few different forums.
Evidently in one of those forum (maybe an old one!) someone wrote an instruction that made my laptop use prism54 drivers.

My current issue is that Xubuntu, once I log in, cannot see the card altogether.

M.

---

### Post by chili555 on 2008-06-09
Please try:```
sudo rmmod -f prism54
sudo modprobe p54pci
sudo iwlist eth1 scan
```Also, please post:```
dmesg | grep eth1
```Thanks.

---

### Post by Michelexub on 2008-06-09
> sudo rmmod -f prism54 
Done it.

> sudo modprobe p54pci 
Done it.

> sudo iwlist eth1 scan 
Done it, but got this:
eth1      Interface doesn't support scanning.

>  Also, please post: dmesg | grep eth1 
Here it is:
[   67.559459] eth1: resetting device...
[   67.559489] eth1: uploading firmware...
[   67.737051] eth1: firmware version: 1.0.4.3
[   67.737109] eth1: firmware upload complete
[   77.222666] eth1: interface reset complete
[  192.335891] eth1: no IPv6 routers present
[  171.247145] eth1: islpci_close ()
[  733.668279] eth1: removing device


Thanks.
M.

---

### Post by chili555 on 2008-06-09
With p54pci loaded, instead of prism54, does:```
sudo lshw -C network
``` still show DISABLED? Could your PCMCIA slot be defective? Are there two in your laptop, an upper and a lower? Does it show UNCLAIMED in the other slot?

---

### Post by Michelexub on 2008-06-10
> With p54pci loaded, instead of prism54,
I don't know how to load/unload these drivers, sorry.

I followed your previous instructions:
sudo rmmod -f prism54
sudo modprobe p54pci

Are these instructions to load/unload those drivers?

Anyway, I have run:
sudo lshw -C network
>   *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:22:2d:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half ip=194.1.1.13 latency=128 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 8
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:09:5b:c9:8f:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 driverversion=1.2 latency=80 maxlatency=28 mingnt=10 module=prism54 multicast=yes wireless=NOT READY!


> still show DISABLED?
Looks like it, doesn't it?
But it seems to me that it is still using the prism54.
What do I have to do to disable it?

> Could your PCMCIA slot be defective?
I don't think so. If I boot into Windows they work.

> Are there two in your laptop, an upper and a lower?
Yes.

> Does it show UNCLAIMED in the other slot?
Don't know how to check this.

M.
PS: I appreciate your help, but if you are getting too frustrated let mw know!

---

