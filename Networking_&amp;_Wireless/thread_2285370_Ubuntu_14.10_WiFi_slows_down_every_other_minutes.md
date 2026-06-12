---
title: "Ubuntu 14.10 WiFi slows down every other minutes"
date: 2015-07-05
forum: Networking &amp; Wireless
---

### Post by norbertk237 on 2015-07-05
Hi,

I have had a problem with WiFi network in Ubuntu for a very long time and now that I have started using my laptop for work as well, it became a bigger issue that I cannot neglect any longer. When I connect to a wireless network the internet connection stops working after a couple of minutes. I thought that the connection went down completely, so my solution was to restart the network-manager which always solved the problem (for about a minute). 

I went through the WiFi troubleshooting guidelines of Ubuntu but I haven't found anything there that would cause this issue. My card is recognised, there is only one driver installed to my card. My card's driver uses other drivers as well, but I don't think that could be the problem. This is what I get when I list the driver modules related to my wlan0 driver:
```

norbert@norbert-pc:~$ sudo lsmod | grep rtl8192ce
rtl8192ce              53509  0 
rtl_pci                26674  1 rtl8192ce
rtlwifi                64237  2 rtl_pci,rtl8192ce
rtl8192c_common        53170  1 rtl8192ce
mac80211              660651  3 rtl_pci,rtlwifi,rtl8192ce

```

I changed the encryption from WPA & WPA2 to WPA only in router that didn't change anything either. Running iwconfig showed that I have encryption key: off, so I tried to set some encryption key. I'm not sure what I should have set it to, so I just copied from one of the pages from Ubuntu's description. I have this now:
```

norbert@norbert-pc:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"BTHub3-P7ZT"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:AC:54:CC:37:62   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:FEFE-FEFE-FE
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42   Missed beacon:0

```

I just realised today that the connection is not down actually. When I try to open a new webpage in Chrome when the internet seems to have stopped, I see at the bottom either "Connecting" or "Resolving host". Previously, after about 20 seconds, I restarted the network-manager reload the page and everything worked fine. I have waited more now and what I've seen is that sometimes the page is loaded but it takes more than 20 seconds. Other times, it just times out or simply says that there's no connection. Chrome now tries to reload the page when it notices that there is a connection and it happens sometimes after a couple of seconds of displaying no connection without me doing anything. 

This is really frustrating issue and it is definitely related to Ubuntu because the other laptop doesn't have any problem running Windows 8 and when I previously had Windows 7 running on this laptop it also worked fine. I would rather keep Ubuntu running on this one and actually I was planning to install Ubuntu on the other laptop as well but if I can't figure out this issue I have to install Windows on this laptop as well.

Do you guys have any idea how to solve this issue?

Thanks,
Norbert

---

### Post by praseodym on 2015-07-05
Try these module parameters

```
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot.

---

### Post by norbertk237 on 2015-07-05
What do these parameters mean? I've tried them and they changed the behaviour a bit. I now get "disconnected" every 30-60 seconds (more frequent) but it resolves quicker, around 5-10 seconds and the connection comes back, if it does at all of course, it still has this thing that sometimes it just doesn't come back and I have to restart network-manager to get online again.

---

### Post by praseodym on 2015-07-05
Check

modinfo rtl8192ce

---

### Post by norbertk237 on 2015-07-05
swlps is still 1. 

```
norbert@norbert-pc:~$ cat /etc/modprobe.d/rtl8192ce.conf 
options rtl8192ce swlps=0 ips=0
```

```
norbert@norbert-pc:~$ modinfo rtl8192cefilename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BE372FB24A1F38A5218DAA0
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
```

EDIT: I didn't have the  /etc/modprobe.d/rtl8192ce.conf file before, does it need to be added to some kind of list or is it picked up automatically from that directory?

---

### Post by norbertk237 on 2015-07-12
Anybody any idea?

---

### Post by jeremy31 on 2015-07-12
Are you sure swlps is still 1, the modinfo just shows the options, not the current setting
Check ```
for p in /sys/module/rtl8723ce/parameters/*; do echo $p; cat $p; done
```

You might want to think about upgrading to 15.04 as 14.10 will be unsupported soon

---

### Post by norbertk237 on 2015-07-12
Thanks jeremy31, you're right, swlps is indeed turned off, I suppose N means no :) This is the output:
```

norbert@norbert-pc:~$ for p in /sys/module/rtl8192ce/parameters/*; do echo $p; cat $p; done
/sys/module/rtl8192ce/parameters/debug
0
/sys/module/rtl8192ce/parameters/fwlps
Y
/sys/module/rtl8192ce/parameters/ips
N
/sys/module/rtl8192ce/parameters/swenc
N
/sys/module/rtl8192ce/parameters/swlps
N

```

I misread the modinfo and thought it is set to 1. Also, I'm happy to update to later version that's not a problem but this issue persisted since I started using Ubuntu which was around Ubuntu 9-10. I didn't really bothered solving the issue because I always used my laptop as a static computer, I didn't really moved it around much, so I was fine using the cable for the internet. So, all in all, I'll probably update, but I doubt the issue would be fixed.

---

### Post by jeremy31 on 2015-07-12
```
[COLOR=#000000][FONT=Ubuntu Mono]echo "options rtl8192ce swlps=0 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```

Reboot and see if disabling fwlps helps[/FONT][/COLOR]

---

### Post by norbertk237 on 2015-07-15
It didn't help. :( The same issue is happening.

---

### Post by jeremy31 on 2015-07-15
Try
```
echo "options rtl8192ce fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
``` if it doesn't help we can try Pilot6's PPA that is based on Larry Finger's rtlwifi

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
``` reboot

---

