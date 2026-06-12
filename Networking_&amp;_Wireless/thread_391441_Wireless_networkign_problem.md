---
title: "Wireless networkign problem"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by andrewlondonuk on 2007-03-23
HI, i've looked in device manager and can see that ubuntu has detected my wireless network card. The problem is, when i go to the networking control panel and try and configure the wireless card it doesn't enable the connection when i click "enable connection". Any pointers? I'm guessing it would be handy if i could see if ubuntu has actually detected the adapter, then i could go from there.

Thanks

---

### Post by chili555 on 2007-03-23
You can find out if Ubuntu has actually detected your wireless card by opening a terminal and doing:```
iwconfig
```You should have an interface with a lot of information next to it. Make a note of the relevant interface, eth1 or wlan0 or ra0 or whatever. Then do:```
sudo iwlist <your_interface> scan
```That will show you your, and several others, possibly, access point that you want to connect to. The most important parts are the ESSID and whether encryption is in place. Then you can go back to the networking control panel, put in the ESSID and try again. Bear in mind that belkin is not the same as Belkin is not the same as BELKIN. Neatness counts.

If you need to set up encryption, WEP, WPA, etc. post back and let us know.

---

### Post by andrewlondonuk on 2007-03-23
I run both commands, i'm guessing this is the wireless card? The problem is, when i run the second command you posted it spits out the following: 

andrew@andrew-laptop:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning : No such device


Any ideas what else i can try?


The interface details are below:
eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2007-03-23
Sometimes these devices wake up if we hit them on the head with```
sudo ifconfig eth1 up
```Sometimes not. Please try scan again after that. If that doesn't produce the information we want, you'll need to go into the administration pages of the router and carefully get it's ESSID and MAC address. It will be a 12-digit hex number like this:  00:12:0E:46:0C:88. It may show on the back or bottom of your router like this:  00120E460C88.

Then sudo gedit /etc/network/interfaces to amend the eth1 section only to look like this:```
auto eth1
iface eth1 inet dhcp
wireless-essid whatyoufound
wireless-ap  00:12:0E:46:0C:88 
``` Or whatever MAC address you found.

Restart networking sudo /etc/init.d/networking restart and let us know.

---

### Post by kevinatkins on 2007-03-23
Hi,

The interface to use may well be wlan0 instead of eth1 - try it and see what happens. It might also be worth having a look at the system logs for nuggets of information relating to your wireless card - try entering 'dmesg | grep wlan0' in a terminal window and see what comes back (omit the quote marks!)

---

