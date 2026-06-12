---
title: "Both wired and wi-fi connections do not work (15.10)"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by kajtekk71 on 2016-01-07
Hi guys,

I recently moved from Manjaro to Ubuntu (manjaro was a bit harder to maintain then) to get fine-working operating system to work with Ruby on Rails. I'm not really into unix systems and prefer to use Windows now, but i know a thing or two. The problem is, that on Ubuntu I cannot access the Internet. It is still possible on Windows 7 (and was possible on Manjaro), however. Moreover, the connection was available during my stay in hometown at the time i was installing Ubuntu (Dlink DIR-300 router). System shows that is connected to Ethernet/Wireless network, but i cannot browse websites or download/update anything via console. No packets are received while pinging 8.8.8.8.

 I'm connected to the dormitory network via ethernet cable. Tried with other sources like my phone with tethered network, other router - TP LINK TL-WR340G with no joy. Ubuntu's installed on HDD, dual booting with Windows 7 on SSD. Linux tells that no priopietary drivers are installed. Tried different things posted in askubuntu/ubuntuforums and nothing helped. I'm using Lenovo Y580. 

Output from ifconfig, lspci and contents of etc/network/interfaces:

```
$ifconfig -a
enp2s0    Link encap:Ethernet  HWaddr 20:89:84:2e:a5:4e  
          inet addr:10.2.11.108  Bcast:10.2.255.255  Mask:255.255.0.0
          inet6 addr: 2001:6a0:12c:1200:2289:84ff:fe2e:a54e/64 Scope:Global
          inet6 addr: fe80::2289:84ff:fe2e:a54e/64 Scope:Link
          inet6 addr: 2001:6a0:12c:1200:a01b:d9d1:1b8:4324/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39166 errors:38515 dropped:0 overruns:38515 frame:0
          TX packets:554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61804 (61.8 KB)  TX bytes:46249 (46.2 KB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:295230 (295.2 KB)  TX bytes:295230 (295.2 KB)


wlp3s0    Link encap:Ethernet  HWaddr 9c:4e:36:96:67:50  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9e4e:36ff:fe96:6750/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3420 (3.4 KB)  TX bytes:22228 (22.2 KB)
$lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GTX 660M] (rev a1)
02:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 08)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)
###########interfaces###############
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



```

---

### Post by kajtekk71 on 2016-01-16
bump

I did some research and did some things, results:
- I can connect via cable to the router (connected via cable directly to academic network) and Wi-Fi connection with that router is also available;
- Direct cable connection with academic network is still available on Windows 7 but not on Ubuntu;
- Wired connection is detected but it blocks the Wi-Fi one, so i cannot browse the internet while connected to both
- I cannot ping default gateway when connected via cable
- sudo dhclient enp2s0 (the name of ethernet) does nothing

To be able to connect to the academic network and get the internet access, each student had to provide its computer MAC address to the administrator, then the computer was added to some database. No auxillary programs are used in this process, nor we have to log in on some site. On Windows 7 and Manjaro distro i got the internet access with no problem (nothing had to be modified manually), so i guess it's the Ubuntu's some configuration's fault. My goal is to get the wired connection working on Ubuntu. Currently i got the clean install of Ubuntu so You don't need to worry about some chaos in config files.

Can You help me? I would be grateful. Thanks in advance!

EDIT: Same problem exists on 14.04.3 LTS.

EDIT2: (On 14.04.3 LTS) Wired connection works for 1-2 seconds (loading a web page shortly after connection is successful) and then stops working. It still shows ,,connected" status, although I cannot access the internet and load websites (,,connecting..." in firefox). What is more, the wired connection can be established only after re-plugging the cable (can't just turn off wired, then turn it on to get it working). After that 1-2 seconds i get spammed with ,invalid response packet from host xxxxxx" in syslog. That doesn't happen when using wi-fi. Both devices use the same academic network, laptop and router are plugged into different sockets in my room.

EDIT3: Checked the situation on Mint 17 and Manjaro 15 distros (both running from usb), result is the same - I can access the internet for about second, then it's off, but still shows ,,connected" and so on. I wonder what's causing the problem. I guess it's something about MAC addresses and verification, cause all other networks i checked are working fine. Direct wired connection is still available on Win7 installed next to Ubuntu.

EDIT4: All wired connections act the same way - internet works only for seconds after plugging the cable. Same with Wicd. Might be a driver issue or something, i dont know.

---

### Post by kajtekk71 on 2016-01-17
Today i solved the problem :S maybe not completely, but with some workaround.
PROBLEM: There is something wrong with Qualcomm Atheros AR8161, ethernet connetcion doesn't receive packets after working for a while.
WORKAROUND: Set the MTU to 8192 for eth0 or whatever is your ethernet interface.
Marking as solved.
Bug report:
[https://bugzilla.kernel.org/show_bug.cgi?id=70761](https://bugzilla.kernel.org/show_bug.cgi?id=70761)

---

