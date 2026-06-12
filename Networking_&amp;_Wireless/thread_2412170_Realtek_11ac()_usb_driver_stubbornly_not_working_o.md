---
title: "Realtek 11ac(?) usb driver stubbornly not working on 18.04"
date: 2019-02-08
forum: Networking &amp; Wireless
---

### Post by foxstew on 2019-02-08
Recently decided on Ubuntu for my hand built PC. Everything has been working perfectly, except for one thing:
THE WIFI ADAPTER. :mad:

Everything I've thrown at this stupid piece of junk wont work. I really, REALLY, don't want to buy a new adapter because i cant return the current one. My SSD is crammed full of various drivers, install scripts, you name it. The drivers on the provided MiniCD won't work, and even the internet hasn't come up with anything. I really, really need help.

paste-bin from running the wireless info script:
[http://paste.ubuntu.com/p/yHZt3px2Cx/](http://paste.ubuntu.com/p/yHZt3px2Cx/)

adapter info:
Blueshadow 600M wireless AC600, dual band, USB 2.0, IEEE 802.11b/g/n/ac

Has a realtek driver (?)

usb-devices turns up
T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=0811 Rev=02.00
S:  Manufacturer=Realtek 
S:  Product=802.11ac WLAN Adapter 
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
so the adapter isnt broken, its obviously sending info to the computer, but none of the drivers work

thanks

---

### Post by jeremy31 on 2019-02-10
Moved to Networking, open a terminal and do
```
sudo apt install git dkms build-essential
git clone https://github.com/gnab/rtl8812au.git
sudo dkms add ./rtl8812au
sudo dkms install 8812au/4.2.2
```
Reboot

---

### Post by foxstew on 2019-02-10
i'll try that, thank
EDIT: THANK YOU IVE BEEN TRYING TO GET THIS STUPID THING TO WORK FOR ABOUT A MONTH THANK YOU THANK YOU THANK YOU.

---

