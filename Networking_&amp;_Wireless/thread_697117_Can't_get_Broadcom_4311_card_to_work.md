---
title: "Can't get Broadcom 4311 card to work"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by oli_ on 2008-02-14
My card:
```
oli@Oli-Notebook:~$ sudo lspci | grep wlan
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

```

here is what i've done until now:
I installed the package bcm43xx-firmware, loaded the kernel module:
sudo modprobe bcm43xx
and checked iwconfig:
```
oli@Oli-Notebook:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
looks fine for me, so i put the interface up
sudo ifconfig eth1 up
and tried to scan for ap's
```
oli@Oli-Notebook:~$ sudo iwlist eth1 scan
eth1      No scan results
```
hmm, my router is configured properly (essid is broadcasted), works fine with windows. But i can't find ap's at all with gutsy. as expected, wicd can't find the ap either (shocker)

whats wrong? :|

---

### Post by oli_ on 2008-02-14
uh, I just found this article:
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)
works now with that. very nice :)

---

