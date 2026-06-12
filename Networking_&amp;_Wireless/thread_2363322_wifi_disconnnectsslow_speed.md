---
title: "wifi disconnnects/slow speed"
date: 2017-06-08
forum: Networking &amp; Wireless
---

### Post by snix101 on 2017-06-08
Hi there,

 I've just bought a USB Wireless Adapter IT WORKS AC600 for my computer

In terminal I type lsusb and the usb adapter was shown as:

Bus 002 Device 006: ID 148f:fffe Ralink Technology, Corp.

How do i configure the adapter to make it work ? i can' find anything on line, maybe because it is a brand new USB wireless adapter ....

Ubuntu 16.04.2 LTS
kernel : 4.8.0-36-generic

---

### Post by wildmanne39 on 2017-06-08
If it is that new then it may not work in Ubuntu yet plug it in and run the wireless script in my signature.

---

### Post by snix101 on 2017-06-08
> **wildmanne39 said:**
> If it is that new then it may not work in Ubuntu yet plug it in and run the wireless script in my signature.

Thanks for the feedback, an update & upgrade have been done but no effect

here is my wireless info : **[https://pastebin.com/hVz2SXVp](https://pastebin.com/hVz2SXVp)**

---

### Post by wildmanne39 on 2017-06-08
I did not find any information that suggests there is a driver for your device, I take it your internal device is slow and disconnects correct? we can make several changes that will help.

---

### Post by snix101 on 2017-06-09
> **wildmanne39 said:**
> I did not find any information that suggests there is a driver for your device, I take it your internal device is slow and disconnects correct? we can make several changes that will help.

where i stand at home my device catches a very low signal from the public wifi box.

 i 've bought this usb wireless adapter in order to catch more signal from home, it worked a few month ago with an other usb wireless adapter : the D-Link DWA-171 . unfortunately, i don't have this one any more ...

of course if your have any suggestion to improve my internal device range of detection , i am all ears !

---

### Post by wildmanne39 on 2017-06-09
Please run the commands one line at a time, copy and paste for accuracy:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Check the settings in your router. WPA2-AES (CCMP) is best, not WPA and WPA2 mixed mode and do not use TKIP. 

Next, if your router is capable of N speeds, you will probably have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. You also should set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.
You have way to many networks in your range, and some appear to have the same name, can you rename the one you want to connect too?

Go into network manager and set your settings to match the screnshots.
If you are in in France do" 
```
sudo iw reg set FR
```
```
sudo sed -i 's/^REG.*=$/&FR/' /etc/default/crda
```
Reboot

---

### Post by snix101 on 2017-06-09
> **wildmanne39 said:**
> Please run the commands one line at a time, copy and paste for accuracy:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

Thanks for the advise, these commands really help to speed things up online.

i've tried the ndiswrapper process (netr28ux.inf / WINDOWS 10 32 bit) in order to install my  IT WORKS AC600 USB wireless adapter but it didn't work neither. i guess i will have to wait the release of the linux driver a  little bit...

Once again thanks for the support, it was very usefull.

---

### Post by wildmanne39 on 2017-06-09
I am glad it helped, if it is okay with you I will change the title of this thread and you can mark it solved so people that are having issues with the same internal card you have will find this one marled solved and it will help them too.

Your Welcome!

---

### Post by snix101 on 2017-06-09
> **wildmanne39 said:**
> I am glad it helped, if it is okay with you I will change the title of this thread and you can mark it solved so people that are having issues with the same internal card you have will find this one marled solved and it will help them too.

Your Welcome!


sure it is fine by me !

---

