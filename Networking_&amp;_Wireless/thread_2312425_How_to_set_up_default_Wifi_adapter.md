---
title: "How to set up default Wifi adapter"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by candear on 2016-02-04
Hello, 

My laptop's original wifi card has some issues when downloading over a few hundred MB, it gets stuck.
I bought a USB TP link adapter that I manage, following this page , to install it :  

[http://brilliantlyeasy.com/ubuntu-linux-tl-wn725n-tp-link-version-2-wifi-driver-install/](http://brilliantlyeasy.com/ubuntu-linux-tl-wn725n-tp-link-version-2-wifi-driver-install/)

Running Ubuntu Mate 15.10

Everything works fine until I reboot the computer, USB card is not working , and the original card takes charge and connects to the Wifi.
So I have to go and pass this command each time I reboot the computer:

```
sudo [COLOR=#000000][FONT=Consolas]insmod 8188eu.ko[/FONT][/COLOR]
```

Is there any way to set up the USB adapter as default ? 

Thanks for your help

---

### Post by howefield on 2016-02-04
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by Hadaka on 2016-02-04
Hi, please allow the computer to boot to the internal wifi card
then copy and paste..
```
lspci -nnk | grep -iA2 net
```
post the output
thanks.

---

### Post by candear on 2016-02-04
Hi, 
Thanks for the reply here's the output :

03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Lenovo Device [17aa:3956]
    Kernel driver in use: atl1c
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: bcma-pci-bridge

---

### Post by Hadaka on 2016-02-04
Hi please open a terminal then copy and paste one line at a time..
```
echo -e "blacklist brcmsmac\nblacklist bcma" | sudo tee -a  /etc/modprobe.d/blacklist.conf
echo rt8188eu | sudo tee -a /etc/modules
```
Insert your usb module and boot
thanks.

---

### Post by candear on 2016-02-04
Auch :( 

After using the commands you shared, during booting , following text appears :

[          7.650388] systemd[1]: Failed to start Load Kernel Modules.
[FAILED] Failed to start Load Kernel Modules.
See 'systemctl status systemd-modules-load service' for details.


After witch computer boots but no more Wifi , none of the two available no wifi network, 
only cable connection works .

Any ideas ?

---

### Post by Hadaka on 2016-02-04
The commands i gave you blacklisted the driver modules for the internal wifi card
and then inserted the usb wifi driver to be loaded at boot. Let's undo those commands
then see if it starts like it did before. please copy and paste.
```
sudo sed -i '/^rt8188eu/ d' /etc/modules
sudo sed -i '/^bcma/ d' /etc/modprobe.d/blacklist.conf
sudo sed -i '/^brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```
boot and then test your usb the way you were doing it.
thanks.

---

### Post by candear on 2016-02-04
I used the last commands you shared, no more error when booting , but no wifi after booting 
i try the command as before  try to get the USB wifi alive doesn't want to 

sudo [COLOR=#000000][FONT=Consolas]insmod 8188eu.ko[/FONT][/COLOR]

any idea how to get the wifi back to work ?

thanks  

[COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by Hadaka on 2016-02-04
Hi, try this..
```
sudo modprobe -rf rtl8188eu
```
then post the output of..
```
cat /etc/modules
```
thanks

---

### Post by candear on 2016-02-04
Hi, 

for the first command, result is :

modprobe: FATAL: Module rtl8188eu not found.


the output of the second command is :

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


maybe I should try to reinstall  the USB one, can I make it worst doing that ? 
thanks

---

### Post by Hadaka on 2016-02-04
hi,blacklisting the internal card modules and inserting
the usb module should not have created a problem, it is now
back exactly as it was an still not working. I would suggest powering
down your computer and the router,especially the router. Test after you
power back up.If it still fails, reloading the usb driver shouldnt cause any
harm.
keep us posted
thanks.

---

### Post by candear on 2016-02-05
Well in the end I reinstall the USB wifi , 
rebooted the comp, and it looks like it is starting automatically for now. 
We will see how it will be after the next update.

As for the internal wifi card, it is not visible . maybe we will stay with this solution 


Thanks for the help. 
Nice day

---

### Post by candear on 2016-02-07
Hi, 

I have to get back to this topic, not sure which are the rules for "SOLVED" topics  

I just realize I cannot see Bluetooth either. 
Trying to follow the official doc, I am unable to install it , not sure if I am doing something wrong 
or it is because of our early interactions. 

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Is there any way we could put the computer back the way it was before we started working on it ? 

Thanks

---

### Post by Hadaka on 2016-02-07
Hi, what we did had nothing to do with bluetooth.
please post the output of..
```
cat /etc/modules
cat /etc/modprobe.d/blacklist.conf
```
thanks.

---

