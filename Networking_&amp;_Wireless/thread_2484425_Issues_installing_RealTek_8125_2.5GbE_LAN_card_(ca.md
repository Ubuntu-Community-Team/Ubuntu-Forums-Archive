---
title: "Issues installing RealTek 8125 2.5GbE LAN card (can't be found)"
date: 2023-02-25
forum: Networking &amp; Wireless
---

### Post by S._Simmons on 2023-02-25
I'm new around here, having not posted to this board before.  In any case, recently I bought a new Motorola MB8611 cable modem to take advantage of the speed increase that my ISP has applied to some accounts, raising them up to a much higher speed.  My older NetGear modem was limited to a 650mb/s rate, while the MB8611 can go up to 2.5gb/s.  

Because my onboard NIC on my older MSI X470 Gaming Plus board is a 1GB chipset, I decided to get a 2.5GB ethernet card to take advantage of both my internet plan's increased speed (1.2GB/s) with the new modem.  I chose a single-port 10GTek card using the RT 8125 chipset.  I went ahead and installed the drivers for it, from the RealTek site:

[https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software)

I've also loaded the module (*sudo modprobe r8125*), but I can't get it to show up when I use the lshw command:

```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54FF54]**crotalus@ryzen7-2700x**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo lshw -c network[/COLOR]
  *-network                  
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:22:00.0
       logical name: enp34s0
       version: 15
       serial: 8a:5b:6d:37:17:f2
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.050.03-NAPI duplex=full ip=76.158.62.148 latency=0 link=yes multic
ast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 ioport:e000(size=256) memory:fc404000-fc404fff memory:fc400000-fc403fff
  *-network DISABLED
       description: Wireless interface
       physical id: 4
       bus info: usb@5:1
       logical name: wlxa854b242897d
       serial: a8:54:b2:42:89:7d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=5.19.0-31-generic firmware=1.4 link=no multicast=yes wireless=IEEE 802.11
(base) [COLOR=#54FF54]**crotalus@ryzen7-2700x**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

[/FONT]
```

I'm not quite sure how to get this card working.  Any suggestions? Also, I am on Kubuntu 22.10, and I bought the card from Newegg, this being the specific model - 

[https://www.newegg.com/10gtek-rtl8125/p/14U-00AM-00048?Item=9SIA9Z9HDR3534](https://www.newegg.com/10gtek-rtl8125/p/14U-00AM-00048?Item=9SIA9Z9HDR3534)

---

### Post by chili555 on 2023-02-26
If it doesn't appear in lshw then it doesn't exist as far as the operating system is concerned. Is it seated properly in the PCI slot? After shutting down and unplugging the computer, I suggest that you remove and reseat it carefully.

Is there any setting in the EFI/BIOS to enable/disable particular PCI slots? Does it appear here?

```
lspci -nnk
```This will be lengthy so you can safely omit all of the graphics, audio, USB, etc. devices that obviously have nothing to do with ethernet. Your device may show up as unknown but let's see it anyway.

---

### Post by S._Simmons on 2023-02-26
> **chili555 said:**
> If it doesn't appear in lshw then it doesn't exist as far as the operating system is concerned. Is it seated properly in the PCI slot? After shutting down and unplugging the computer, I suggest that you remove and reseat it carefully.

Is there any setting in the EFI/BIOS to enable/disable particular PCI slots? Does it appear here?

```
lspci -nnk
```This will be lengthy so you can safely omit all of the graphics, audio, USB, etc. devices that obviously have nothing to do with ethernet. Your device may show up as unknown but let's see it anyway.

Yeah, apparently is was in the wrong slot.  I put it in another PCIe slot and it's detected now (with both lspci and lshw), though I'm still having issues getting it work.  When I use the RTL8125 card, I am able to connect with the Network Manager (with some difficulty) but I'm not able to get internet access, and it'll eventually return a "IP configuration not available" type message. 

This is my lspci output: 

```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54FF54]**crotalus@ryzen7-2700x**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ lspci -nnk | grep "Realtek"[/COLOR]
22:00.0 Ethernet controller [0200]: [COLOR=#FF5454]**Realtek**[/COLOR][COLOR=#000000] Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)[/COLOR]
29:00.0 Ethernet controller [0200]: [COLOR=#FF5454]**Realtek**[/COLOR][COLOR=#000000] Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:8125] (rev 04)[/COLOR]
        Subsystem: [COLOR=#FF5454]**Realtek**[/COLOR][COLOR=#000000] Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:0123][/COLOR]

[/FONT]
```

And the output of lshw:

```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54FF54]**crotalus@ryzen7-2700x**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo lshw -c network[/COLOR]
[sudo] password for crotalus:  
  *-network                  
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:22:00.0
       logical name: enp34s0
       version: 15
       serial: 00:d8:61:10:36:66
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.2.0-060200-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 
ip=76.137.163.136 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:35 ioport:d000(size=256) memory:fc404000-fc404fff memory:fc400000-fc403fff
  *-network
       description: Ethernet interface
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:29:00.0
       logical name: enp41s0
       version: 04
       serial: 30:52:5a:00:14:0d
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.2.0-060200-generic firmware=rtl8125b-2_0.0.2 07/13/20 latency=0 li
nk=no multicast=yes port=twisted pair
       resources: irq:106 ioport:e000(size=256) memory:fca10000-fca1ffff memory:fca20000-fca23fff memory:fca00000-fca0ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 4
       bus info: usb@2:1
       logical name: wlxa854b242897d
       serial: a8:54:b2:42:89:7d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=6.2.0-060200-generic firmware=1.4 link=no multicast=yes wireless=IEEE 802.11
(base) [COLOR=#54FF54]**crotalus@ryzen7-2700x**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

I'm figuring the error has something to do with my DNS, but I'm not entirely sure how to deal with it.  I had some trouble earlier today with even getting my onboard LAN to work, though now it's up and running.  I did change my netplan configuration (/etc/netplan/01-network-manager-all.yaml), adding in 'dhcp4: true' for both RT devices (enp34s0 is my onboard LAN, enp41s0 is the LAN card) -

```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp34s0:
       dhcp4: true
    enp41s0:
       dhcp4: true   

```

At least my onboard LAN is working though.

---

### Post by chili555 on 2023-02-26
> I'm figuring the error has something to do with my DNSI suspect so.

Please revert your additions to netplan and follow with:

```
sudo netplan generate
sudo netplan apply
```

Reboot and show us:

```
ip a
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
ls -al /etc/resolv.conf
```You might not get supersonic speeds with the r8169 driver; however, let's get it working and then work on getting it working fast. 

Did you install the 6.2 kernel to try to address this issue? I suspect that the better driver, if we need one, will not compile properly on a kernel above 5.19. Let's wait and see before you remove 6.2.

-----------------------------------------------

Possibly helpful with some changes: [https://askubuntu.com/questions/1373924/asus-pn50-e1-and-18-04-lts-no-network-adapter](https://askubuntu.com/questions/1373924/asus-pn50-e1-and-18-04-lts-no-network-adapter)

---

### Post by S._Simmons on 2023-02-26
> **chili555 said:**
> I suspect so.

Please revert your additions to netplan and follow with:

```
sudo netplan generate
sudo netplan apply
```

Reboot and show us:

```
ip a
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
ls -al /etc/resolv.conf
```You might not get supersonic speeds with the r8169 driver; however, let's get it working and then work on getting it working fast. 

Did you install the 6.2 kernel to try to address this issue? I suspect that the better driver, if we need one, will not compile properly on a kernel above 5.19. Let's wait and see before you remove 6.2.

-----------------------------------------------

Possibly helpful with some changes: [https://askubuntu.com/questions/1373924/asus-pn50-e1-and-18-04-lts-no-network-adapter](https://askubuntu.com/questions/1373924/asus-pn50-e1-and-18-04-lts-no-network-adapter)

I did all that, but now I can't even get into Kubuntu at all, because of some USB 3-1 error it spits out after checking the journal for my boot SSD.  Then it puts me into LXQt and will ask me to find a window manager...

I'm not sure how to fix it but I'm going to try the recovery mode and re-run dkpg.  All this happened after I updated the kernel and my Nvidia drivers to the 525 series.

**Edit:** As I suspecting, running dkpg in the recovery mode didn't do anything.  I'm downloading the Kubuntu 22.10 ISO file now (under Windows, I dual-boot) so I can attempt a re-install.  I am not sure what else I can do.

---

### Post by chili555 on 2023-02-26
> because of some USB 3-1 error Nothing I suggested above is related at all to USB. I believe a reinstall is the shortest road to a fix.

---

### Post by S._Simmons on 2023-02-27
> **chili555 said:**
> Nothing I suggested above is related at all to USB. I believe a reinstall is the shortest road to a fix.

Oh, I know, it was a separate issue and I couldn't fix it without reinstalling Kubuntu.  I had to do a fresh install and format my SSD though because when I tried doing an install over my existing installation (keeping my personal files), it kept giving me a initramfs/Busybox error... I decided just to do a clean install, instead, which fixed that issue.

Unfortunately I still have the same problem connecting to that new modem as I did before.  It *was* working for awhile until I messed with the connection settings.  I'll have to redo the above steps later as I don't have time here to do all that, right now.  I'll post later in the day.  

Thanks.

---

### Post by S._Simmons on 2023-02-28
Well, I am not entirely sure why, but my connection is working now, as of this afternoon.  Apparently changing any of the settings can cause problems.  I need to figure out *why* though.

Currently, for my wired connection, 'Restrict to device' is blank, as is the cloned MAC address, and the Link negotiation is set to ignore.  My netplan has the follow options, but I'm going to leave it as is, since it's working for the time being: 

```
# Let NetworkManager manage all devices on this systemnetwork:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp34s0:
      dhcp4: true

```

Output of ip a, ping, and ls -al /etc/resolv.conf - 

```

[FONT=monospace][COLOR=#54FF54]**crotalus@ryzen7-2700x**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ ip a[/COLOR]
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host  
       valid_lft forever preferred_lft forever
2: enp34s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:d8:61:10:36:66 brd ff:ff:ff:ff:ff:ff
    inet 76.137.163.136/23 brd 76.137.163.255 scope global dynamic noprefixroute enp34s0
       valid_lft 227044sec preferred_lft 227044sec
    inet6 fe80::2d8:61ff:fe10:3666/64 scope link  
       valid_lft forever preferred_lft forever
3: enp41s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 30:52:5a:00:14:0d brd ff:ff:ff:ff:ff:ff
[/FONT][COLOR=#54FF54][FONT=monospace]**crotalus@ryzen7-2700x**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ ping -c3 8.8.8.8[/FONT][/COLOR]
[FONT=monospace]PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=11.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=54 time=12.6 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=54 time=11.2 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 11.224/11.798/12.648/0.613 ms

[/FONT][FONT=monospace][COLOR=#54FF54]**crotalus@ryzen7-2700x**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ ls -al /etc/resolv.conf[/COLOR]
lrwxrwxrwx 1 root root 39 Feb 27 02:49 [COLOR=#54FFFF]**/etc/resolv.conf**[/COLOR][COLOR=#000000] -> ../run/systemd/resolve/stub-resolv.conf
[/COLOR][/FONT][FONT=monospace]
```

Thanks for the help, I appreciate it.[/FONT]

---

