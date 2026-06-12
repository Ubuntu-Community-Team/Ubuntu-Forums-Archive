---
title: "wifi network not deteced on Ubuntu16.04.2lts, NIC card: realtek rtl8723be"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by ishanbhatt on 2017-03-05
Recently installed  ubuntu 16.04.2 LTS
but after installation no WiFi networks are detected.
[SIZE=4][B]
iwconfig:[/B][/SIZE]
lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
enp0s20f0u1  no wireless extensions.

eno1      no wireless extensions.

[SIZE=4]**lspci | grep -i net**[/SIZE]
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 0a)


I have attached the file that was created by using pastebin and running the script in "sticky thread".


**The link created in terminal:**
[http://paste.ubuntu.com/24118283/](http://paste.ubuntu.com/24118283/)

Need help
*Thanks in anticipation.*

---

### Post by jeremy31 on 2017-03-05
Let's see if changing the ant_sel parameter makes an improvement
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

### Post by ishanbhatt on 2017-03-05
Yes. 1 was better.
2 did not work at all.
after checking both when i did:
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf

it still didn't work.
Hence, I did

sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'

echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf

again. 
This worked.
Would love to know a bit more about what caused the problem.

Thanks!!

---

### Post by jeremy31 on 2017-03-06
HP started using wifi cards with only one antenna and for now this is how we set what antenna is used as the cards have 2 antenna connectors

---

