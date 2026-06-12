---
title: "No WiFi Adapter HP AU008TX issue"
date: 2018-12-25
forum: Networking &amp; Wireless
---

### Post by bhanu904 on 2018-12-25
I have tried almost all the methods but none of them work for me 

WiFi was running good on dual boot all of sudden something happened (i tried to access Ubuntu files from windows using an external software .. may be i got issue at this time and from then onwards wifi stopped working both on windows as well as Ubuntu)

i have have diagnostic process as mentioned in the pinned thread

Here is the link : [http://paste.ubuntu.com/p/txJXfnDc7C/](http://paste.ubuntu.com/p/txJXfnDc7C/)


UBUNTU 18.04 and Windows 10 Dual boot 

i have tried this way as well its not working :( 

[https://ubuntuforums.org/showthread.php?t=2392454](https://ubuntuforums.org/showthread.php?t=2392454)

---

### Post by praseodym on 2018-12-25
Please show the full outputs of
```

lspci -nnk
usb-devices
lsmod
```

---

### Post by bhanu904 on 2018-12-25
> **praseodym said:**
> Please show the full outputs of
```

lspci -nnk
usb-devices
lsmod
```


Here is the outputs of 3 codes :  [https://paste.ubuntu.com/p/hwrPMWGWqb/](https://paste.ubuntu.com/p/hwrPMWGWqb/)

By the way i am using mobile network USB teathering to access the internet atm

---

### Post by jeremy31 on 2018-12-25
Is wifi disabled in BIOS?

---

### Post by bhanu904 on 2018-12-25
> **jeremy31 said:**
> Is wifi disabled in BIOS?

I think no.... There is no such option available in my BIOS SETTINGS 

[https://imgur.com/a/jyf4eWE](https://imgur.com/a/jyf4eWE)



To add to this.... Bluetooth shows continuesly on in Ubuntu... Without any WiFi.... When I try to switch off Bluetooth Ubuntu goes into airplane mode.... 

2 option only
Bluetooth on
Off Bluetooth it's goes to airplane mode

---

### Post by jeremy31 on 2018-12-25
Bus 001 Device 004: ID 8087:0a2a Intel Corp is your bluetooth device and I am sure that is on the same chip as the wifi, the only difference is that the wifi should show in lspci results and it doesn't
You might need to reset BIOS to defaults and see if wifi works again

---

### Post by bhanu904 on 2018-12-25
> **jeremy31 said:**
> Bus 001 Device 004: ID 8087:0a2a Intel Corp is your bluetooth device and I am sure that is on the same chip as the wifi, the only difference is that the wifi should show in lspci results and it doesn't
You might need to reset BIOS to defaults and see if wifi works again


Just did that still no luck :(


Earlier I even tried factory resetting my pc... But it still didn't work

---

### Post by jeremy31 on 2018-12-25
I would power off, remove bottom panel and see if the wifi card is still properly attached to the motherboard

---

### Post by bhanu904 on 2018-12-31
> **jeremy31 said:**
> I would power off, remove bottom panel and see if the wifi card is still properly attached to the motherboard

Solved...i couldn't do it myself, took it to service center... WiFi card was disconnected. Now it's fine

---

