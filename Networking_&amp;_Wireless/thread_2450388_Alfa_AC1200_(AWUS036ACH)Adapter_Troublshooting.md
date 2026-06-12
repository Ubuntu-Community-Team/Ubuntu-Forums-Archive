---
title: "Alfa AC1200 (AWUS036ACH)Adapter Troublshooting"
date: 2020-09-12
forum: Networking &amp; Wireless
---

### Post by sook628 on 2020-09-12
Im trying to get an Alfa AC1200 (AWUS036ACH) adapter working on my newly installed Ubuntu 20. When I plug the adapter in the USB, nothing happens - even the light on the device doesnt come on. Any suggestions on how to proceed?

---

### Post by jeremy31 on 2020-09-12
Post results from terminal for ```
lsusb; lsmod | grep cfg; rfkill list; mokutil --sb-state
```

---

### Post by sook628 on 2020-09-12
> **jeremy31 said:**
> Post results from terminal for ```
lsusb; lsmod | grep cfg; rfkill list; mokutil --sb-state
```




I have a second wireless card connected which is how Im connecting to internet. Hoping to change that for the AC1200 though.

---

### Post by jeremy31 on 2020-09-12
See the wireless script link in my signature and post results

---

### Post by sook628 on 2020-09-12
> **jeremy31 said:**
> See the wireless script link in my signature and post results


Its a long file. Is this what you mean?

---

### Post by jeremy31 on 2020-09-12
Try ```
cat wireless-info.txt | nc termbin.com 9999
```
Post URL

---

### Post by sook628 on 2020-09-12
> **jeremy31 said:**
> Try ```
cat wireless-info.txt | nc termbin.com 9999
```
Post URL

What are you looking at in these outputs? I'd like to understand how you're troubleshooting thing

---

### Post by jeremy31 on 2020-09-12
Results weren't complete for some reason, can you post results for ```
modinfo rtl8812au; dkms status
```
The results usually show a lot more info about the device, driver used and some messages from the error log that are useful in figuring out what the issue might be

---

### Post by sook628 on 2020-09-12
> **jeremy31 said:**
> Results weren't complete for some reason, can you post results for ```
modinfo rtl8812au; dkms status
```
The results usually show a lot more info about the device, driver used and some messages from the error log that are useful in figuring out what the issue might be

Results

---

### Post by jeremy31 on 2020-09-12
That info looks ok, what about ```
dmesg | grep 8812
```

---

### Post by sook628 on 2020-09-12
> **jeremy31 said:**
> That info looks ok, what about ```
dmesg | grep 8812
```

Results

---

### Post by jeremy31 on 2020-09-12
I would do ```
sudo apt remove rtl8812au-dkms
sudo apt install git build-essential dkms
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
```
Reboot

---

### Post by sook628 on 2020-09-12
> **jeremy31 said:**
> I would do ```
sudo apt remove rtl8812au-dkms
sudo apt install git build-essential dkms
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
```
Reboot

That worked. Can you tell me what the issue was and how the above commands fixed it?

Thanks

---

### Post by jeremy31 on 2020-09-12
There were some weird errors with the other driver like it wasn't patched for your kernel.  I use this other driver for a rtl8814au wifi device but it works for rtl8812au, rtl8814au, and rtl8821au

---

### Post by sook628 on 2020-09-12
> **jeremy31 said:**
> There were some weird errors with the other driver like it wasn't patched for your kernel.  I use this other driver for a rtl8814au wifi device but it works for rtl8812au, rtl8814au, and rtl8821au

Thanks for your help

---

