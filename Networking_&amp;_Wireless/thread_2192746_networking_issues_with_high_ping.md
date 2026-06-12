---
title: "networking issues with high ping"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by servalboi on 2013-12-09
so i have a samsung chronos series 7 NP700Z5A-S0AUS
and it has both wireless N and ethernet.

i've pritty much given up having a good ping time through wifi, so seeing as the router is sitting right next to me, i just hooked an ethernet cable to it , and low and behold high ping :(

here's an example
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=300 ttl=45 time=48.8 ms
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=301 ttl=45 time=41.5 ms
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=302 ttl=45 time=56.2 ms
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=303 ttl=45 time=41.8 ms
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=304 ttl=45 time=42.7 ms
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=305 ttl=45 time=91.0 ms
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=306 ttl=45 time=44.9 ms
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=307 ttl=45 time=88.0 ms
64 bytes from pc-in-f104.1e100.net (74.125.28.104): icmp_req=308 ttl=45 time=147 ms
^C
--- [www.google.com]("http://www.google.com") ping statistics ---
308 packets transmitted, 285 received, 7% packet loss, time 400047ms
rtt min/avg/max/mdev = 40.110/80.462/357.517/40.776 ms
shane@DemonLappy:~$ 


no matter what i do, i cannot get a normal ping which should be very low, around 45ms or somewhere in there, 
i've tried every single howto i can find and nothing has worked, 
also i seem to have screwed something up
in the networking connections box, there is a new connection (ifupdown(eth0) that i cannot seem to remove no matter what i try to do.

here is some info that i have managed to get
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
this is from lspci:
shane@DemonLappy:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M]
[B]02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] (rev 34)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)[/B]
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
shane@DemonLappy:~$ 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
here is the output for cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20

Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info>   address 192.168.0.57
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info>   prefix 24 (255.255.255.0)
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info>   gateway 192.168.0.1
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info>   hostname 'DemonLappy'
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info>   nameserver '192.168.0.1'
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info>   nameserver '205.171.2.25'
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info>   domain name 'PK5001Z'
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info> DNS: starting dnsmasq...
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <error> [1386614082.963973] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <error> [1386614082.964002] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <warn> DNS: plugin dnsmasq update failed
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec  9 11:34:42 DemonLappy NetworkManager[1292]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec  9 11:34:43 DemonLappy NetworkManager[1292]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec  9 11:34:43 DemonLappy NetworkManager[1292]: <info> Activation (eth0) successful, device activated.
Dec  9 11:34:43 DemonLappy NetworkManager[1292]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Dec  9 11:34:44 DemonLappy NetworkManager[1292]: <warn> dnsmasq appeared on DBus: :1.13
Dec  9 11:34:44 DemonLappy NetworkManager[1292]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
shane@DemonLappy:~$ 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
here is the link to the dmesg log

[http://paste.ubuntu.com/6547195/](http://paste.ubuntu.com/6547195/)
there may be a few things wrong here, but im only interested in fixing networking ^_^
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
here is the readout from lshw -class network

 *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6230 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:9d:a5:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-34-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:53 memory:c0600000-c0601fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: e8:03:9a:24:e3:d2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.037.00-NAPI duplex=full ip=192.168.0.57 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:50 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
shane@DemonLappy:~$ 

as you can see NETWORK is disabled, yet i can still connect to the internet with a very high ping.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
rfkill list:

shane@DemonLappy:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: samsung-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
shane@DemonLappy:~$ 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
i don't know what other information to provide.
i've tried every howto i could find to fix my networking issue, and i can't get it to fix it's self and it's driving me nuts, 
if there is anything anyone can do please help, it's my only complaint about ubuntu, is that it hates my wired and wireless cards.
thank you all for your time.

---

### Post by praseodym on 2013-12-09
Check the mtu value of your ISP and add it as a number instead of "Automatic" to the NM profile

---

### Post by servalboi on 2013-12-09
i already did that, i have it set for DSL speed at 1492, the DSL modem also mirrors this setting.
nothing seems to be working v.v im getting very frusterated.

---

### Post by praseodym on 2013-12-09
What about the nameservers?
[B]
cat /etc/resolv.conf
route -n[/B]

---

### Post by servalboi on 2013-12-09
here is the information you requested

shane@DemonLappy:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.0.1
nameserver 205.171.2.25
nameserver 127.0.0.1
search PK5001Z
shane@DemonLappy:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
shane@DemonLappy:~$

---

### Post by servalboi on 2013-12-09
also here's some more info for you.

shane@DemonLappy:~$ dmesg | grep -i eth | grep -vi ipv6 | grep -vi bluetooth
[    0.835780] r8168 Gigabit Ethernet driver 8.037.00-NAPI loaded
[    0.856754] eth%d: 0xffffc90000c68000, e8:03:9a:24:e3:d2, IRQ 49
[    0.907594] ACPI Error: Method parse/execution failed [\_SB_.PCI0.GFX0._DSM] (Node ffff88025407c910), AE_AML_OPERAND_TYPE (20121018/psparse-537)
[   10.200593] r8168: eth0: link up
[   13.209299] r8168: eth0: link up
shane@DemonLappy:~$

---

### Post by servalboi on 2013-12-09
and some more info

shane@DemonLappy:~$ sudo lshw -c network
[sudo] password for shane: 
  *-network DISABLED      
       description: Wireless interface
       product: Centrino Advanced-N 6230 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:9d:a5:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-34-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:53 memory:c0600000-c0601fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: e8:03:9a:24:e3:d2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.037.00-NAPI duplex=full ip=192.168.0.57 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:49 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
shane@DemonLappy:~$

---

### Post by praseodym on 2013-12-09
Deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by servalboi on 2013-12-09
so i found the fix, and it might work with anyone that uses this kind of laptop or the realtek 8111E card.

first go to realteks website and get the lan drivers for your linuxbox, install them
you may not notice any change as of yet.

untill you do this:

sudo gedit/leafpad /etc/default/grub <enter>

look for the section grub that has alot of this [GRUB_CMDLINE_LINUX_DEFAULT=]

at the end of that list, put the following; 
GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"
save and exit.

then

sudo update-grub
sudo reboot

and you should have phenominal ping time after that.
but make sure you get the drivers from realtek










you can get the drivers here:

[B][http://tinyurl.com/57n6q4](http://tinyurl.com/57n6q4)

go to the linux section of the downloads, and then select the current driver which is [/B]8.037.00 drivers

ill be writing a howto on howto do this.

---

