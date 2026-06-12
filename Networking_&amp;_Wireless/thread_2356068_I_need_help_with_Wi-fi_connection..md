---
title: "I need help with Wi-fi connection."
date: 2017-03-19
forum: Networking &amp; Wireless
---

### Post by pedrohba18 on 2017-03-19
So, I have recently started using ubuntu Linux and my wireless adapter doesn't seem to be working on Ubuntu because it's light doesn't turn on.
I suppose this is a driver problem, but i can't find any linux driver to download and i think i don't know what I would do with one. I'm completely laic using this operational system.
The wireless adapter model is  TP-LINK TL-WN822N.


I can't get internet without this wireless adapter. I would need a very long ethernet cable, which I do not have.
Does someone knows how to solve this problem?

---

### Post by ajgreeny on 2017-03-19
See if this thread helps.
[https://ubuntuforums.org/showthread.php?t=1905813](https://ubuntuforums.org/showthread.php?t=1905813)
You may need to use a cabled connection temporarily just for this, but then should be OK once done and connected wirelessly.

---

### Post by jeremy31 on 2017-03-19
Please post the results of ```
lsusb
```
With the WN822N plugged in

---

### Post by pedrohba18 on 2017-03-19
I put that into the terminal and here is what I've got.

$ lsusb
Bus 002 Device 005: ID 048d:1172 Integrated Technology Express, Inc. 
Bus 002 Device 004: ID 18f8:0f97  
Bus 002 Device 003: ID 2357:0108  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by RobGoss on 2017-03-19
It would be a good idea to be hard wired that way you can download and install the **proprietary drives **that Ubuntu provides   

Go to **Software & Updates** and choose the **Additional driver**, there you can install the appropriate drivers for your system

Remember you will need a internet connection to accomplish this

---

### Post by pedrohba18 on 2017-03-19
I cannot use any cable connection, I would need a very long one, and there is nowhere i can buy it.

---

### Post by jeremy31 on 2017-03-19
See [https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)

Please post result of ```
uname -a
```
I may be able to compile it for you as I noticed you have no internet access with Ubuntu

---

### Post by pedrohba18 on 2017-03-19
I can't use a cable. Sorry that won't work. ;-;

---

### Post by jeremy31 on 2017-03-19
Please post results for ```
uname -a
```
If I have the same kernel I can compile and give instructions on how to transfer it

---

### Post by pedrohba18 on 2017-03-19
I don't understand anything that is happening in the link you send. 
I will post the result of that code, just a second.

---

### Post by pedrohba18 on 2017-03-19
Here is the result:

uname -a
Linux pedro-desktop 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:41 UTC 2017 i686 i686 i686 GNU/Linux

---

### Post by jeremy31 on 2017-03-19
I am sorry as I do not use a i686 version so I cannot compile the source code

---

### Post by pedrohba18 on 2017-03-19
Here is what i get:

uname -a
Linux pedro-desktop 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:41 UTC 2017 i686 i686 i686 GNU/Linux

---

### Post by pedrohba18 on 2017-03-19
Fine, thanks.

---

### Post by RobGoss on 2017-03-20
So you stated you don't have a LAN cable correct? or at least it would have to be a long cable to connect it to your machine

You also did't tell us what kind of machine Laptop or a desktop, if it is a laptop maybe you can take that machine to a friends how and connect it there so you can download the wireless drivers needed for your machine

Is this the only OS on that machine Ubuntu?

---

### Post by jeremy31 on 2017-03-20
*Thread moved to **Networking & Wireless**.*

Is there a reason that you didn't use the 64 bit install?

You might be able to download [http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu/pool/main/r/rtl8192eu-dkms/rtl8192eu-dkms_4.4_all.deb](http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu/pool/main/r/rtl8192eu-dkms/rtl8192eu-dkms_4.4_all.deb) with an OS with internet access, copy it to a USB drive and then copy it to the Ubuntu desktop, then in terminal do
```
cd Desktop
sudo dpkg -i rtl8192eu-dkms_4.4_all.deb
```

Reboot and see if it works

---

