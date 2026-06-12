---
title: "Ubuntu 12.04 adapter, wireless &amp; VM connectivity issue"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by Marcus Aurelius on 2014-09-18
Hello,

I have a networking challenge I've been putting off since I installed Ubuntu Linux 12.04.1-LTS (3.2.0-68-generic) 64-bit on my Acer Travelmate Laptop 5744-6870 Intel Core i5-480M 2.66 ghz (4 GB DDR3) over a year ago.  I have it installed with the full disk encryption, including the home folder.  I have 64-bit Windows 7 Pro running in VirtualBox version 4.3.6 r91406.

When I reboot the computer, it says:

Unlocking Disk
    -The disk drive for /dev/mapper/machine_name-Swap-1 is not ready yet or not present.
    -Continue to wait, or press S to skip mounting or M for manual recovery.
        -Starting CUPS printing spooler/server
    -Waiting for Network Configuration
        ***** AT THIS POINT: We sit and wait for 50 seconds or so*****
    -Waiting up to 60 more seconds for network configuration....
        ***** AT THIS POINT: We wait around another 60 seconds*****
    Booting system without full network configuration

The system gives up and allows me to log onto the desktop. 
Now, issue here has been in existence since I setup the computer, and has been like this ever since.  I didn't have the time to look into correcting this issue at the time and just lived with it.  It was not working initially, but I used to enter this command in terminal, and it worked as above ever since.

sudo apt-get remove -- purge resolvconf
sudo /etc/init.d/networking restart
During this bungled time period, I somehow renamed my eth0 adapter to eth1, and not there is no eth1 nor eth0, it is eth2.

In sum:

1. My laptop has the above encryption timeout, network fails to connect issue.  I want to resolve this issue.
2. My laptop can connect wirelessly, but my wired connection does not work.
    -I have attached some laptop statistics below, there is:
        -ifconfig -a 
        -lspci
        -sudo gedit /etc/network/interfaces
        

username@machine:~$ ifconfig -a 
eth2      Link encap:Ethernet  HWaddr e8:40:f2:f1:e3:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth2:avahi Link encap:Ethernet  HWaddr e8:40:f2:f1:e3:56  
          inet addr:169.254.11.50  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22426 (22.4 KB)  TX bytes:22426 (22.4 KB)

wlan1     Link encap:Ethernet  HWaddr 10:0b:a9:e6:7a:74  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd82:3af5:ac94:0:120b:a9ff:fee6:7a74/64 Scope:Global
          inet6 addr: fe80::120b:a9ff:fee6:7a74/64 Scope:Link
          inet6 addr: fd82:3af5:ac94:0:8d3d:3f1:1959:5e5f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25971376 (25.9 MB)  TX bytes:1566237 (1.5 MB)




----------------------------------------------


username@machine:~$ $ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



---------------------------------------------

sudo gedit /etc/network/interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth2
iface eth2 inet dhcp




# The primary wireless network interface

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid ##########
    wpa-psk  ##########

auto wlan1
iface wlan1 inet dhcp
    wpa-ssid ##########
    wpa-psk  ##########

---

### Post by Marcus Aurelius on 2014-09-19
ttt

---

### Post by Marcus Aurelius on 2014-09-21
I solved some issues, and modified the above post greatly, but if anyone has any ideas about the boot issue, I'd be appreciative.  Thanks.

---

### Post by praseodym on 2014-09-22
Change "false" to "true" in the file /etc/NetworkManager/NetworkManager.conf. Otherwise the network-manager cannot handle the manual config in the "interfaces".

---

### Post by Marcus Aurelius on 2014-09-26
> **praseodym said:**
> Change "false" to "true" in the file /etc/NetworkManager/NetworkManager.conf. Otherwise the network-manager cannot handle the manual config in the "interfaces".

Hello and thank you for the reply.  I checked the networkmanager.conf file and it was 100% blank.  I restored that back to the default.  Also I did not have netork-manager properly installed.  So reinstalled that.  Now I DO have a wired connection which I did not have before.  

Incidentally, my wired laptop can not ping my wireless printer.  They ARE on different networks.  Is there an easy way to switch my wired and wireless to the same networks?  If this is not a quick answer, I will post another thread at a later date.

Finally, the boot issue is still not correct and it takes 2 minutes to load.  Anymore ideas?  Thanks.

---

