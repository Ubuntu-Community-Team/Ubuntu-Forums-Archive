---
title: "[SOLVED] Problems with Realtek 8139D"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by doomsniper on 2008-04-18
Hi, I am pretty new to Ubuntu, and I need help on my Realtek 8139D Network Card.  I have tried to search around the forums, most of them un-answered, it would be really nice if you could guide me through what to do.

The card works with Vista, although I had to insert the CD for the driver.  At the moment, I have Vista being the second O/S.

I do not know where to start, and it would be nice to learn a bit of Ubuntu as well.

---

### Post by chili555 on 2008-04-19
With the wire connected, when you go to System -> Administration -> Network is there a wired connection to check off? If so, please check it and select Properties and drop down DHCP. Save and close everything and you should connect.

In case Dr. Chili, computer whisperer, is wrong today, then open a terminal: Applications -> Accessories -> Terminal and do:```
sudo lshw -C network
```That means, roughly, 'list all the hardware of the class "network"'. Now, I know you can't, without the internet, copy and paste all the text back into this forum, but we just want, pertaining to your Realtek, the information, if any, like I have bolded here:```
 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       **logical name: eth1**
       version: 02
       serial: 00:19:d2:c2:1b:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=ipw3945** driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.999 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
```Just tell us the logical name and driver.

---

### Post by doomsniper on 2008-04-19
```
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       **logical name: eth0**
       version: 01
       serial: 00:e0:4e:ab:5c:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=sc92031** driverversion=2.0c duplex=full ip=192.168.1.126 latency=32 link=yes maxlatency=40 mingnt=20 module=sc92031 multicast=yes port=MII speed=100MB/s

```

Here it is, also, I can go on to the internet through

```
sudo ifup eth0
```

I am not sure what it does exactly though.

---

### Post by chili555 on 2008-04-19
> I can go on to the internet Terrific! Did you need more help or all you all set? Does it not stick through a reboot, or....?

---

### Post by doomsniper on 2008-04-19
I think I need more help.  Although I can force the LAN card to work, it really doesn't seem to be a permanent solution.  Everytime I need internet, I have to go to the Terminal and type: ```
sudo ifup eth0
```

However, even though I can go onto Firefox, it doesn't allow me to install Software Packages and updates.  Do you know something which could allow me to update my Ubuntu?

---

### Post by chili555 on 2008-04-19
> it really doesn't seem to be a permanent solutionWhen you go to System -> Administration -> Network and highlight your wired connection, then select Properties, is 'Enable This Connection' checked?> Do you know something which could allow me to update my Ubuntu?When you go to System -> Administration -> Synaptic, then select Settings and Repositories, are all the 'Downloadable from the Internet' options checked? If you make any changes,  press Reload, then press Mark All Changes and Apply.

Let us know.

---

### Post by doomsniper on 2008-04-19
> When you go to System -> Administration -> Network and highlight your wired connection, then select Properties, is 'Enable This Connection' checked?

I do not know where to find the "Enable This Connection".  What I see is in the Attachments, so take a look please.

---

### Post by chili555 on 2008-04-19
Ah! Roaming! NetworkManager! Makes perfect sense for a wired, that is, a stationary computer.

The following comments are solely the opinion of the poster, chili555, and not necessarily those of the forum sponsors nor the Ununtu developers, nor Linus Torvalds, his spouse, children or kitty cat:

I think NetworkManager really doesn't work very well, after years of work and, in fact, stinks.

End rant.

If this is a desktop computer, you could consider removing NetworkManager. I could put another notch on my gun-belt.

Lets see:```
cat /etc/network/interfaces
```Thanks!

---

### Post by doomsniper on 2008-04-19
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp





auto eth0
```
OK, I put what you typed and got this.

EDIT:  I don't know what I did, I think I managed to do something which allows the internet to auto connect.  Whatever it was it had to do with

```
 sudo ifup 
```

Thank you once again for helping me, I really appreciate it.

---

