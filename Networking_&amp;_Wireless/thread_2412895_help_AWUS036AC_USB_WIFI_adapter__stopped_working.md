---
title: "help AWUS036AC USB WIFI adapter  stopped working"
date: 2019-02-18
forum: Networking &amp; Wireless
---

### Post by Gadget2008 on 2019-02-18
Hi
I got AWUS036AC USB WIFI adapter and just stopped working for some reason. It was working a few hours ago...When i bought this alfa adapter I use this command to install this adapter  sudo apt-get install rtl8812au-dkms.
It was working fine but now stopped, Can anyone help to get this AWUS036AC USB WIFI adapter working please?
I use Ubuntu 18.04.
kernel 4.15.0-45-generic
I copy some information from terminal
jarek@jarek-400B4C-400B5C-200B4C-200B5C:~$ dmesg | grep 8812au
[   12.899008] 8812au: version magic '4.15.0-44-generic SMP mod_unload ' should be '4.15.0-45-generic SMP mod_unload '
[   89.479716] 8812au: version magic '4.15.0-44-generic SMP mod_unload ' should be '4.15.0-45-generic SMP mod_unload '
[  115.118925] 8812au: version magic '4.15.0-44-generic SMP mod_unload ' should be '4.15.0-45-generic SMP mod_unload '
jarek@jarek-400B4C-400B5C-200B4C-200B5C:~$ sudo apt-get install rtl8812au-dkms
[sudo] password for jarek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8812au-dkms is already the newest version (4.3.8.12175.20140902+dfsg-0ubuntu8).
0 to upgrade, 0 to newly install, 0 to remove and 123 not to upgrade.
jarek@jarek-400B4C-400B5C-200B4C-200B5C:~$ lsusb
Bus 002 Device 004: ID 08ff:168a AuthenTec, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1010 Silicon Motion 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0781:5591 SanDisk Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I enjoy Ubuntu but I don't know much about commands line etc so please put some plain instruction how to get this thing work again.
I will very appreciate any help.
Thank you
I look forward to get respond from Ubuntu community.

---

### Post by jeremy31 on 2019-02-18
Ok, in terminal do
```
sudo -H gedit /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```
Replace line 4 with ```
MAKE="'make' all KVER=${kernelver}"
```
Save and exit
We can do a hack to make the current module work
```
sudo sed -i 's/4.15.0-44-generic /4.15.0-45-generic/'  /lib/modules/4.15.0-45-generic/updates/dkms/8812au.ko
```
Reboot

---

### Post by Gadget2008 on 2019-02-23
Hi,
Thank you for your reply.
I put in terminal code  

sudo -H /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf  
 and it's not working:I paste below what it's said:
,,jarek@jarek-400B4C-400B5C-200B4C-200B5C:~$ sudo -H /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
[sudo] password for jarek: 
sudo: /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf: command not found
jarek@jarek-400B4C-400B5C-200B4C-200B5C:~$ 

If you can please help me to  get this alfa  AWUS036AC USB WIFI adapter work. 

I will very appreciated your help.
Thank you
I'm looking forward to hear from you or someone else who can help.
I love linux but I don't know much about linux,commands,etc
I bought this wiifi adapter because I had another one older model Alfa and work fine under linux Ubuntu. i just plug in and work in my another laptop,
This one Alfa  AWUS036AC USB WIFI adapter stopped working any more and I don't know how to fix it.
 I hope someone help me to get this  AWUS036AC USB WIFI adapter work again.

---

### Post by jeremy31 on 2019-02-23
I fixed the code in the other post, please try again.  Let me know if the current kernel is now -46 ```
uname -a
```
If it is -46 you will need to do ```
sudo sed -i 's/4.15.0-45-generic /4.15.0-46-generic/'  /lib/modules/4.15.0-46-generic/updates/dkms/8812au.ko
``` and reboot to get it to work in the current kernel

---

