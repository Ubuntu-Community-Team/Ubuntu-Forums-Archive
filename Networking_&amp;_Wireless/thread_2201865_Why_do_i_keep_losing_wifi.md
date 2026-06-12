---
title: "Why do i keep losing wifi??"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by bryan13 on 2014-01-26
I just installed Ubuntu 13.01 after getting sick of windows. I am really enjoying the linux experience but ive been having problems with losing my wifi connection. It seems to just disconnect at random but usually while trying to download somthing from the Ubuntu software center. When it happens the wifi icon goes blank and disapears from the available networks. When i go to system settings/network/wireless it says my wifi is not in range??. When i restart my computer its fine until it happens again. I never had connection problems when i had win8 installed so im assuming its some driver-ubuntu complication. Anybody know what might be going on?

---

### Post by Bucky Ball on 2014-01-26
Could you open a terminal and post the output of these two commands, please:
```

sudo lshw -C network
iwconfig
```

---

### Post by bryan13 on 2014-01-26
> **Bucky Ball said:**
> Could you open a terminal and post the output of these two commands, please:
```

sudo lshw -C network
iwconfig
```

                        Ok, heres the output you requested. 

**This is while the network connection is working:**

bryan@BRYANS-NOTEBOOK:~$ sudo lshw -c network
[sudo] password for bryan: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 84:34:97:93:28:0b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: a4:17:31:93:5a:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.11.0-12-generic firmware=0.37 ip=192.168.0.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:f0210000-f021ffff
bryan@BRYANS-NOTEBOOK:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DWG855D1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:D1:B5:BD:D6   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:75   Missed beacon:0

bryan@BRYANS-NOTEBOOK:~$

---

### Post by bryan13 on 2014-01-26
> **Bucky Ball said:**
> Could you open a terminal and post the output of these two commands, please:
```

sudo lshw -C network
iwconfig
```


**This is after i lose my network connection:**

bryan@BRYANS-NOTEBOOK:~$ sudo lashw -c network
[sudo] password for bryan: 
sudo: lashw: command not found
bryan@BRYANS-NOTEBOOK:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 84:34:97:93:28:0b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: a4:17:31:93:5a:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci  driverversion=3.11.0-12-generic firmware=0.37 latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:f0210000-f021ffff
bryan@BRYANS-NOTEBOOK:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          
bryan@BRYANS-NOTEBOOK:~$

---

### Post by Bucky Ball on 2014-01-26
Apparently this works:

[http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

This is your card:

product: RT3290 Wireless 802.11n 1T/1R PCIe

The fix might look complicated at first glance, but take it slow and careful and it won't take long. Hopefully then you'll never need to do it again. ;)

PS: This:

wlan0 IEEE 802.11bgn ESSIDff/any 

... from iwconfig show you are not currently connected to any access point.

---

### Post by bryan13 on 2014-01-26
> **Bucky Ball said:**
> Apparently this works:

[http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

This is your card:

product: RT3290 Wireless 802.11n 1T/1R PCIe

The fix might look complicated at first glance, but take it slow and careful and it won't take long. Hopefully then you'll never need to do it again. ;)

PS: This:

wlan0 IEEE 802.11bgn ESSIDff/any 

... from iwconfig show you are not currently connected to any access point.


Hey, BuckyBall thanks for helping me. I tried following the step-by-step instructions you linked for me but i keep on running into this "ERROR 2". I even googled my problem and found an alternate site that has similar instructions for installing the driver but I get the same error at the same step. As soon as i get to the step where i enter "sudo make install" i get the error. 

**This is site i found, i followed the "Official Site Guide"**
[http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

**Here's the error i get:**

bryan@BRYANS-NOTEBOOK:~/Downloads/DPO_RT3290_LinuxSTA_V2600_20120508$ sudo make install
make -C /home/bryan/Downloads/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux -f Makefile.6 install
mkdir: cannot create directory ‘/etc/Wireless’: File exists
make[1]: Entering directory `/home/bryan/Downloads/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/bryan/Downloads/DPO_RT3290_LinuxSTA_V2600_20120508/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3290sta.ko /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/
install: cannot stat ‘rt3290sta.ko’: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/bryan/Downloads/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux'
make: *** [install] Error 2
bryan@BRYANS-NOTEBOOK:~/Downloads/DPO_RT3290_LinuxSTA_V2600_20120508$

---

### Post by Bucky Ball on 2014-01-26
Hmm. Try 'sudo su' (which will make you root permanently so type 'exit' as soon as you've completed the commands), then

make
make install

Just a stab but that has worked for me.

---

### Post by bryan13 on 2014-01-27
> **Bucky Ball said:**
> Hmm. Try 'sudo su' (which will make you root permanently so type 'exit' as soon as you've completed the commands), then

make
make install

Just a stab but that has worked for me.

Thanks Bucky!!. Its wierd, even thought i didnt complete all the steps in either tutorial my wifi is working perfectly now???. I guess getting far as i did was enough to jump start my network card??. Thanks for your help. I am really enjoying this OS!!.

---

### Post by Sean_Vigent on 2014-01-27
Nevermind. Good thing you enjoy Ubuntu! :P

---

### Post by Bucky Ball on 2014-01-27
Great news! If it holds up for 24 hours or so, to help others please mark the thread as solved by following the instructions in my signature. 

Enjoy the forums, the learning curve and the OS! ;)

---

