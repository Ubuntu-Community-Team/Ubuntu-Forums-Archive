---
title: "Very weak wifi please help"
date: 2018-05-07
forum: Networking &amp; Wireless
---

### Post by beadgc on 2018-05-07
Hey guys. Installed Ubuntu 16.04 last night. Love it but the has very weak signal unless I'm standing in front of the router. Worked great on windows before I installed ubuntu. I have tried a bunch of things I have read and nothing has worked yet. I have a HP Pavilion lap top and in the terminal it shows this for my wireless Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter. Any help would be greatly appreciated.

Thanks in advance

---

### Post by jeremy31 on 2018-05-07
Hi, this has been an issue for a while since HP started using one antenna on a card designed for 2, in terminal do ```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be-ant.conf
```
Then reboot

Welcome to the forums!

---

### Post by beadgc on 2018-05-07
> **jeremy31 said:**
> Hi, this has been an issue for a while since HP started using one antenna on a card designed for 2, in terminal do ```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be-ant.conf
```
Then reboot

Welcome to the forums!


OMG THANK YOU! Full signal even in my basement lol.

---

