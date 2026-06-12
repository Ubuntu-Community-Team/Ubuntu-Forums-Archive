---
title: "Netbook: no wifi"
date: 2014-01-08
forum: Networking &amp; Wireless
---

### Post by jlh68 on 2014-01-08
History:  New netbook purchased 4 months ago.  It would not connect to my WiFi. Shortly after trying to work this out with some posts to this forum, my Laptop quit working, so I took the Laptop HD and put it into the Netbook.  With my Laptop HD inw installed in the Netbook the WiFi was completly operational.  I had messed up the dual boot (Win7 and Ubuntu), with only Ubuntu working.  I have recently put the Netbook HD back into the Netbook and I used Boot-Repair to correct the boot problem.  

Now I am trying to tackle the WiFi not working problem.  So I am requesting help.  I can make the Netbook connect online by using the Ethernet connection with a hard wire.  

Could I use the WiFi files on the Laptop and copy them to the Netbook?

Suggestions.

---

### Post by chili555 on 2014-01-08
Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by jlh68 on 2014-01-08
> john@Osprey:~$ lspci -nn | grep 0200 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) 
john@Osprey:~$ rfkill list all 
0: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
john@Osprey:~$ 

As requested

---

### Post by chili555 on 2014-01-08
> **jlh68 said:**
> As requestedIt probably doesn't show up very well, but it's actually:```
lspci -nn | grep 02[COLOR="#FF0000"]**8**[/COLOR]0
```oh-two-eight-oh.

---

### Post by jlh68 on 2014-01-08
> john@Osprey:~$ lspci -nn | grep 0280 
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01) 
john@Osprey:~$ rfkill list all 
0: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
john@Osprey:~$ 

This time 0280

---

### Post by chili555 on 2014-01-08
> Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032]Your device works with the driver *ath9k* built in to most recent Ubuntu versions. Let's load it and see if there are any errors or warnings and then check the logs:```
sudo modprobe ath9k
dmesg | grep ath
iwconfig
```Which version are you running?```
lsb_release -d
```

---

### Post by jlh68 on 2014-01-08
here is what I got:
> john@Osprey:~$ sudo modprobe ath9k
[sudo] password for john: 
FATAL: Error inserting ath9k (/lib/modules/3.5.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid argument
john@Osprey:~$ sudo modprobe ath9k
FATAL: Error inserting ath9k (/lib/modules/3.5.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid argument
john@Osprey:~$ dmesg |grep ath
[   16.895533] ath9k: `1' invalid for parameter `enable_diversity'
[  116.205534] ath9k: `1' invalid for parameter `enable_diversity'
[  136.828655] ath9k: `1' invalid for parameter `enable_diversity'
john@Osprey:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

john@Osprey:~$ 


---

### Post by chili555 on 2014-01-08
It appears someone attempted a driver parameter. Do you have a file /etc/modprobe.d/ath9k.conf or similar? If so, it has an error in it.```
ls /etc/modprobe.d
cat /etc/modprobe.d/ath9k.conf
```There may be other issues as well, but let's see.

---

### Post by jlh68 on 2014-01-08
These are the wiireless files from the Laptop HD, which when installed in the Netbook produced a working wifi.  I thought  maybe it would help you while we work throught this.
> /media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/net/wireless/cfg80211.ko
/media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/net/wireless/lib80211.ko
/media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/net/wireless/lib80211_crypt_ccmp.ko
/media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/net/wireless/lib80211_crypt_tkip.ko
/media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/net/wireless/lib80211_crypt_wep.ko

---

### Post by chili555 on 2014-01-08
> **jlh68 said:**
> These are the wiireless files from the Laptop HD, which when installed in the Netbook produced a working wifi.  I thought  maybe it would help you while we work throught this.Not really but thanks.

---

### Post by jlh68 on 2014-01-08
I have both of these on both hard drives.  I think we have to look into another area. 

> /media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
/media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
/media/Ubuntu 12.04LTS/lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko

---

### Post by chili555 on 2014-01-08
How about what I asked for in post #8? Anything??

---

### Post by jlh68 on 2014-01-08
Sorry I missed that post earlier.

> john@Osprey:~$ ls /etc/modprobe.d 
alsa-base.conf          blacklist.conf              blacklist-oss.conf 
ath9k.conf              blacklist-firewire.conf     blacklist-rare-network.conf 
ath9k.conf~             blacklist-framebuffer.conf  blacklist-watchdog.conf 
blacklist-ath_pci.conf  blacklist-modem.conf        vmwgfx-fbdev.conf 
john@Osprey:~$ cat /etc/modprobe.d/ath9k.conf 
options ath9k nohwcrypt=1 blink=1 btcoex_enable=1 enable_diversity=1 
john@Osprey:~$ 

---

### Post by chili555 on 2014-01-08
Ah, ha! Let's experimentally remove the file and reboot:```
sudo rm /etc/modprobe.d/ath9k.conf
```Off for the evening, I'll check tomorrow.

---

### Post by jlh68 on 2014-01-08
Yes more tommorrow, I am in the EST so it is getting late for me also.

I have removed the file and I am rebooting.

Well what do you know?  The WiFi is now working, it logged into my router just fine.

That is a **Bravo Zulu** to you for helping me through this.  (BZ is U.S.Navy speak for a job well done).

---

### Post by chili555 on 2014-01-09
Awesome! May I get a Solved, also? [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

