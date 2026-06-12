---
title: "No wireless after up upgrading to Ubuntu 14.04"
date: 2014-07-12
forum: Networking &amp; Wireless
---

### Post by humanracer on 2014-07-12
Hi
I just upgraded to the latest version of ubuntu but my wireless network will not appear. My wireless switch is on. 

I followed the instructions and downloaded b43 whatever that its.

I then followed the following instructions in another thread


Code:

sudo mkdir /lib/firmware/b43-open
sudo cp /lib/firmware/b43/*  /lib/firmware/b43-open

Unload and reload:
Code:

sudo modprobe -r b43
sudo modprbe b43

Check:
Code:

dmesg | grep b43


Now I get the errors

[   14.983458] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.025657] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   15.107947] b43 ssb0:0: Direct firmware load failed with error -2
[   15.107960] b43 ssb0:0: Falling back to user helper
[   16.410374] b43 ssb0:0: Direct firmware load failed with error -2
[   16.410388] b43 ssb0:0: Falling back to user helper
[   16.520401] b43 ssb0:0: Direct firmware load failed with error -2
[   16.520414] b43 ssb0:0: Falling back to user helper
[   16.546679] b43 ssb0:0: Direct firmware load failed with error -2
[   16.546693] b43 ssb0:0: Falling back to user helper
[   16.558022] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   16.558225] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   16.558416] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  189.084905] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  189.128303] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[  189.152510] b43 ssb0:0: Direct firmware load failed with error -2
[  189.152529] b43 ssb0:0: Falling back to user helper
[  189.161290] b43 ssb0:0: Direct firmware load failed with error -2
[  189.161314] b43 ssb0:0: Falling back to user helper
[  189.173833] b43 ssb0:0: Direct firmware load failed with error -2
[  189.173846] b43 ssb0:0: Falling back to user helper
[  189.183436] b43 ssb0:0: Direct firmware load failed with error -2
[  189.183450] b43 ssb0:0: Falling back to user helper
[  189.197078] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[  189.197093] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[  189.197102] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware 

I tried the link above and got the message

humanracer@humanracer-Compaq-Mini-110c-1100:~$ sudo apt-get install firmware-b43-installer
[sudo] password for humanracer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer




If the problem cannot be solved can someone tell me the most modern version of Ubuntu or any other Linux OS that will support my wireless without having to do any complicated stuff?

I am using an Acer mini 110.


Many thanks in advance

---

### Post by chili555 on 2014-07-12
Please try:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```

---

### Post by humanracer on 2014-07-12
Thanks for suggestion but got it working. I tried the following:

[TABLE]
[TR]
[TD="class: votecell"]      

              [/TD]
                [TD="class: answercell"]                  You need to:
  sudo apt-get update && apt-cache search b43 
  To find the firmware package. Then again:
  sudo apt-get install firmware-b43-installer

[/TD]
[/TR]
[/TABLE]

---

