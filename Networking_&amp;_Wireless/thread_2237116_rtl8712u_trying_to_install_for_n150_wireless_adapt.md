---
title: "rtl8712u trying to install for n150 wireless adapter f9l1001"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by daniel172 on 2014-07-30
Dear Ubuntu community,

I'm using lxle, which I think is built on ubuntu. I just installed it onto the machine a couple days ago (first time!) and am trying to get the driver to use my wireless adapter on it. The wireless adapter is belkin n150, f9l1001v1, and the driver I think works for it (from forum searches) is rtl8712u. I tried using this site for guidance 

[http://ubuntuforums.org/showthread.php?t=1947015](http://ubuntuforums.org/showthread.php?t=1947015) 

but I'm stuck at the all the steps before the issue the guy in the forum was having. I found this website

[https://git.kernel.org/cgit/linux/kernel/git/gregkh/staging.git/tree/drivers/staging/rtl8712](https://git.kernel.org/cgit/linux/kernel/git/gregkh/staging.git/tree/drivers/staging/rtl8712)

which was a git containing all the files for the driver, but I do not know where to go from there. I manage to clone the repository onto a folder in my computer called 'rtl8712-driver'.
Can you help me install this driver?
I'm a first-timer who is new at linux.

---

### Post by chili555 on 2014-07-30
In recent versions of Ubuntu, the driver r8712u is built-in by default. Are you sure it isn't loaded already?```
lsmod | grep 8712
```If it is loaded, your wireless should be working. If not, load it:```
sudo modprobe r8712u
```Now show us:```
rfkill list all
iwconfig
dmesg | grep 8712
```Thanks.

---

### Post by daniel172 on 2014-07-30
It works! Worries tend to lead us all astray I guess. Just in case, here's what you wanted to see:
```
skylife@skylife-EX321AA-ABA-SR1930NX-NA630:~$ rfkill list all
skylife@skylife-EX321AA-ABA-SR1930NX-NA630:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"HANDOJO"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 30:46:9A:86:52:C7   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=86/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

skylife@skylife-EX321AA-ABA-SR1930NX-NA630:~$ dmesg | grep 8712
[12772.076515] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[12772.082631] r8712u: DriverVersion: v7_0.20100831
[12772.082674] r8712u: register rtl8712_netdev_ops to netdev_ops
[12772.082679] r8712u: USB_SPEED_HIGH with 4 endpoints
[12772.083345] r8712u: Boot from EFUSE: Autoload OK
[12772.812954] r8712u: CustomerID = 0x0000
[12772.812961] r8712u: MAC Address from efuse = b4:75:0e:1e:9d:b7
[12772.812965] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[12772.814060] usbcore: registered new interface driver r8712u
[12774.968497] r8712u: 1 RCR=0x153f00e
[12774.969245] r8712u: 2 RCR=0x553f00e


```

---

### Post by chili555 on 2014-07-30
The late timestamp on loading r8712u indicates it isn't loading on boot. Let's fix it:```
sudo -i
echo r8712u  >>  /etc/modules
exit
```You should be all set.

Please use thread tools at the top to mark Solved.

---

### Post by daniel172 on 2014-07-30
Thanks for your help!

---

