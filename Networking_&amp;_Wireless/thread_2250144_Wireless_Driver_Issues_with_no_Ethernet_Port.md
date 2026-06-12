---
title: "Wireless Driver Issues with no Ethernet Port"
date: 2014-10-27
forum: Networking &amp; Wireless
---

### Post by fr3adomsk8ter on 2014-10-27
Hello, I recently just installed Ubuntu onto my new Asus Laptop. For the last 3 days I've been trying to figure out how to install my wireless driver manually off a thumb drive. I've found the correct Intel driver specifically for my wireless card on Linux. But there is very poor documentation to show me how to install it properly. Also my laptop not having an ethernet port does not make my transition an easy one.

I don't have ndiswrapper on my machine so I can't use my Windows Driver to get it up and running. I've also attempted to manually install ndiswrapper off of a USB thumb drive but with no success.

I'm really in to computers and the new world of Linux excites me but without internet browsing capabilities it makes the journey quite difficult. Any advice on how to resolve this issue would be appreciated. Thank you.

---

### Post by Bucky Ball on 2014-10-27
*Thread moved to **Networking & Wireless**.*

Welcome. Do NOT use ndiswrapper. Last resort, can cause more confusion and largely superceded. A lot of newcomers have been bringing it up lately. There are very few cards it is used for now. Please check how old your info is.

Open a terminal and paste this in then hit enter:

```
sudo lshw -C network
```

Post the result back here, please. Also provide the release you are using and any other relevant information.

---

### Post by mike555 on 2014-10-27
They make ethernet to USB adapters, like this one;     [http://www.amazon.com/gp/product/B00484IEJS/ref=oh_aui_search_detailpage?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00484IEJS/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)   that will allow you to use ethernet through a USB port , I sometimes do this with my tablet.

---

### Post by fr3adomsk8ter on 2014-10-27
This is the Code I recieved back  


> 


  *-network UNCLAIMED      
       description: Network controller 
       product: Wireless 7260 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: cb 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:f7c00000-f7c01fff 



On my thumbdrive I have the driver for my intel wireless 7260 card. The file itself is listed as iwlwifi-7260-ucode-22.15.8.0.tgz


When I attempt to run the program it will open in the software center and show a blank page since I have no internet access.


I've attempted


>  sudo apt-get install iwlwifi-7260-ucode-22.15.8.0.tgz 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
E: Unable to locate package iwlwifi-7260-ucode-22.15.8.0.tgz 
E: Couldn't find any package by regex 'iwlwifi-7260-ucode-22.15.8.0.tgz'



But it always fails to find the correct directory.


I'm running Ubuntu 14.04.1Lts

---

### Post by chili555 on 2014-10-27
What you have there is the firmware, not the driver. Recent versions of Ubuntu include the driver and the firmware by default. Before we proceed, please tell us what version you installed:```
lsb_release -d
uname -r
```Older versions of Ubuntu don't include a newer driver that covers your relatively new device.

---

### Post by fr3adomsk8ter on 2014-10-28
After typing in the provided command this is what I got back.


> xyston@xyston-Q302LA:~$ lsb_release -d 
Description:	Ubuntu 14.04.1 LTS 
xyston@xyston-Q302LA:~$ uname -r 
3.13.0-32-generic 


Also to Mike555 I thought about buying one where I work to try to get the computer up and running through that. The USB Ethernet adapter we sell was our stores brand name so I was hesitant on spending money on a piece of hardware that might not even get recognized by the basic drivers that come with Linux. Hopefully with the help of the Ubuntu Community I can get my machine up and running and gain some knowledge more on Linux.

---

### Post by chili555 on 2014-10-28
Good news! Both the driver and associated firmware are present in 14.04. If the driver doesn't load or tries to load and fails for some reason, it will show in *lshw* as 'Unclaimed.' Let's try to load the driver and see what the logs tell us:```
sudo modprobe iwlwifi
dmesg | grep iwl
```Either the wireless will spring to life and we'll arrange for the driver to load on boot or an error message will suggest where we turn next.

---

### Post by jeremy31 on 2014-10-28
version: cb

Another one of those

---

### Post by jeremy31 on 2014-10-28
Here is chili555's fix for that card revision [http://ubuntuforums.org/showthread.php?t=2242147&p=13112184#post13112184](http://ubuntuforums.org/showthread.php?t=2242147&p=13112184#post13112184)

And it is no longer experimental as it has worked for at least 3 posters that I know of

---

