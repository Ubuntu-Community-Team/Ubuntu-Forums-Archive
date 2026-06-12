---
title: "cannot connect to internet: network UNCLAIMED"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by solow3752 on 2013-10-12
Hello, new linux user here. I am trying to set up a new laptop to dual boot Windows 8 and Ubuntu 13.04. I partitioned the hard drive and installed Ubuntu. I currently can't access the internet from Ubuntu wirelessly or from an ethernet cable. I would like to get the internet working in Ubuntu before I attempt to install Windows 8.

I believe my problem is similar to the one discussed in these threads, but I think my hardware is different so I'm not sure how to proceed:
[http://ubuntuforums.org/showthread.php?t=2180230](http://ubuntuforums.org/showthread.php?t=2180230)
[http://ubuntuforums.org/showthread.php?t=2143039](http://ubuntuforums.org/showthread.php?t=2143039)

I think the problem is in recognizing the wireless card, but I don't understand why that would affect the ethernet connection:
Intel Dual Band AC 7260 

Some other specs which might be relevant:
[FONT=arial]Sager NP2740
[/FONT][FONT=arial]i7-4750HQ
16 GB RAM
[/FONT]

Some output from commands that I see are requested in related threads:

==================================================


**sudo lshw -C network **
  *-network               
       description: Ethernet interface 
       product: Ethernet ConnectionI217-V 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 05 
       serial: 00:90:f5:ed:13:35 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi cap_listethernet physical 
       configuration: broadcast=yesdriver=e1000e latency=0 multicast=yes 
       resources: irq:20memory:f7e00000-f7e1ffff memory:f7e3d000-f7e3dfffioport:f080(size=32) 
  *-network UNCLAIMED 
       description: Network controller 
       product: Intel Corporation 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 73 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpresscap_list 
       configuration: latency=0 
       resources:memory:f7c00000-f7c01fff 


==================================================


**lsmod | grep -i e100 **
e1000e                198787  0 


==================================================


**apt-cache policy network-manager **
network-manager: 
  Installed: 0.9.8.0-0ubuntu6 
  Candidate: 0.9.8.0-0ubuntu6 
  Version table: 
 *** 0.9.8.0-0ubuntu6 0 
        100 /var/lib/dpkg/status 


==================================================


**cat /etc/network/interfaces **
# interfaces(5) file used by ifup(8)and ifdown(8) 
auto lo 
iface lo inet loopback 


==================================================


**dmesg | grep e100 **
[    1.631933] e1000e: Intel(R)PRO/1000 Network Driver - 2.1.4-k 
[    1.631938] e1000e: Copyright(c)1999 - 2012 Intel Corporation. 
[    1.631987] e1000e 0000:00:19.0:setting latency timer to 64 
[    1.632062] e1000e 0000:00:19.0:Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.632096] e1000e 0000:00:19.0: irq43 for MSI/MSI-X 
[    1.796549] e1000e 0000:00:19.0eth0: (PCI Express:2.5GT/s:Width x1) 00:90:f5:ed:13:35 
[    1.796553] e1000e 0000:00:19.0eth0: Intel(R) PRO/1000 Network Connection 
[    1.796608] e1000e 0000:00:19.0eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF 
[    4.965169] e1000e 0000:00:19.0: irq43 for MSI/MSI-X 
[    5.066204] e1000e 0000:00:19.0: irq43 for MSI/MSI-X 
[  312.006808] e1000e 0000:00:19.0: irq43 for MSI/MSI-X 
[  607.360374] e1000e 0000:00:19.0: irq43 for MSI/MSI-X 
[ 2168.703068] e1000e 0000:00:19.0:System wakeup enabled by ACPI 
[ 2170.756044] e1000e 0000:00:19.0:System wakeup disabled by ACPI 
[ 2170.756287] e1000e 0000:00:19.0: irq49 for MSI/MSI-X 
[ 2173.541261] e1000e 0000:00:19.0: irq49 for MSI/MSI-X 
[ 2173.642717] e1000e 0000:00:19.0: irq49 for MSI/MSI-X 

==================================================


**ifconfig -a **
eth0      Link encap:Ethernet  HWaddr00:90:f5:ed:13:35  
          UP BROADCAST MULTICAST MTU:1500  Metric:1 
          RX packets:0 errors:0dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TXbytes:0 (0.0 B) 
          Interrupt:20Memory:f7e00000-f7e20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1 Mask:255.0.0.0 
          inet6 addr: ::1/128Scope:Host 
          UP LOOPBACK RUNNING MTU:65536  Metric:1 
          RX packets:9472 errors:0dropped:0 overruns:0 frame:0 
          TX packets:9472 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:764272 (764.2 KB) TX bytes:764272 (764.2 KB) 


==================================================


**lspci **
00:00.0 Host bridge: Intel CorporationCrystal Well DRAM Controller (rev 08) 
00:02.0 VGA compatible controller:Intel Corporation Crystal Well Integrated Graphics Controller (rev08) 
00:03.0 Audio device: Intel CorporationCrystal Well HD Audio Controller (rev 08) 
00:14.0 USB controller: IntelCorporation Lynx Point USB xHCI Host Controller (rev 05) 
00:16.0 Communication controller: IntelCorporation Lynx Point MEI Controller #1 (rev 04) 
00:19.0 Ethernet controller: IntelCorporation Ethernet Connection I217-V (rev 05) 
00:1a.0 USB controller: IntelCorporation Lynx Point USB Enhanced Host Controller #2 (rev 05) 
00:1b.0 Audio device: Intel CorporationLynx Point High Definition Audio Controller (rev 05) 
00:1c.0 PCI bridge: Intel CorporationLynx Point PCI Express Root Port #1 (rev d5) 
00:1c.1 PCI bridge: Intel CorporationLynx Point PCI Express Root Port #2 (rev d5) 
00:1c.3 PCI bridge: Intel CorporationLynx Point PCI Express Root Port #4 (rev d5) 
00:1d.0 USB controller: IntelCorporation Lynx Point USB Enhanced Host Controller #1 (rev 05) 
00:1f.0 ISA bridge: Intel CorporationLynx Point LPC Controller (rev 05) 
00:1f.2 SATA controller: IntelCorporation Lynx Point 6-port SATA Controller 1 [AHCI mode] (rev 05) 
00:1f.3 SMBus: Intel Corporation LynxPoint SMBus Controller (rev 05) 
02:00.0 Unassigned class [ff00]:Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev01) 
03:00.0 Network controller: IntelCorporation Device 08b1 (rev 73) 


==================================================


**ifup eth0 **
Ignoring unknown interface eth0=eth0. 


==================================================


**cat/etc/NetworkManager/NetworkManager.conf **
[main] 
plugins=ifupdown,keyfile 
dns=dnsmasq 


[ifupdown] 
managed=false 

==================================================


**dmesg | grep -e eth0 -e bcm **
[    1.796549] e1000e 0000:00:19.0eth0: (PCI Express:2.5GT/s:Width x1) 00:90:f5:ed:13:35 
[    1.796553] e1000e 0000:00:19.0eth0: Intel(R) PRO/1000 Network Connection 
[    1.796608] e1000e 0000:00:19.0eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF 
[    2.966254] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[    5.066322] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[    5.066753] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 2173.642829] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 

==================================================

Please advise.

---

### Post by grahammechanical on 2013-10-12
When we install Ubuntu we are asked to tick if the machine is connected to the Internet (preferably by ethernet). Did you install with an Internet connection? Try clicking the Network Manager icon and making sure the Network is enabled and also if Wi-Fi is enabled. Does this laptop require you to use a keyboard combination to switch on the wireless adapter and the ethernet adapter?

This says that there is a driver for ethernet

> [COLOR=#000000]configuration: broadcast=yesdriver=e1000e latency=0 multicast=yes [/COLOR]

This says that the ethernet adapter is not connected to a router. It should also say RUNNING in between BROADCAST and MULTICAST

[COLOR=#000000]eth0 Link encap:Ethernet HWaddr00:90:f5:ed:13:35 [/COLOR]
> [COLOR=#000000]UP BROADCAST MULTICAST MTU:1500 Metric:1 [/COLOR]

Also ifconfig -a should show something for wlan0. This is what I get

> wlan0     Link encap:Ethernet  HWaddr 00:15:af:0e:9b:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


But that is because I have not set up a wireless connection with the router on this install of Ubuntu. I am using ethernet only. This is what I see when I authentic a connection to my router by wireless

> wlan0     Link encap:Ethernet  HWaddr 00:15:af:0e:9b:e0  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe0e:9be0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3256 (3.2 KB)  TX bytes:11423 (11.4 KB)


Run this command
```
rfkill list
```

Do you see this?

> : phy0: Wireless LAN
Soft blocked: no
Hard blocked: no


hard blocked: yes means that the wireless adapter is switched off in hardware, possibly at the keyboard.
soft blocked: yes means that the wireless adapter is switched off by software. Networking and/or wireless networking are not enabled.

Regards.

---

### Post by solow3752 on 2013-10-12
I can connect via ethernet now but i still can't connect wirelessly

> [COLOR=#000000]Did you install with an Internet connection?[/COLOR][COLOR=#000000]

No. I just rebooted to the USB to test whether that would have been possible, and it recognized the ethernet connection. Then I rebooted to the installed version of Ubuntu and it also recognized the ethernet connection.

I hadn't restarted with the ethernet cable already plugged in. So thanks for your help, and I'm sorry I didn't do my due diligence before.

tl;dr connecting via ethernet is solved by a reboot

HOWEVER, I still haven't connected wirelessly.

[/COLOR]> [COLOR=#000000]Does this laptop require you to use a keyboard combination to switch on the wireless adapter and the ethernet adapter?[/COLOR]

I'm not sure I know what you mean by keyboard combination. There are no physical switches on the machine for turning wireless on and off.

[COLOR=#000000]> ifconfig -a should show something for wlan0


It doesn't, here is the output:
> eth0      Link encap:Ethernet  HWaddr 00:90:f5:ed:13:35  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdb8:dac8:3f80:0:290:f5ff:feed:1335/64 Scope:Global
          inet6 addr: 2601:4:2080:263:290:f5ff:feed:1335/64 Scope:Global
          inet6 addr: fe80::290:f5ff:feed:1335/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4540623 (4.5 MB)  TX bytes:353106 (353.1 KB)
          Interrupt:20 Memory:f7e00000-f7e20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70446 (70.4 KB)  TX bytes:70446 (70.4 KB)


This is the output in response to rfkill list:
[/COLOR]> 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no[COLOR=#000000]

And in response to sudo iwlist eth0 scan I get:
> eth0      Interface doesn't support scanning.
[/COLOR]

---

### Post by solow3752 on 2013-10-12
In case it wasn't clear, I'm still struggling here trying to get Ubuntu to connect to a wireless network using the AC7260 wireless card.

---

### Post by solow3752 on 2013-10-12
The advice on this thread worked: [http://askubuntu.com/questions/322511/no-wireless-with-intel-centrino-advanced-n-7260](http://askubuntu.com/questions/322511/no-wireless-with-intel-centrino-advanced-n-7260)

> [COLOR=#333333][FONT=UbuntuRegular]I suggest you download this to your desktop:[http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:[/FONT][/COLOR]
cd Desktop/backports-3.11-rc3-1/
make defconfig-iwlwifi
make
sudo make install

---

