---
title: "wireless not working on new ubuntu 12.04 install"
date: 2013-10-28
forum: Networking &amp; Wireless
---

### Post by cptflo on 2013-10-28
Hi,

I have a lenovo thinpad x131 with AMD processor. Just installed 12.04 on it and despite my efforts to find drivers and other things I can't enable the wireless. Wireless option do not appear on the network manager either.

Some help would be very appreciated.

I am posting the following commands hoping to provide enough info:


  	 	 	 	  ```
 **rfkill list  **

 

 0: tpacpi_bluetooth_sw: Bluetooth  

 	Soft blocked: no  
 	Hard blocked: no  
 1: hci0: Bluetooth  
 	Soft blocked: no  
 	Hard blocked: no  
 

 

 

 

 **iwconfig  **

 

 eth0      no wireless extensions.  
 

 lo        no wireless extensions.  
 

 

 

 

 **sudo lshw -C network**

 

 *-network                

        description: Network controller  
        product: BCM43228 802.11a/b/g/n  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        version: 00  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: driver=bcma-pci-bridge latency=0  
        resources: irq:17 memory:f0a00000-f0a03fff  
   *-network  
        description: Ethernet interface  
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth0  
        version: 07  
        serial: 08:9e:01:33:1c:d2  
        size: 10Mbit/s  
 

 

 

 

 **nm-tool  **

 

 NetworkManager Tool  
 

 State: disconnected  
 

 - Device: eth0 -----------------------------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             unavailable  
   Default:           no  
   HW Address:        08:9E:01:33:1C:D2  
 

   Capabilities:  
     Carrier Detect:  yes  
 

   Wired Properties  
     Carrier:         off  
```



Thank you for looking into it!

---

### Post by Hadaka on 2013-10-28
Hi,please post the output of..
```
lspci -nn | grep 0280
```
thanks.

---

### Post by cptflo on 2013-10-28
Thank you for your reply.

  	 	 	 	   The 0280 in the following reading is highlighted in red.

 

 **lspci -nn | grep 0280  **

02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]

---

### Post by Hadaka on 2013-10-28
Hi,please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by cptflo on 2013-10-29
Thanks!

The only thing is that I only have a wifi. I am using my old computer to go online (it's running an older version of ubuntu). I don't have a wired connection.
I was hoping to download the required update packages with the old computer, then tranfer them over to the new computer with a USB stick and install them from there. I did try to download the drivers from realtek.com but no luck. I just don't know how to do it!

I'll have to go find a wired connection somewhere, unless there is another relatively easy way to get the right updates using the older lap top and transfer them over?

Thanks!

---

### Post by Hadaka on 2013-10-29
Hi,please click --SystemSettings..Hardware/additional drivers.
that sta driver "may" work.meantime, i am in search of a zipped
broadcom-kernel-source file to attach.
thanks.

---

### Post by Hadaka on 2013-10-29
Hi, if you can somehow aquire a wired connection.
then do..
```
sudo apt-get install linux-headers-generic linux-headers-`uname -r`
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by cptflo on 2013-10-29
> **Hadaka said:**
> Hi,please click --SystemSettings..Hardware/additional drivers.
that sta driver "may" work.meantime, i am in search of a zipped
broadcom-kernel-source file to attach.
thanks.

It says: "no proprietary drivers aare in use in this system"

thanks

---

### Post by cptflo on 2013-10-29
> **Hadaka said:**
> Hi, if you can somehow aquire a wired connection.
then do..
```
sudo apt-get install linux-headers-generic linux-headers-`uname -r`
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

I'm going to check the library for a wired connection,

Thank you

---

### Post by wildmanne39 on 2013-10-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by cptflo on 2013-11-09
Hi!

I finally made my way to a wired connection. tried to download/activate the STA driver and my computer screen went crazy. Had to power down depressing the power switch.
I then restarted and did ```

sudo apt-get install linux-headers-generic linux-headers-`uname -r`
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

the end result is quite good really with a wireless that is working :D  ... So thank you very much for your help!

The only thing is that the STA driver is activated as well. If I deactivate it then wireless is gone again.

Am I running the STA driver or the open source driver?
I read that it is best to run the open source on there

[https://wiki.archlinux.org/index.php/Broadcom_wireless](https://wiki.archlinux.org/index.php/Broadcom_wireless)

Should I look further into this? Perhaps go back to a wired connection, deactivate the sta driver, re-do the code you recommanded above and see what I get?

Thanks a bunch.

---

### Post by cptflo on 2013-11-18
After one week of usage on the STA driver, the wireless is working fine.
Unfortunately, the keyboard, touchpad and left/right clic switches stop functioning randomly (unresponsive).
I was wondering if it could be related to the STA driver or if there are 2 unrelated problems.

Thank you.

Correction: it actually is the entire computer that randomly becomes unresponsive. also, Sometimes the switches from the touch pad do not work (while the touch pad works fine) and I have to reboot to get them to work. It looks like this brand new install just isn't going well. I'm wondering if it is related somehow to the wireless issues I had before or what's possibly going on.

Any advice leading me in the right direction to solve these various issues is appreciated.

---

