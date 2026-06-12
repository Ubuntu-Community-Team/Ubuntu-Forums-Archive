---
title: "Huawey k4203 modem no tty channel"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by Dr_Lion on 2016-02-04
I'm running ubuntu server 14.04.3, i installed gsm[FONT=verdana]-utils and usb_m[/FONT]odeswitch through apt-get install.

My modem vendorid is 0x12d1 and product id 0x1590, at the begining this modems use to address at 1f1c..

I 've tried some commands like:

> sudo modprobe usbserial vendor=0x12d1 product=0x1590

[FONT=verdana]and i edited the file /lib/udev/rules.d/40-usb_modeswitch.rules to add:[/FONT]

> # Vodafone Mobile Broadband (Huawei) K4305
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1f15", RUN+="usb_modeswitch '%b/%k'"


[FONT=verdana]i did not try this:[/FONT] 

> sudo usb_modeswitch -v 12d1 -p 1f1c -W -I -M 55534243123456780000000000000011062000000101000100000000000000

[FONT=verdana]because my product id is 1590 and not 1f1c so i dont know if im supposed to.

My modem is connected and it is blinking a green (or blue, im not sure now) light. When i run "ifconfig" i dont see the modem interface, when i run "lsusb" it is there Huawei.... When i run dmesg it is weird because it recognises the device, but the line that says "device on tty..." is missing!!

So i suspect that the modem is there but i cant access it through terminal. Is there a way to manally create a tty to interact with it? I only wanted to send some sms with it, but i would like the process to be auto, instead of going to the web page and sent the sms with mouse commands..
I did list ttyU* and ttyS* and got nothing also!

I did try to send sms with gmssendsms but offcourse it gives an error 22, because my tty is not right... that is really all i wanna do, is just send some sms with it... i could use any other software, i also tried gammu, but i suspect it has more problems than gsm-utils...


Now im not able to post, but tomorrow i can post any output needed to get some help, if someone could give me a hand, i fried my head off for two 2 long days and got nothing..

dmesg:
> [   90.073273] usb 1-3: new high-speed USB device number 5 using ehci-pci
[   90.207193] usb 1-3: New USB device found, idVendor=12d1, idProduct=1590
[   90.207218] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   90.207235] usb 1-3: Product: HUAWEI Mobile
[   90.207250] usb 1-3: Manufacturer: Vodafone(Huawei)
[   90.458192] cdc_ether 1-3:1.0 eth0: register 'cdc_ether' at usb-0000:00:1d.7-3, CDC Ethernet Device, 00:1e:10:1f:00:00
[   90.458277] usbcore: registered new interface driver cdc_ether
[   92.621736] usbcore: registered new interface driver usbserial
[   92.621791] usbcore: registered new interface driver usbserial_generic
[   92.621829] usbserial: USB Serial support registered for generic
[   92.662244] usbcore: registered new interface driver option
[   92.662320] usbserial: USB Serial support registered for GSM modem (1-port)


lsusb:
> 
Bus 001 Device 005: ID 12d1:1590 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0709:9137 Silicon Systems, Ltd (SSL) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 040b:2000 Weltrend Semiconductor 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


usb-devices:
> 
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1590 Rev=01.02
S:  Manufacturer=Vodafone(Huawei)
S:  Product=HUAWEI Mobile
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=06 Prot=00 Driver=cdc_ether


Any help why i'm not getting tty?
[/FONT]

---

### Post by Dr_Lion on 2016-02-05
Well at the moment and after install wvdial, gnome-ppp, usbserial, etc and gnome-desktop. I can access the huawei modem through web browser, and from there i can control the modem (turn on mobile data, send sms, etc) but what i want is to send sms through terminal... and this still my problem because i can't figure which "/dev/tty" should i connect to send the sms by cmdline. Any help available?

I got this outputs:

dmesg:
> [    1.813786] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    1.862129] r8169 0000:02:00.0 p1p1: renamed from eth0
[    1.862969] usb 1-3: New USB device found, idVendor=12d1, idProduct=1590
[    1.862979] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.862986] usb 1-3: Product: HUAWEI Mobile
[    1.862991] usb 1-3: Manufacturer: Vodafone(Huawei)
[    1.873996] systemd-udevd[116]: renamed network interface eth0 to p1p1


lsusb:
> Bus 001 Device 003: ID 12d1:1590 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0709:9137 Silicon Systems, Ltd (SSL) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 040b:2000 Weltrend Semiconductor 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


usb-devices:T:  
> Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1590 Rev=01.02
S:  Manufacturer=Vodafone(Huawei)
S:  Product=HUAWEI Mobile
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=06 Prot=00 Driver=cdc_ether

ifconfig:
> eth0      Link encap:Ethernet  HWaddr XX:XX:XX:xx:xx:xx  
          inet addr:192.168.9.100  Bcast:192.168.9.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:10ff:fe1f:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:455558 (455.5 KB)  TX bytes:13132 (13.1 KB)


route -n:
> 192.168.9.0     192.168.9.100   255.255.255.0   UG    800    0        0 eth0

This eth0 is the interface from huawei usb modem that i would like to access not from the browser but by cmd, sending sms through browser will be such a pain since i even cant find the webserver or site "served by modem" at the address 192.168.9.1.

Again, any ideas?

---

