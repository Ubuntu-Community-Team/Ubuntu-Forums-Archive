---
title: "update to 16.10 - wired connection stopped working RTL 8111/8168/8411"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by Bartje on 2017-03-05
Hi all,

I have searched and searched, but found no solution yet. Perhaps someone here can guide me through finding a solution.

I upgraded to 16.10 recently, after a lot of doubting since after each upgrade I do run into an issue (or two, three... :-p )

This time it is the wired network connection. This is a first for me, since usually it's the wireless connection, or some button that does not want to work anymore.

I have a RTL 8111/8168/8411 ethernet controller of Realtek. Before, it used to work out of the box, now it does not work, well, it is not 'enabled'. 

```
*-network DISABLED        
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 06
       serial: 50:e5:49:30:5a:33
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.042.00-NAPI duplex=full latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:28 ioport:de00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.6
       logical name: wlx64700208748e
       serial: 64:70:02:08:74:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=4.8.0-40-lowlatency firmware=1.4 ip=192.168.1.59 link=yes multicast=yes wireless=IEEE 802.11

```

As you see, I now use a wireless 'thing' to get online, but I'd prefer my wired connection. Can anyone here help?

thanks.
Bart

---

### Post by jeremy31 on 2017-03-05
Does running
```
sudo ifconfig enp7s0 up
```
Get the ethernet working?

---

### Post by Bartje on 2017-03-05
Hi,

wen running your code I get 'Kabel onbeheerd' (dutch here, using gnome at the moment). When I click on connect, nothing happens.

running lshw -C Network, it does not mention it is disabled anymore:

```
*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 06
       serial: 50:e5:49:30:5a:33
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.042.00-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:28 ioport:de00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff

```

---

### Post by jeremy31 on 2017-03-05
Does "Kabel onbeheerd" translate to cable disconnected?  Has the r8169 module worked for ethernet as I see you must have installed r8168?

---

### Post by Bartje on 2017-03-05
hey,

'Kabel onbeheerd' rather translates as 'cable not managed', but translations can be dodgy, it could actually mean disconnected. The cable is in, and the light is on, not flickering though.

After upgrading, I had no connection, so I followed some idea's on the web, one was blacklisting the r8169, installing the r8168-dkms, I even unplugged power cable as I read somewhere, nothing worked.

I'll purge the r8168-dkms, reboot, remove the blacklisting and reboot.

grtz,
Bart

---

### Post by Bartje on 2017-03-05
I reverted back to the r8169, no change.

---

### Post by jeremy31 on 2017-03-09
Cable not managed has some meaning, please post result of
```
cat /etc/network/interfaces
```

---

### Post by doeonethousand on 2017-03-10
Hi!

I do have the same network card, but in my case the problem is in accessing certain sites. For instance, I can access google.com and youtube.com, but I can't access ubuntu.com although I can ping it. I also can't update the system. So I decided to downgrade to Ubuntu 14.04 and now it works as it should. The visible difference to me between the to systems is in the way they name the network card: on Ubuntu 14 is eth0; on Ubuntu 16 is enp0s0 (or something very similar).

So what should I do? Stay on the 14 wagon? Or is there a file or a configuration I can modify to make the internet work on the Ubuntu 16 also? BTW, on the newer version of Ubuntu the upload speed is 1.5 to 2 times faster than the download speed. Kinda weird so definitely something not working correctly.

Thanks!

LE: If I launch Ubuntu 16 Live USB within VirtualBox on Ubuntu 14 then the internet works fine (except the DL & UL speeds), but if I boot the computer from the same Ubuntu 16 Live USB then I end up in the situation described above.
Another difference between the two systems is the lack of IPv6 on the former.

---

### Post by kwah on 2017-04-24
Have got exactly the same issue upon upgrading 16.04 -> 16.10. Quickly looked around for possible solution, and decided to go on with upgrade to 17.04, since it was my initial upgrade target anyway. So, he we are: wireless adapter is working, while wired does not work any more.

Observation: I've also tried live session from USB based on 17.04 ISO-image, wired network adapter just works in the live session. Conclusion: it is a software issue.

---

### Post by kwah on 2017-04-30
Submitted bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687262](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687262) please +1 it on launchpad.

---

### Post by kwah on 2017-05-02
As a work around, I've finally configured wired interface via /etc/network/interfaces:
```
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto enp5s0
iface enp5s0 inet dhcp
```

Now it works.

---

### Post by kwah on 2017-09-11
When similar was observed after upgrading of another system with completely different hardware:
  *-network DISABLED
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation

I've noted that it was also
  *-network DISABLED

This time search of the web led me to AskUbuntu entry [1] and the answer [2] advising to change NetworkManager configuration in /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf

Although I do not understand if there are other implications, this answer helped me to resolve issue at hand.

Looks like this bug should belong to network-manager or other project dealing with configuration changes upon upgrades.

[1] [https://askubuntu.com/q/906636/735629](https://askubuntu.com/q/906636/735629)
[2] [https://askubuntu.com/a/909185/735629](https://askubuntu.com/a/909185/735629)

---

