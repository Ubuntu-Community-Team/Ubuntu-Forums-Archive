---
title: "Improved question--Ubuntu Netbook cannot access my home wifi network."
date: 2011-01-22
forum: New to Ubuntu
---

### Post by pencils42 on 2011-01-22
Okay, here's my story, which of course includes some of my own stupid mistakes.

I got my netbook in the mail yesterday, opened it up, logged in, and Windows 7 was installed. Being a Windows hater my whole life, I followed a friend's advice and downloaded Ubuntu netbook, made a USB drive, changed the BIOS settings, all that. Here's when the stupidity occurs--I decided to go ahead and install Ubuntu without trying it, and to delete Windows to do so. A couple minutes later I realized that was a really, really stupid idea, so in a panic I turned my netbook off. I turned it back on and it was still on install but not really moving, so I powered off and on again and went back to the "Try Ubuntu" or "Install Ubuntu" choice screen. I chose "Try Ubuntu" and found that it did not recognize my home wifi network or ask me to join--or any wifi network, for that matter. 

Now, it did recognize my wifi network the few minutes I spent on Windows 7, so I tried to change the BIOS settings back to where I could just use that until I figured out the problem. But no matter which setting I tried (HDD/SDD just gives me a black screen, and FDD and LAN do the same as the USB drive), I can't get back to Windows, so I guess I did delete it. Which leaves me with a netbook that can only connect to the internet via ethernet cable. Which kind of defeats the purpose.

Questions I should answer:

1. How am I trying to get online? My home's wireless network. We have a router. All the other laptops in the house connect fine.

2. Who is my internet service provider (and in which country?) COX, United States.

3. Can you get online with any other method? Yes, the internet works fine with an ethernet cable.

4. How am I getting online to post in this forum? My parent's laptop.

5. What hardware are you using? Toshiba N505 netbook and a router. I can give more information about the router if you need it, but I doubt it's the program since the other laptops are fine.

Give me one moment and I will add some code that it gives me when I put in the commands this website tells me to.

My two final questions are:

1. Is there any way to recover Windows without buying it again?
2. How can I get Ubuntu to connect to my home wifi network?


EDIT: Here's some code. I have no idea what it means, but hopefully you do.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:76:9f:96
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.5 latency=0 multicast=yes
       resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:76:9f:96  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fe76:9f96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3682498 (3.6 MB)  TX bytes:326427 (326.4 KB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
ubuntu@ubuntu:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

---

### Post by cariboo on 2011-01-22
You may need to connect to your router with an ethernet cable in order to install the driver for your wireless device.

---

### Post by pencils42 on 2011-01-22
> **cariboo907 said:**
> You may need to connect to your router with an ethernet cable in order to install the driver for your wireless device.

Thank you! I will do that. (I was planning on it). But my question is, how do I install a driver for my wireless device? Which one should I install? Where do I get it? I just don't know where to go/what to do once I plug it into the ethernet cable.

---

