---
title: "Ideapad 310, WIFI and Blue-tooth not working"
date: 2017-09-24
forum: Networking &amp; Wireless
---

### Post by bobsone on 2017-09-24
Hi
I have installed Ubuntu Mate (16.4) alongside Win10 on a Lenovo Ideapad 310.
Since the install I have had an issue with my WIFI randomly dropping out and (mostly) not restarting until the notebook is rebooted.  Unfortunately since I have also been attempting to resolve a malfunctioning Blue-tooth problem I have now completely broken the WIFI.

 Connecting via cable takes a while to connect but is reliable and the WIFI works correctly in Win10. The Notebook WIFI card is listed as a Realtek RTL8821AE and (in Mate and Win10) it is connected to the 802.11ac network of a Netgear R2650ac router.
 I have worked through the  instructions in the sticky “Before posting in Network & Wireless”; *sudo apt update* and * sudo apt dist-upgrade* didn’t help. The *"wireless-info.txt"* is at [B][http://paste.ubuntu.com/25606108/](http://paste.ubuntu.com/25606108/)

[/B]If needed, the output from *lspci -nnk | grep -iA2 net* is```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:384c]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
    Kernel modules: rtl8821ae
```

Regards

---

### Post by jeremy31 on 2017-09-24
Welcome to the forums

Why are you loading the Ralink rt2800pci module using /etc/modules as your wifi card needs rtl8821ae and it seems that you have manually unloaded or removed that module

---

### Post by bobsone on 2017-09-25
Thanks for the reply.
This is embarrassing, not sure exactly when that happened.
So now how to fix it?  Bearing in mind my attempts were prompted by intermittent (and now broken) WIFI and a dysfunctional Blue-tooth, what is a good start point to attempt a solution?
 
I have made an attempt at a solution (but haven&#8217;t tried it yet).

[I]sudo apt-get install linux-headers-generic build-essential git 
git clone [https://github.com/lwfinger/rtlwifi_new/tree/master/rtl8821ae](https://github.com/lwfinger/rtlwifi_new/tree/master/rtl8821ae)
cd rtl8821AE_new [/I][I]
sudo make install 
[/I]
 
Regards.

---

### Post by jeremy31 on 2017-09-25
I actually think you have to
```
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
```
To make it work but it you want it to automatically update for new kernels, do the following instead
```
sudo apt-get install dkms
[code]git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

---

### Post by bobsone on 2017-09-26
Thanks for the help,
I tried the solution in post #4, unfortunately it didn’t work; still no WIFI. 
Is it possible I need to remove existing wifi drivers, the command *[FONT=arial]```
[/FONT]**[FONT=arial]git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)[/FONT]**[FONT=arial]
```[/FONT]*   returned the following message; fatal: destination path 'rtlwifi_new' already exists and is not an empty directory.
Also, I reran the wireless info script from the sticky and I see that Ralink rt2800pci is still in place.

---

### Post by jeremy31 on 2017-09-26
You should be able to get the rt2800pci out with
```
sudo sed -i 's/rt2800pci/#rt2800pci/' /etc/modules
```
Reboot and see if ```
sudo modprobe -v rtl8821ae
```
gets the wifi going again

---

### Post by bobsone on 2017-09-26
Some success, rt2800pci appears to be gone.
Unfortunately still no rtl8821ae the code
```
sudo modprobe -v rtl8821ae
``` 
returns the following; 
*insmod /lib/modules/4.10.0-35-*[I]generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8821ae': Exec format error[/I]

---

### Post by jeremy31 on 2017-09-26
Somehow the module was built against the wrong kernel, so try ```
cd rtlwifi-new
sudo make uninstall
make clean
make
sudo make install
```
Reboot

---

### Post by bobsone on 2017-09-26
That has fixed it.
A big thank you to Jeremy31 for fixing my error(s), I would have been stuck without your input.

Regards, Bob

---

### Post by betouar-hamza-89 on 2017-10-18
Thank you, it's work for me

---

