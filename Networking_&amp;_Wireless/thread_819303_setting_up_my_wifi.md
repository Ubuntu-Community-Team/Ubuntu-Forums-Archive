---
title: "setting up my wifi"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by kalju24 on 2008-06-05
i just joined ubuntu with my hp compaq nx 6110 and i wanted to join wifi but i dont know how it was easy on windows but not here can somebody help me and by the way i have broadcoam or something card i need step by step info 
thx for the info

---

### Post by hal10000 on 2008-06-05
Hi,
the first you shoul do is to give some info about your card. You can do this by opening a terminal window ( in gnome i guess it can be found in the menu Applications--->Terminal window or something similar, don't use gnome, so i cant't tell you the exact menu-position).
Then type in the following commands and post their output here (you can mark the output with your mouse and paste it with the middle mouse button)

1.
> 
iwconfig

2.
> 
cat /etc/network/interfaces

3.
> 
ifconfig

4.
If your wireless card is built-in or a pci-card then
> 
lspci

> 
lspci -n

or, if your wireless device is an usb stick:
> 
lsusb

After you have posted the output we can go further.

---

### Post by kalju24 on 2008-06-06
administrator@M44LAP195:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"JALAX"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


administrator@M44LAP195:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface wlan0 inet static
address 194.168.0.195
netmask 255.255.0.0
gateway 194.168.0.36
wireless-key **********
wireless-essid JALAX











iface eth0 inet static
address 194.168.0.195
netmask 255.255.0.0
gateway 194.168.0.79







auto eth0

auto wlan0

administrator@M44LAP195:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:38:15:d0:c0  
          inet addr:194.168.0.195  Bcast:194.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::214:38ff:fe15:d0c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:758 errors:0 dropped:0 overruns:0 frame:0
          TX packets:307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:360665 (352.2 KB)  TX bytes:36375 (35.5 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74427 (72.6 KB)  TX bytes:74427 (72.6 KB)

administrator@M44LAP195:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

administrator@M44LAP195:~$ lspci -n
00:00.0 0600: 8086:2590 (rev 03)
00:02.0 0300: 8086:2592 (rev 03)
00:02.1 0380: 8086:2792 (rev 03)
00:1d.0 0c03: 8086:2658 (rev 03)
00:1d.1 0c03: 8086:2659 (rev 03)
00:1d.2 0c03: 8086:265a (rev 03)
00:1d.3 0c03: 8086:265b (rev 03)
00:1d.7 0c03: 8086:265c (rev 03)
00:1e.0 0604: 8086:2448 (rev d3)
00:1e.2 0401: 8086:266e (rev 03)
00:1e.3 0703: 8086:266d (rev 03)
00:1f.0 0601: 8086:2641 (rev 03)
00:1f.1 0101: 8086:266f (rev 03)
00:1f.3 0c05: 8086:266a (rev 03)
02:04.0 0280: 14e4:4320 (rev 03)
02:06.0 0607: 104c:8031
02:06.2 0c00: 104c:8032
02:0e.0 0200: 14e4:170c (rev 02)





THAT was what i got i diidnt to usb scan because i dont have a usb wificard

---

### Post by hal10000 on 2008-06-06
Your card is a Broadcom Corporation [COLOR="Red"]BCM4306[/COLOR] 802.11b/g Wireless LAN Controller (rev 03).

First of all, because you configured your network-devices manually (your wireless [COLOR="Red"]and[/COLOR] ethernet card) are you sure, you have setup your ip-addresses correctly?

I ask this, because in almost every case you need a [COLOR="Red"]private ip-address-range[/COLOR] to get your network working and these private addresses must start with either [COLOR="Red"]192.168.X.X[/COLOR] or with [COLOR="Red"]10.X.X.X[/COLOR], but your ip- addresses (for ethernet-card and wireless) starts with 194.168.X.X; this is not a private ip-address.

To prevend me from confusing me more and more you should tell me something more about the way you are connected through your network.

Does your ethernet-connection work? (try [COLOR="Red"]ping 194.168.0.79[/COLOR] and [COLOR="Red"]ping [www.google.com](www.google.com)[/COLOR] (or another address in the internet like [COLOR="Red"]ping [www.nasa.gov](www.nasa.gov)[/COLOR])

It seems as if you are connected via two routers (one wired and one wireless) , is that right?

The driver for your wireless network-card should be a file called  bcm43xx.ko
You can test if it is already loaded with the following command:
> 
lsmod | grep bcm

If you get an answer, then it is loaded (i suppose this is the case).
If not then you can manually load it with [COLOR="Red"]sudo modprobe bcm43xx[/COLOR] (without the .ko suffix).

But before we go on configuring the wireless card we have to be sure about your general network (router, Accesspoint, ip-addresses etc.)

---

### Post by kalju24 on 2008-06-06
yes my ip is right im in my office everyone has their own ip and thats mine i used the same ones when i used windows

---

### Post by kalju24 on 2008-06-06
administrator@M44LAP195:~$ sudo modprobe bcm43xx
[sudo] password for administrator: 
administrator@M44LAP195:~$ sudo modprobe bcm43xx

and i tried it so also
root@M44LAP195:/home/administrator# sudo modprobe bcm43xx
root@M44LAP195:/home/administrator# 

it dosent do nothing

and bytheway i have ubuntu 8.04 hardy

---

