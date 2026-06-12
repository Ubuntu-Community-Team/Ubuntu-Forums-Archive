---
title: "Ubuntu 14.04 wi-fi stopped again"
date: 2017-03-10
forum: Networking &amp; Wireless
---

### Post by pavel27 on 2017-03-10
Hi, everybody! Suddenly wi-fi stopped on my laptop. One year ago I had this problem and posted it [https://ubuntuforums.org/showthread.php?t=2297019&p=13366468#post13366468](https://ubuntuforums.org/showthread.php?t=2297019&p=13366468#post13366468) Later I found another way to solve this problem - reboot to Windows (I have both OS). Now wi-fi works in Windows, but finally stopped to work in Ubuntu. So I obviously need to know how to solve this problem. Any idea? :confused:

---

### Post by kc1di on 2017-03-11
Start by giving us some more information. 
can you connect via Ethernet cable?  If so please install the following in a terminal ```
sudo apt-get install inxi
```
when that is finished run the command ```
inxi -Fxz
``` and copy and past the output here.

This page may also be of help in trouble shooting your problem. [https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html")

Also run the wireless script found in my signature and post the output.

---

### Post by pavel27 on 2017-03-11
I can't connect via Ethernet. I've tried wireles script you recommended but it seems that script doesn't work on my laptop (HP Compaq). Here is the output
```
########## wireless info START ##########

```
Also I checked if my adapter was recognized
**sudo lshw -C network**


```
*-network DISABLED
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros

```
and **lspci**


```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```
And like I did early I typed 
**iwconfig**


```
eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

Do you find this information useful?](*,)

---

### Post by kc1di on 2017-03-11
Ok the script runs on all models - but it may not run because there no internet.

would you go to the terminal and copy and paste the output of ```
rfkill list
```

---

### Post by pavel27 on 2017-03-11
Yes, sure 
[B]rfkill list
[/B]```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by kc1di on 2017-03-11
Let try this one ```
lsmod | grep -e ath9k
```

---

### Post by pavel27 on 2017-03-11
```
pavel@pavel-laptop-PC:~$ lsmod | grep -e ath9k
ath9k                 141379  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              660855  1 ath9k
cfg80211              506619  4 ath,ath9k_common,ath9k,mac80211

```
And ath9 is red everywhere in this output, if it's important

---

### Post by kc1di on 2017-03-12
That all looks good, Give me some more info on you computer - type , model, cpu ram gpu etc.

---

### Post by pavel27 on 2017-03-12
My OS is Ubuntu 14.04, Kernel Linux 3.16.0-77-generic, MATE 1.8.2. Here is some probably interesting from output [B]lshw
[/B]```
pavel-laptop-pc           
    description: Notebook
    product: Presario CQ57 Notebook PC (A7R67EA#ACB)
    vendor: Hewlett-Packard
    version: 0690120000204910000600100
    
    width: 64 bits


*-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU B815 @ 1.60GHz
          vendor: Intel Corp.

```
Also I'm worried about this part of output:
```
 *-network DISABLED
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
 *-network DISABLED
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

```
It seems that I need to turn on it, but I've no idea how.

---

### Post by kc1di on 2017-03-12
does the light on the keyboard wireless key shine amber or blue?

---

### Post by pavel27 on 2017-03-13
The light changes the color when I press the wireless key like everything is OK. But except it nothing changes.

---

