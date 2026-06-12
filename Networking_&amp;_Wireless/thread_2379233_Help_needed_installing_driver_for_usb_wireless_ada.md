---
title: "Help needed installing driver for usb wireless adaptor!"
date: 2017-12-02
forum: Networking &amp; Wireless
---

### Post by cboujoukos on 2017-12-02
Hello all! 
Yesterday I set up my first PC, and everything was going great until I tried to get my Wireless adapter up and running. I am fairly new to linux, have been running ubuntu mate in a virtual machine on my laptop for about a month, but aside from that I have really only ever used Macs. So more about my issue.

1) When I run [FONT=courier new]usb-devices [FONT=arial]from the terminal it does see the hardware:

[/FONT][/FONT]T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=03 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=a811 Rev=02.00
S:  Manufacturer=Realtek 
S:  Product=802.11ac WLAN Adapter 
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl8812au

and lsusb returns:
 
Bus 003 Device 004: ID 0bda:a811 Realtek Semiconductor Corp.

2) I have tried installing opensource drivers for adapter from github with no luck
3) I have read through several similar posts on this forum, but unfortunately I am not Linux saavy enough to follow along once my errors divert from the errors that the poster is receiving.
4) Downloaded the Windows drivers and tried to install with ndiswrapper, but again No luck.

      But when I type [FONT=courier new]ndiswrapper -l [FONT=arial]it returns that the driver is installed and the hardware is present.

[/FONT][/FONT]chris@cboujoukos:~/Desktop/winxp/Realtek-drivers/Win10X64$ ndiswrapper -lnetrtwlanu : driver installed
    device (0BDA:A811) present (alternate driver: 8812au)


     

My current setup is as follows:

AMD Ryzen 5 1600
Gigabyte AB350-GAMING 3
PowerColor Red Devil rx570

I Honestly am at a total loss of what to try next, and any help would be GREATLY appreciated!! and let me know if you need any more info.

Thanks!

---

### Post by deadflowr on 2017-12-03
*Thread moved to **Networking and Wireless***

---

### Post by Hadaka on 2017-12-03
Hi, you dont need ndiswrapper..
see if this link helps..
[https://askubuntu.com/questions/838131/having-problems-seeing-my-wifi-ubuntu-gnome-16-04/838368#838368](https://askubuntu.com/questions/838131/having-problems-seeing-my-wifi-ubuntu-gnome-16-04/838368#838368)

---

