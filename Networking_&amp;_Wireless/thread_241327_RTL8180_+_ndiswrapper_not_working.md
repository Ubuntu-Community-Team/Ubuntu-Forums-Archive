---
title: "RTL8180 + ndiswrapper not working"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by stefanogrini on 2006-08-22
hi 
I have a Notebook Gericom in dualboot (win xp ed Ubuntu 5.1) and a wireless card RTL8180, i tried to use ndiswrapper version 1.1 found on the ubuntu CD to run the card.

I took the driver from the page of [realtek]("http://www.realtek.com.tw/downloads/downloads1-3.aspx?software=True&refdesign=True&spec=True&other=True&series=2002121&lineID=2002111&famID=2002111") 
 
i have installed the card following instructions on the wiki page of ndiswrapper  

**if i run dmesg i get this: **
 
> [4295143.067000] ndiswrapper version 1.1 loaded (preempt=no,smp=no) 
[4295143.141000] ndiswrapper: driver net8180 (Realtek,10/07/2004,5.173.1007.2004) loaded 
[4295143.141000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003) 
[4295143.141000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10 
[4295143.142000] PCI: Setting latency timer of device 0000:02:00.0 to 64 
[4295143.203000] ndiswrapper: using irq 10 
[4295144.804000] wlan0: ndiswrapper ethernet device 00:02:72:42:58:a3 using driver net8180, configuration file 10EC:8180.5.conf 
[4295144.804000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP 
[4295226.239000] ndiswrapper: device wlan0 removed 
[4295226.770000] ACPI: PCI interrupt for device 0000:02:00.0 disabled 
[4296199.371000] ndiswrapper version 1.1 loaded (preempt=no,smp=no) 
[4296199.386000] ndiswrapper: driver net8180 (Realtek,10/07/2004,5.173.1007.2004) loaded 
[4296199.397000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10 
[4296199.458000] ndiswrapper: using irq 10 
[4296201.056000] wlan0: ndiswrapper ethernet device 00:02:72:42:58:a3 using driver net8180, configuration file 10EC:8180.5.conf 
[4296201.056000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP 
[4296359.030000] wlan: 0.8.6.0 (EXPERIMENTAL) 
root@ubuntu:/home/ste/Desktop/wlan# 

 
**Running the "iwconfig wlan0 " i get this **
 
> wlan0 IEEE 802.11b ESSID:off/any 
Mode:Auto Frequency:2.412 GHz Access Point: 00:00:00:00:00:00 
Bit Rate:11 Mb/s Tx-Power:20 dBm Sensitivity=0/3 
RTS thr:2432 B Fragment thr:2432 B 
Encryption key:off 
Power Management:off 
Link Quality:100/100 Signal level:-95 dBm Noise level:-256 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 
 
 
i tried the command: iwconfig wlan0 essid default as written in instruction of the wiki
 
doesn't change nothing,  
 
what should i do? which is the problem?

---

### Post by Kosmonaut on 2006-08-22
Servus!

I´ve got a rtl8180 card. With dapperdrake I didn´t need to "ndiswrap" any windows driver to get my card working. There is allready a kernel module that supports this card. And yes! It worked out-of-the-box.
What happens when you enter this:
```
sudo depmod -a
```
```
sudo modprobe r818x
```
```
ifconfig
```
```
iwconfig
```

Greetings!

PS: The rtl8180-module should even support WPA, I guess that you need to install "wpasupplicant". And it should work. I haven´t try to encypt with WPA. Because my Wlan-Router is to old.:rolleyes:

---

### Post by stefanogrini on 2006-09-07
after 3 weeks of working and an upgrade to 6.06, I get it working.

But now at every boot i need to run all commands :( 

> iwconfig wlan0 essid ...
ifconfig wlan0 up
dhclient

is there no way to save it and automatically let the card run at every boot?

thanks 
ste

---

### Post by Kosmonaut on 2006-09-16
Well, that is hard to say.
Do you still use ndiswrapper or do you use the kernel module, to get your card working?

---

