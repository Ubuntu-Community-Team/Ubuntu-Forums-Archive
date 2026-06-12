---
title: "Wireless USB not recognised"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Paul T. on 2011-06-27
I've just installed Ubuntu on an old Compaq Presario 700 laptop; this doesn't have a wireless network so am trying to use a 'Texet' wireless USB adapter. However it seems that Ubuntu doesn't recognise it as it doesn't seem to be turned on, and options for connecting to wireless networks are greyed out.
Any advice on how to initialise it much appreciated.

(Previously I have tried Puppy Linux & Lubuntu on this laptop and both recognised the wireless immediately, but Ubuntu doesn't?)

Paul.

---

### Post by gandaran on 2011-06-27
we need to know the adapter chipset, maybe you have to install drivers, type in terminal this and post the output
```
lsusb
```

---

### Post by wolfen69 on 2011-06-27
You can also check the *additional drivers* section in ubuntu to see if a driver is offered for download. Of course you'll need to be plugged onto the internet so you can download the file.

---

### Post by Paul T. on 2011-06-27
Ok, you'll have to bear (bare?) with me as I cannot copy & paste the output from terminal,

lsusb says that it's a 8171 Realtek chipset.

nm-tool says:

Device: wlan0
Type: 802.11 WiFi
Driver: rtl819xU
State: disconnected 

Hope this helps.

Tried to connect via lan cable, but this didn't work either. :(

---

### Post by gandaran on 2011-06-28
> **Paul T. said:**
> Ok, you'll have to bear (bare?) with me as I cannot copy & paste the output from terminal,

lsusb says that it's a 8171 Realtek chipset.

nm-tool says:

Device: wlan0
Type: 802.11 WiFi
Driver: rtl819xU
State: disconnected 

Hope this helps.

Tried to connect via lan cable, but this didn't work either. :(
should work out of the box on ubuntu 11.04, which ubuntu version do you have?
try this code
```
sudo ifup wlan0
```

---

### Post by Paul T. on 2011-06-28
I've installed 10.04.2 LTS. I previously tried Lubuntu 11.04 where the adapter did work out of the box.

Anyway, sudo ifup wlan0 says:

Ignoring unknown interface wlan0=wlan0

:confused:

---

### Post by gandaran on 2011-06-28
> **Paul T. said:**
> I've installed 10.04 LTS. I previously tried Lubuntu 11.04 where the adapter did work out of the box.

Anyway, sudo ifup wlan0 says:
Ignoring unknown interface wlan0=wlan0
:confused:
you do have to install the drivers for 10.04, you can get them from the realtek drivers website, sorry I don't have any other solution.

---

### Post by Paul T. on 2011-06-28
> **gandaran said:**
> you do have to install the drivers for 10.04, you can get them from the realtek drivers website, sorry I don't have any other solution.


Gandaran, thx for your help; may be quicker for me to simply wipe the hd and install 11.04 instead. ](*,)

---

### Post by gandaran on 2011-06-28
> **Paul T. said:**
> Gandaran, thx for your help; may be quicker for me to simply wipe the hd and install 11.04 instead. ](*,)
I would recommend that too and if you don't like the unity desktop you can still set Ubuntu to use classic gnome mode.

---

### Post by Paul T. on 2011-06-28
Have just downloaded 11.04.
Had a quick look on Realtek website but can only see Windows drivers.

---

### Post by Paul T. on 2011-06-28
Installed 11.04, wireless works out of the box. :P

---

