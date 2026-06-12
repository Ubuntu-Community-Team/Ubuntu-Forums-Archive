---
title: "Low reach of wifi after upgrade to 18.04 RealTek RTL8723BE controller"
date: 2018-11-03
forum: Networking &amp; Wireless
---

### Post by mr-mister on 2018-11-03
¡Hi! Did a clean install of 18.04 and i notice that a have fewer reach of wifi. When i installed 16.10 and 17.10 and had a similar issue, [this thread]("https://ubuntuforums.org/showthread.php?t=2356155") helped me. 
[https://pastebin.com/index/D9hDeQNi](https://pastebin.com/index/D9hDeQNi) any ideas?

---

### Post by jeremy31 on 2018-11-03
Do ```
sudo apt-get install dkms git build-essential
git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Reboot

---

### Post by mr-mister on 2018-11-03
Did not work. Not getting any signal were i used to... Need more info?

---

### Post by jeremy31 on 2018-11-03
Post results for ```
dmesg | grep rtl
```

---

### Post by mr-mister on 2018-11-03
[   13.981301] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[   14.289212] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.289739] rtlwifi: rtlwifi: wireless switch is on
[   14.439853] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0
[   14.540029] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   14.540032] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   14.593239] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   14.593243] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[  193.698700] rtlwifi: AP off, try to reconnect now
[  334.818592] rtlwifi: AP off, try to reconnect now

---

### Post by jeremy31 on 2018-11-03
Run the wireless script again

---

### Post by mr-mister on 2018-11-03
[https://pastebin.com/6cNDCjjG](https://pastebin.com/6cNDCjjG)

---

### Post by jeremy31 on 2018-11-03
Did you uninstall it and change the ant_sel parameter to 1?  I have used the github to make it work on my laptop with the rtl8723be chip with only one antenna connected

---

### Post by mr-mister on 2018-11-03
At some point i tried changing it to 2, but that was before i posted this thread and it did not work, should i set it back to 2?

---

### Post by jeremy31 on 2018-11-03
Yes the rtlwifi_new from github should work when installed with ant_sel=2 and rebooted

---

### Post by mr-mister on 2018-11-03
I changed it with
```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf

```
And after reboot lost all connectivity (ran it again with ant_sel=1 and got wifi again, still no signal in other rooms), should i be configuring with other commands? 
[https://pastebin.com/PrVLxqJC](https://pastebin.com/PrVLxqJC) In module parameters says ant_sel: 1 but in the .conf file is what i echoed

---

### Post by jeremy31 on 2018-11-03
Run the wifi script with the github drivers in use, just do ```
./wireless-info
```
In terminal then remove it if needed to connect then ```
cat wireless-info.txt | nc termbin.com 9999
```
Post link

---

### Post by mr-mister on 2018-11-03
[http://termbin.com/52u5](http://termbin.com/52u5)

---

### Post by jeremy31 on 2018-11-03
Those results are not using the github modules from [https://ubuntuforums.org/showthread.php?t=2405266&p=13813649#post13813649](https://ubuntuforums.org/showthread.php?t=2405266&p=13813649#post13813649) or is it using ant_sel=2

---

### Post by mr-mister on 2018-11-03
I installed those modules when you suggested it, so it should be using those modules. I did not use ant_sel=2

want me to install the github modues again?

---

### Post by jeremy31 on 2018-11-03
Post results for ```
dkms status
```
The results are showing the the kernel modules are still in use

---

### Post by mr-mister on 2018-11-03
rtlwifi-new, 0.6, 4.15.0-36-generic, x86_64: installed

---

### Post by jeremy31 on 2018-11-03
Check ```
grep [[:alnum:]] /sys/module/rtl8723be/parameters/*
```
See if it shows ant_sel:2
Then reboot and use grub menu advanced options to boot into kernel 4.15.0-36

---

### Post by mr-mister on 2018-11-03
It shows /sys/module/rtl872be/parameters/ant_sel:1 and the other parameters

Booted with that kernel, have no wifi. ifconfig shows no wifi interface.  Plug in ether to install the git modules with this kernel?

---

### Post by jeremy31 on 2018-11-03
From the 4.15.0-36 kernel do ```
dmesg | grep 8723
```
Post results best you can

---

### Post by mr-mister on 2018-11-03
[   18.412707] rtl8723_common: Unknown symbol rtl_fw_page_write (err 0)
[   18.412737] rtl8723_common: Unknown symbol rtl_fill_dummy (err 0)
[   19.833651] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   19.833654] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   19.997523] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   19.997527] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin

---

### Post by jeremy31 on 2018-11-03
OK try
```
sudo cp /var/lib/dkms/rtlwifi-new/0.6/source/rtl8723com/rtl8723_common.ko /lib/modules/4.15.0-36-generic/updates
sudo depmod -a
```
reboot into the 4.15.0-36

---

### Post by jeremy31 on 2018-11-03
I actually have a better fix, boot normally if you can connect and do
```
cd Desktop
git clone https://github.com/jeremyb31/rtlwifi_new.git
sudo dkms add rtlwifi_new
sudo dkms install rtlwifi-new/0.7
```
Reboot and this should work with ant_sel=2 as I found an issue with dkms.conf on lwfinger github site

---

### Post by mr-mister on 2018-11-03
Success! Sorry had to leave for a while. Thank you very very much for the patience.

---

### Post by jeremy31 on 2018-11-03
Great, use the thread tools menu near the top right of the page to mark as solved

I have notified lwfinger of the issue on github

---

