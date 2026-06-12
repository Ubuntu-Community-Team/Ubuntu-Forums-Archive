---
title: "WiFi is too slow on HP laptop on 18.04."
date: 2018-08-25
forum: Networking &amp; Wireless
---

### Post by arpi732 on 2018-08-25
I used to get proper speeds on my laptop until suddenly it became very slow after booting up today.
After my fresh installation I had run this command:
sudo tee /etc/modprobe.d/rtl8723be.conf <<< "options rtl8723be ant_sel=2" 
and then wifi worked well, I now get slower very slow speeds on rtl8723be ant_sel=2 and somewhat usable speeds for rtl8723be ant_sel=1
here is my output for
lspci -knn | grep Net -A3 08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723] Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c] Kernel driver in use: rtl8723be Kernel modules: rtl8723be 09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)


Rolling back to the 4.15.0-32 kernel didn't work and I couldn't boot into 4.15.0-30 kernel.

Secure boot is turned off.

---

### Post by arpi732 on 2018-08-26
I "solved" it by installing manjaro and then rolling up to the new 4.18 kernel. This is a kernel bug and I guess everyone with rtl8723 will be affected.

---

