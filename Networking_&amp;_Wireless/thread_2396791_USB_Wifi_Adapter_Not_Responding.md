---
title: "USB Wifi Adapter Not Responding"
date: 2018-07-20
forum: Networking &amp; Wireless
---

### Post by alucardzm on 2018-07-20
[SIZE=2]Hello,

Couple of months back I got a USB WiFi adapter to use because the built in card in my laptop has been dreadfully slow in public places like my school's library. It's the [/SIZE][COLOR=#111111][FONT=&amp]OURLINK 600Mbps AC600 Dual Band USB WiFi Dongle I got from Amazon. It's worked fantastic on my Windows 10 OS since I got it, but when I boot into my Ubuntu OS it's unable to turn on and operate at all. 

I've looked around and tried to install the driver for the particular chipset in the dongle, but I've hit some bumps along the way and, frankly speaking since I'm new to Linux I'm unsure if I even installed it properly. 

I have gone ahead and used lsusb to figure out what my computer sees with when I plug it in (it's the one that's in bold):
[/FONT][/COLOR]
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 001 Device 017: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
**Bus 001 Device 018: ID 0bda:a811 Realtek Semiconductor Corp. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 001 Device 017: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

As well as sudo tail -n 0 -f /var/log/syslog to keep track of it as soon as I plug it in:  

```

Jul 20 15:54:18 alex-X550JF kernel: [ 2635.376075] usb 1-1: new high-speed USB device number 20 using xhci_hcd
Jul 20 15:54:18 alex-X550JF kernel: [ 2635.516507] usb 1-1: New USB device found, idVendor=0bda, idProduct=a811
Jul 20 15:54:18 alex-X550JF kernel: [ 2635.516513] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 20 15:54:18 alex-X550JF kernel: [ 2635.516518] usb 1-1: Product: 802.11ac WLAN Adapter 
Jul 20 15:54:18 alex-X550JF kernel: [ 2635.516522] usb 1-1: Manufacturer: Realtek 
Jul 20 15:54:18 alex-X550JF kernel: [ 2635.516526] usb 1-1: SerialNumber: 00e04c000001
Jul 20 15:54:18 alex-X550JF mtp-probe: checking bus 1, device 20: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1"
Jul 20 15:54:18 alex-X550JF mtp-probe: bus: 1, device: 20 was not an MTP device

```


[COLOR=#111111][FONT=&amp]Any help would be appreciated it, and if nothing works well any good recommendations on a better WiFi dongle? 

Cheers! 
[/FONT][/COLOR]

---

### Post by jeremy31 on 2018-07-20
I would try the following and reboot
```
sudo apt-get install dkms git build-essential
 git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
 cd rtl8812AU_8821AU_linux
 sudo make -f Makefile.dkms install
```

---

### Post by alucardzm on 2018-07-20
OK I did just that and it seems to have install properly. However, once I rebooted I'm certain it's not using the adapter to connected since I remove it and it doesn't cause a hiccup, because it's probably still using the inboard card.

---

### Post by jeremy31 on 2018-07-20
Post results for ```
lspci -nnk | grep -iA3 net
```
And I will be able to tell you how to temporarily disable the internal

---

### Post by alucardzm on 2018-07-20
```

03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave AW-NE186H [1a3b:1186]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169
	Kernel modules: r8169



```

---

### Post by jeremy31 on 2018-07-20
```
sudo modprobe -r ath9k
```
Will stop the internal from working until reboot.  Let me guess, it has bad reception

If you want to enable the internal without rebooting do ```
sudo modprobe ath9k
```

---

### Post by alucardzm on 2018-07-20
How about no connection at all haha... :(

I did just that and then waited a good couple of minutes and then just turned it back on (I figured if i just removed the -r it should turn back on and it did). While it was off I did run ifconfig and yeah the onboard card was disabled properly, but no registry of my adapter was present at all:

Off:
```

alex@alex-X550JF:~$ ifconfig
enp4s0f1  Link encap:Ethernet  HWaddr 1c:b7:2c:2e:a3:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103921 (103.9 KB)  TX bytes:103921 (103.9 KB)



```

On:
```

enp4s0f1  Link encap:Ethernet  HWaddr 1c:b7:2c:2e:a3:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106515 (106.5 KB)  TX bytes:106515 (106.5 KB)


wlp3s0    Link encap:Ethernet  HWaddr 40:e2:30:c5:04:09  
          inet addr:172.25.42.87  Bcast:172.25.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7874:1864:9f39:13f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1657 (1.6 KB)  TX bytes:1607 (1.6 KB)



```

---

### Post by jeremy31 on 2018-07-20
What results for ```
modprobe -c | grep -i a811; mokutil --sb-state
```

---

### Post by alucardzm on 2018-07-20
```

alias usb:v0BDApA811d*dc*dsc*dp*ic*isc*ip*in* 8812au
alias usb:v0BDApA811d*dc*dsc*dp*ic*isc*ip*in* rtl8812au
alias usb:v0BDApA811d*dc*dsc*dp*ic*isc*ip*in* rtl8812au
alias usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in* 8812au
alias usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in* rtl8812au
SecureBoot enabled

```

---

### Post by jeremy31 on 2018-07-20
Go into BIOS/UEFI settings and disable Secure Boot as it prevents compiled kernel modules from loading.

---

### Post by alucardzm on 2018-07-20
Dude! Holy hell finally! I've had this for months trying to figure out how to get it to work and it's been killing me. Come to find out it was simply a BIOS settings. If you don't mind me asking what is Secure Boot anyways?

Thank you so much! It works just as I expected it to work on Windows! Now I don't ever feel compelled to go back into Windows for some time since I finally have good internet speed lol.

Quick Edit/Update: It's a bit iffy, definitely better than my inboard card, but actually a little slower than on Windows, but I don't think that's much of an issue or fixable lol. As a quick question, do I have to keep disabling my onboard card using the command you gave me or just manage the connection through the general ubuntu settings?

---

