---
title: "Realtek RTL8723 connection problems"
date: 2018-01-23
forum: Networking &amp; Wireless
---

### Post by eli-rangel on 2018-01-23
I recently downloaded Ubuntu on my HP notebook and found out that my realtek rtl8723 network card does not have the best support. I managed to make it work on some networks, my home, my hotspot, yet it will not recognize other networks. For instance at school I cannot see any of the wifi connections, coffee shop, etc are the same so far. Now when I connect to my home network I lose connection and have very slow speeds unless I am right next to the router or I am wired in.

 I looked online and found a script to run to help diagnose which I am attaching.

```
##### kernel ############################

Linux 4.13.0-31-generic #34~16.04.1-Ubuntu SMP Fri Jan 19 17:11:01 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:81ed]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: Sanji2 
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]

```
Above is an example of the output for hardware reference, below is the attached file.
[ATTACH]278299[/ATTACH]

Any help or explanation of what could be happening would be great, thank you!

---

### Post by Hadaka on 2018-01-24
Hi, there are several issues that need attention.
First...' ssid xday [AC2] '... does this belong to you ??
#*If no..then click the wifi icon > wireless and delete it.
#*if yes..do the same but edit the connection and uncheck connect automatically
Then open a terminal ctrl/alt/t ..and please Copy and paste..
#*Turn OFF power mgmt..Power Management-on
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
#*Set IPv6 to ignore...[ipv6] method=auto
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/OnePlus3
sudo systemctl restart network-manager.service
```
#*Correct unset Country Code...country 00: DFS-UNSET
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
#*Correct the "have to be close to the router" and connection problems
```
sudo modprobe -rf rtl8723be
echo "options rtl8723be swenc=1 msi=1 fwlps=0 ips=0 ant_sel=1"  |  sudo tee /etc/modprobe.d/rtl8723be.conf
sudo modprobe -v rtl8723be
```
boot and test wireless
Thanks

---

### Post by eli-rangel on 2018-01-24
Thank you so much! I will try this tomorrow as I do not have time tonight and will post the results. I appreciate your time!

---

