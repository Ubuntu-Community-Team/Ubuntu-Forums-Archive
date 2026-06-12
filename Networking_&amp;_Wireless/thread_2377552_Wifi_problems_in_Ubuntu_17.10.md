---
title: "Wifi problems in Ubuntu 17.10"
date: 2017-11-14
forum: Networking &amp; Wireless
---

### Post by newspire2 on 2017-11-14
I installed Ubuntu 17.10 on an Acer E 15 15-575 laptop. I have been  experiencing multiple problems with networking and wifi. These problems  include:
  
[LIST]
[*]Not able to access captive portals 
[*]Not able to turn off wifi 
[*]Not able to change networks 
[*]It stops seeing networks it isn't connected to 
[*]Network Manager freezes, and I'm unable to access Settings 
[/LIST]
  I ran ```
lspci -knn | grep Net -A3
``` and got the following output:
  02:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)     
Subsystem: Lite-On Communications Inc QCA9377 802.11ac Wireless Network Adapter [11ad:08a6] 
    Kernel driver in use: ath10k_pci     
Kernel modules: ath10k_pci 03:00.0 
Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader [10ec:5287] (rev 01)

  I ran ```
sudo lshw -class network
``` and the output for my wireless card is the following:
  
*-network
       description: Wireless interface        product: QCA9377 802.11ac 
Wireless Network Adapter        vendor: Qualcomm Atheros 
       physical id: 0        bus info: pci@0000:02:00.0 
       logical name: wlp2s0        
version: 31        
serial: 64:6e:69:ba:ec:71
       width: 64 bits        
clock: 33MHz        
capabilities: pm msi pciexpress bus_master cap_list ethernet physical 
wireless        configuration: broadcast=yes driver=ath10k_pci driverversion=4.13.0-16-generic firmware=WLAN.TF.1.0-00267-1 ip=192.168.43.173 latency=0 link=yes multicast=yes wireless=IEEE 802.11 
       resources: irq:131 
memory:b1000000-b11fffff

  I have checked for driver updates through Software & Updates, but  there weren't any updates available. Secure boot has been turned off.

---

### Post by jeremy31 on 2017-11-14
Moved to networking
See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520#post13614520)
See if that helps you, if not see the wireless script link in my signature and post results

---

