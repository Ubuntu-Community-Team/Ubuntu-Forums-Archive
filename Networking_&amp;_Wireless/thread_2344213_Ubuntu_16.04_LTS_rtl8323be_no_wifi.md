---
title: "Ubuntu 16.04 LTS rtl8323be no wifi"
date: 2016-11-23
forum: Networking &amp; Wireless
---

### Post by kobragae on 2016-11-23
Hi guys,
I'm trying to get wifi working, I tried everything I found on the web, I installed the rtlwifi_new driver but nothing happens: card is seen by ubuntu, module is loaded in the kernel, but no wifi networks are found.
```
$ lspci | grep -i wire
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
```
All modules are loaded
```
$ lsmod | grep rtl
rtl8723be              94208  0
btcoexist             180224  1 rtl8723be
rtl_pci                28672  1 rtl8723be
btrtl                  16384  1 btusb
rtlwifi                77824  3 btcoexist,rtl_pci,rtl8723be
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              565248  2 mac80211,rtlwifi
```
I modified the /etc/modprobe.d/rtl8723be.conf
```
$ cat /etc/modprobe.d/rtl8723be.conf 
options rtl8723be ant_sel=2
```

here is the ifconfig output
```
wlo1      Link encap:Ethernet  IndirizzoHW xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
```
and iwscan doesn't see any network
```
$ sudo iwlist wlo1 scan
wlo1      No scan results
```

Can you help please?

---

### Post by kobragae on 2016-11-23
after a few tries I found the solution, hope it helps someone: on my hp probook g55 module params to get wifi working are:
```
msi=1 ips=0
```
every other setting I tried failed

---

### Post by ratcheer on 2017-03-16
Thank you. I just got an HP Probook 450 and I'm having a similar problem. I will try your settings...  Tim

---

### Post by jeremy31 on 2017-03-16
If you have an HP with the RTL8723BE chipset open a terminal window and enter
```
iwlist scan | egrep -i 'ssid|quality'
```

That will show the Access Points and the reception, then we will unload the module and try the first parameter option
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=1
```
```
iwlist scan | egrep -i 'ssid|quality'
```

The results from the scan may be the same as original or better but we will check the last option for ant_sel

```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=2
```
```
iwlist scan | egrep -i 'ssid|quality'
```

If ant_sel=1 was the best then do
```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf
```

If ant_sel=2 was the better option
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf
```

---

