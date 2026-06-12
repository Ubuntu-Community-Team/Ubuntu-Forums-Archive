---
title: "Wifi speed inconsistent and slow to very slow"
date: 2016-09-12
forum: Networking &amp; Wireless
---

### Post by womanlysteel on 2016-09-12
I'm running 16.04.1 on a Lenovo ideapad 300, with Intel Dual Band Wireless-AC 3165 Plus Bluetooth. Brand new laptop, deleted windows 10 and installed ubuntu. Everything went fine with the install as far as I can tell, installed 15.10 and upgraded.

Problem is the wifi is inconsistent and slow. like <10 kbps to 80 kbps max, when I'm getting 1-5 Mbps from the laptop sitting next to me on the table. I have good signal strength, just no speed.

I've updated, rebooted, tried turning power management off and turning off IPv6, which helped some but not enough. When I search I find that a lot of people had this problem with 14.4, but not more recently. 

Here are snippets from my wireless-info file. Sorry if I forgot to include something important.

```

##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3837]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Intel Corporation Intel Dual Band Wireless-AC 3165 Plus Bluetooth [8086:3166] (rev 99)
    Subsystem: Intel Corporation Intel Dual Band Wireless-AC 3165 Plus Bluetooth [8086:4210]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 174f:1158 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```
```

##### lsmod #############################


iwlmvm                311296  1
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1468119 (1.4 MB)  TX bytes:598756 (598.7 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"TP-LINK_AEBC24"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'TP-LINK_AEBC24' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0

```

---

### Post by wildmanne39 on 2016-09-12
Everything in that file is important please post the whole file.
Thanks

---

### Post by womanlysteel on 2016-09-13
> **Wild Man said:**
> Everything in that file is important please post the whole file.
Thanks

The file was too large to upload as a single file, so I've divided it into two. Sorry about that.

---

### Post by wildmanne39 on 2016-09-13
There is errors with the driver we will install the backported driver and see if that helps if not we may have to install a new kernel.

Download the latest backport driver, all commands copy and paste for accuracy on line at a time and watch for errors.
```
https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
``` 
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Now we will compile the driver:
```
tar xvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-iwlwifi
make
sudo make install
```
Every time there is a kernel upgrade you will have to reinstall the driver by doing the following:
```
cd backports-4.4.2-1
sudo su
make clean
make defconfig-iwlwifi
make install
exit
```

---

### Post by womanlysteel on 2016-09-14
I appreciate you taking the time to help me with this. 

Ran your code using copy/paste, in the correct order, didn't see any errors thrown, but it doesn't seem to have helped. After reboot, I'm still getting 50  kbps while my old laptop is getting 12 Mbps in the same area.

---

### Post by wildmanne39 on 2016-09-14
Please run the wireless script again and post the results here so we can see if the new driver took care of the errors in dmesg.
Thanks

---

### Post by womanlysteel on 2016-09-15
> **Wild Man said:**
> Please run the wireless script again and post the results here so we can see if the new driver took care of the errors in dmesg.
Thanks

Here you go. I had to divide it again at the "module" portion, this file was even longer than the first.

---

### Post by wildmanne39 on 2016-09-15
Please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlmvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
does that help? and there are still errors in dmesg we may have to change kernels to try to fix it.

---

### Post by womanlysteel on 2016-09-16
> **Wild Man said:**
> Please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
does that help? and there are still errors in dmesg we may have to change kernels to try to fix it.

The ```
 sudo modprobe -rfv iwlwifi 
``` doesn't work for me. I get ```
 modprobe: FATAL: Module iwlwifi is in use. 
```If I do 
```
lsmod | grep iwlwifi
iwlwifi               200704  1 iwlmvm
cfg80211              561152  3 iwlwifi,mac80211,iwlmvm
compat                 16384  4 cfg80211,iwlwifi,mac80211,iwlmvm

```

Can I force its removal while in use, or terminate it and then remove it?

---

### Post by womanlysteel on 2016-09-16
> **Wild Man said:**
> Please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
does that help? and there are still errors in dmesg we may have to change kernels to try to fix it.

The ```
 sudo modprobe -rfv iwlwifi 
``` doesn't work for me. I get ```
 modprobe: FATAL: Module iwlwifi is in use. 
```If I do 
```
lsmod | grep iwlwifi
iwlwifi               200704  1 iwlmvm
cfg80211              561152  3 iwlwifi,mac80211,iwlmvm
compat                 16384  4 cfg80211,iwlwifi,mac80211,iwlmvm

```

Can I force its removal while in use, or terminate it and then remove it?

---

### Post by wildmanne39 on 2016-09-16
I edited the code, please run it again.
Thanks

---

### Post by womanlysteel on 2016-09-17
> **Wild Man said:**
> I edited the code, please run it again.
Thanks
That solved it. Thanks for your help!

---

### Post by wildmanne39 on 2016-09-17
Your welcome!
Enjoy!

---

