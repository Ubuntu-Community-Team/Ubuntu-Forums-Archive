---
title: "[SOLVED] eth0, eth1"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by joukez on 2008-12-29
I have, i think, a small problem. I have 2 network interfaces in my machine,eth0 and eth1. I want to make eth1 outgoing so i can link another pc to that one so it can go on the internet. This is a windows-machine. From that machine it is a piece of cake to do that stunt. So you can say problem solved! But no! The windows machine is my son's and he is here 2 weekends per month, so when he is not around the 2 machines have to be up and running. That in order to have internet on my Linux-machine. I have tried allmost anything i could find on the internet but nothing seems to work. The only thing that happend, no internet at all and had to change the config-files again:(:D. So can somebody help me!My machine runs Ubuntu 8.04

---

### Post by Dedoimedo on 2008-12-29
You want to use one of the machines as the internet gateway, right?

You can use either windows or linux; you already have the windows side covered.

linux side:

You need to configure forwarding on the linux box. 

```

echo "1" > /proc/sys/net/ipv4/ipv4_forward

```

This will only work for the specific session. To make the change permanent:

```

cp /etc/sysctl.conf /etc/sysctl.conf-backup

```

Open /etc/sysctl.conf and look for net.ipv4_forward directive.
Change it from net.ipv4_forward=0 to net.ipv4_forward=1.

Save and close. Now either reboot or run:

```

sysctl -p

```

Now you have forwarding enabled. If you also use a firewall, you'll have to setup forwarding in the firewall rules too. On the windows machine, you'll have to setup the linux box IP to be the default gateway and the dns.

Dedoimedo

---

### Post by joukez on 2008-12-29
wel it does not work, i'll show you what the terminal displays:



jouke@ubuntu:~$ echo "1" > /proc/sys/net/ipv4/ipv4_forward
bash: /proc/sys/net/ipv4/ipv4_forward: No such file or directory
jouke@ubuntu:~$ sudo gedit /etc/sysctl.conf
[sudo] password for jouke: 
jouke@ubuntu:~$ sysctl -p
error: permission denied on key 'kernel.printk'
error: permission denied on key 'kernel.maps_protect'
error: permission denied on key 'fs.inotify.max_user_watches'
error: permission denied on key 'vm.mmap_min_addr'
error: permission denied on key 'net.ipv4.conf.default.rp_filter'
error: permission denied on key 'net.ipv4.conf.all.rp_filter'
error: permission denied on key 'net.ipv4.ip_forward'

---

### Post by joukez on 2008-12-29
when i put ifconfig in the terminal it does not show the eth1

jouke@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ea:99:e7  
          inet addr:82.75.152.173  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::218:f3ff:feea:99e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4867796 (4.6 MB)  TX bytes:436816 (426.5 KB)
          Interrupt:17 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99500 (97.1 KB)  TX bytes:99500 (97.1 KB)
so where is eth1:D I put auto eth1 in the same file where it says auto eth0 and lo and loopback etc. etc.

---

### Post by burnetbj on 2008-12-29
Looks like you tried to run the commands without being root. I dunno how to fix the problem on the NIC looks like the previous poster knows what they are talki ng about so I would try runnning the same commands as root, with sudo infront of each line posted

---

### Post by joukez on 2008-12-29
Thanks guys! Tried it again now as root but no succes!](*,):)

---

### Post by Dedoimedo on 2008-12-29
Hello,

OK, so you enabled forwarding ... sorry for the sudo thingie, forgot to mention, considered it obvious :0

Now, did you configure the windows client?

Next, print the ifconfig info ... if eth1 does not show, it means it's not up.

You'll need to the following:

1) Decide if you want to use static or dynamic ip addresses. I recommend static, because then your linux box won't have to act as a dhcp server, too.

2) Setup eth1 on linux and then setup windows accordingly.

Use ips that you want and find adequate.

```

ifconfig eth1 192.168.1.100 netmask 255.255.255.0 up

```

Next, let's check that it's up with ifconfig and then that it uses the default gateway:

```

route -n

```

Post the info for route command here. Let's make sure that eth1 uses eth0 as the default gateway. If not, we'll change that.

Next, setup windows to use 192.168.1.101 or any other ip on the same subnet (192.168.1.1-192.168.1.254), exclude the first and the last ips as they are used by the system as network id and broadcast.

Setup windows to use 192.168.1.100 (linux ip) as dns.

See if this works now.

NOTE: the changes we did for route and eth1 are temporary until next reboot or next network restart, but we do this to test the setup. Once we're sure it works, we'll commit the changes to the configuration files.

Network configurations are stored in /etc/interfaces. Backup this file before making any changes. Furthermore, search the forums a little for how to configure the network device permanently and change the route permanently.

If during any of the stages you get confused, simply restart the network and start over:

```

sudo /etc/init.d/networking restart

```

Dedoimedo

---

### Post by joukez on 2008-12-29
Well long story!

jouke@ubuntu:~$ sudo ifconfig eth1 192.168.1.100 netmask 255.255.255.0 up
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth1: ERROR while getting interface flags: No such device
jouke@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]
jouke@ubuntu:~$ sudo ifconfig eth1 192.168.1.100 netmask 255.255.255.0 up
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth1: ERROR while getting interface flags: No such device
jouke@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ea:99:e7  
          inet addr:82.75.152.173  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::218:f3ff:feea:99e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6932810 (6.6 MB)  TX bytes:506992 (495.1 KB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80136 (78.2 KB)  TX bytes:80136 (78.2 KB)

---

### Post by Dedoimedo on 2008-12-29
Hmmm, what does ifconfig -a give you ...
Dedoimedo

---

### Post by joukez on 2008-12-29
jouke@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:f3:ea:99:e7  
          inet addr:82.75.152.173  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::218:f3ff:feea:99e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3866880 (3.6 MB)  TX bytes:341277 (333.2 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87696 (85.6 KB)  TX bytes:87696 (85.6 KB)

---

### Post by Dedoimedo on 2008-12-29
You don't have eth1 (recognized) in your system! You may need to install drivers for it to be recognized it ...

Did you put the second network card in your linux box?

Cheers,
Dedoimedo

---

### Post by anewguy on 2008-12-29
Are both cards installed?  Are both internal?

Post the ouput of:

sudo lspci


Also, if one is USB not PCI:

sudo lsusb


Thanks!
Dave :)

---

### Post by joukez on 2008-12-29
Yes i put it in my linux machine. I also reinstalled ubuntu after i put the 2nd nic in my ubuntu machine.I tought that might help, but unfortunatly it did not.Eth0 is an onboard via rhine the other is a 3com

---

### Post by joukez on 2008-12-29
jouke@ubuntu:~$ sudo lspci
[sudo] password for jouke: 
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:03.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by joukez on 2008-12-29
it's pci not usb

---

### Post by anewguy on 2008-12-29
Judging from the output of lspci, it is not even seeing the 2nd adapter (the 3com one) - only your Rhine adapter shows.  Perhaps there is a driver needed, but I would have thought the device would at least show.

Obviously we can't do much about the onboard card, but for the 3com card does it have any jumpers, etc.,  on it?  Did the 3com card come with any kind of driver for Windows?

Let's also check one other thing - see if the hardware shows via this:

sudo lshw -C network

Dave :)

EDIT:  BTW - what is the model, etc., of the 3com card that is not working?

---

### Post by joukez on 2008-12-29
well i swapped the cards, the 3com came from a working ms-machine with internet. I have another one, usrobotics, that one works on ubuntu. The 3com works on a ms-machine at the moment:confused:](*,). But now when i want to configure Firestarter it says when i want to save: firestarter could not start eth1 is not ready! so what now?

jouke@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:18:f3:ea:99:e7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=82.75.152.173 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1
       version: 10
       serial: 00:14:c1:35:ce:79
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by joukez on 2008-12-29
Thanks guys for the help! The card is now up and running! The next step is to let the ms-machine run on it, i will try when it won't work i'll be back. Windows is actually not the thing i use, it's my son's pc. Thanks a lot for the time and effort! CHEERS!

---

