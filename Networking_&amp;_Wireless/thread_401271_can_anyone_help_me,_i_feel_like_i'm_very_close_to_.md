---
title: "can anyone help me, i feel like i'm very close to getting my networkcard to work"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by notsteve on 2007-04-04
i have a broadcom 4318 network card in my aer aspire 5000, i`v gone through all the steps and the driver bcml5 is installed and present but the light to show the network card is not working.

all the steps go fine until i write:
steve@steve-laptop:~$ sudo ndiswrapper -m
then this pops up:
modprobe config already contains alias directive
is this normal, if so why does my network card not work.

---

### Post by chili555 on 2007-04-04
Please let us see ```
iwconfig
```. When you run the command, one of the interfaces, wlan0 possibly, will have a lot of text next to it. This is your wireless interface. Then do:```
iwlist <your_wireless_interface> scan
```Please let us see the result.

Any encryption on your network? WEP, WPA or Romulan?> modprobe config already contains alias directive
is this normalProbably. It just means, 'what you asked to be done is already done.'

---

### Post by notsteve on 2007-04-04
ok this is what happens when i type in iw config:

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by notsteve on 2007-04-04
my

---

### Post by notsteve on 2007-04-04
it claimed there is no scan results, the one with a lot of tet next to it is eth1

---

### Post by joeally on 2007-04-04
I'm having the exact same problem but with an rt73 based belkin usb thingy magigy (fd7050)

I used ndiswrapper and my iwconfig comes out just like ures. The light keeps on flashing.

arghh i am so close yet so far

---

### Post by Floppyjoe on 2007-04-04
NotSteve, Did you do:
```
sudo iwlist eth1 scan
```
or 
```
iwlist eth1 scan
```
?

---

### Post by zombiepunkcaptain on 2007-07-05
Hi guys, I also have a Belkin FD7050,

results of sudo iwconfig rausb0 scan are

rausb0    Interface doesn't support scanning : Network is down

---

