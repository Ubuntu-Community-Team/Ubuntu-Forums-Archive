---
title: "Rosewill RNX-N150 driver installation help"
date: 2018-02-08
forum: Networking &amp; Wireless
---

### Post by thatsmyboy on 2018-02-08
Hiya,
I'm running Ubuntu Studio today and I need to get access to the internet! I bought a nifty Rosewill USB wireless adapter [here]("https://www.newegg.com/Product/Product.aspx?Item=N82E16833166116"), but it didn't work out of the box for me. 
It has a  [linux driver on the website]("https://www.rosewill.com/it-products/wireless-networking/wireless-adapters/rosewill-rnx-n150nub-wireless-usb-n150-wi-fi-adapter.html#product_tabs_Downloads"), but I can't make heads or tails of it. Anyone care to help? 

Bus 001 Device 005: ID 0bda:ffef Realtek Semiconductor Corp. 

[https://pastebin.com/GtFbyLKP]("https://pastebin.com/GtFbyLKP")

---

### Post by wildmanne39 on 2018-02-08
I do not believe that device is support in the kernel 4.10, is there a reason you do not want to use your internal wifi card?

---

### Post by Hadaka on 2018-02-09
Hi, It seems the system is seeing the device..
[.Bus 001 Device 005: ID 0bda:ffef Realtek Semiconductor Corp. ] 
From a working wired connection first please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Then..
Please try this link..the devise I.D. is identical 0bda:ffef
[https://ubuntuforums.org/showthread.php?t=2349486](https://ubuntuforums.org/showthread.php?t=2349486)
Post #8
```
sudo apt-get install git build-essential dkms linux-headers-generic
git clone https://github.com/lwfinger/rtl8188eu.git
sudo dkms add ./rtl8188eu
sudo dkms build 8188eu/1.0
sudo dkms install 8188eu/1.0
```
reboot
```
sudo modprobe rtl8188eu
```
Thanks

---

### Post by thatsmyboy on 2018-02-10
Thanks for the tip about the previous post. I searched but I didn't see that one in there. The internal broadcom (internal) wifi uses wonky drivers, spawns all manner of errors for me. I'll try those suggestions out and get back to you guys. Thanks in advance!

---

### Post by thatsmyboy on 2018-02-11
No Joy, 
upon restart :

$ sudo modprobe rtl8188
modprobe: FATAL: Module rtl8188 not found in directory /lib/modules/4.10.0-42-lowlatency

---

### Post by jeremy31 on 2018-02-11
I think that should be ```
sudo modprobe 8188eu
```

---

### Post by thatsmyboy on 2018-02-16
Thanks, when I tried "sudo modprobe 8188eu" there was no change to my wifi, but no error either. I did some digging and found r8188eu.ko exists in the staging tree (  /lib/modules/4.10.0-42-lowlatency/kernel/drivers/staging/rtl8188eu/r8188.ko ) and 8188eu.ko exists in DKMS updates ( /lib/modules/4.10.0-42-lowlatency/updates/dkms/8188eu.ko ). But again, I still don't have wifi.

---

### Post by thatsmyboy on 2018-02-16
Just a recap of the current situation:

```
~/Downloads$ sudo dkms add ./rtl8188eu/
Error! DKMS tree already contains: 8188eu-1.0
You cannot add the same module/version combo more than once.
~/Downloads$ sudo dkms build 8188eu/1.0
Module 8188eu/1.0 already built for kernel 4.10.0-42-lowlatency/4
~/Downloads$ sudo dkms install 8188eu/1.0
Module 8188eu/1.0 already installed on kernel 4.10.0-42-lowlatency/x86_64
~/Downloads$ sudo modprobe 8188eu
~/Downloads$ sudo modprobe rtl8188eu
modprobe: FATAL: Module rtl8188eu not found in directory /lib/modules/4.10.0-42-lowlatency
```

---

### Post by jeremy31 on 2018-02-16
Does it still show in lsusb as ID 0bda:ffef Realtek Semiconductor Corp. ?

---

### Post by thatsmyboy on 2018-02-17
> **jeremy31 said:**
> Does it still show in lsusb as ID 0bda:ffef Realtek Semiconductor Corp. ?

Yes, exactly the same. Should it have changed to something more descriptive?

---

### Post by jeremy31 on 2018-02-17
That ID is not in the source code for the driver, but we can try a little trick and see if it works
```
sudo modprobe 8188eu
sudo -i
echo 0bda ffef > /sys/bus/usb/drivers/8188eu/new_id
exit
```
See if it works then

---

### Post by thatsmyboy on 2018-02-20
> **jeremy31 said:**
> That ID is not in the source code for the driver, but we can try a little trick and see if it works
```
sudo modprobe 8188eu
sudo -i
echo 0bda ffef > /sys/bus/usb/drivers/8188eu/new_id
exit
```
See if it works then

I didn't get to try out your last suggestion, I did some fiddling over the weekend with the help of [this post by Andrew Powell]("http://www.thelinuxrain.com/articles/getting-realtek-8188eu-wireless-adapters-to-work-in-linux-and-possibly-other-wireless-realtek-chipsets"). In the end, I enabled and disabled both *Network Manager* and *wicd* which seemed to be the kick in the pants it needed. I will try to reproduce the solution before I mark it solved. Thanks everybody for your help!:KS

---

