---
title: "Cannot compile wireless card driver in ubuntu: RNX-N180PCe"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by ThoseTimesAreGone on 2013-10-14
Hey guys,

I am having a problem on linux mint 15 / ubuntu 12.04.03 trying to compile my wireless card driver. The wireless card is this one:
[http://www.rosewill.com/products/1698/ProductDetail_Download.htm](http://www.rosewill.com/products/1698/ProductDetail_Download.htm)

Whenever I try to compile, it gives me an errors seen here:

[http://i.imgur.com/FBP6YPd.png](http://i.imgur.com/FBP6YPd.png)

What to do?

---

### Post by chili555 on 2013-10-14
> **ThoseTimesAreGone said:**
> Hey guys,

I am having a problem on linux mint 15 / ubuntu 12.04.03 trying to compile my wireless card driver. The wireless card is this one:
[http://www.rosewill.com/products/1698/ProductDetail_Download.htm](http://www.rosewill.com/products/1698/ProductDetail_Download.htm)

Whenever I try to compile, it gives me an errors seen here:

[http://i.imgur.com/FBP6YPd.png](http://i.imgur.com/FBP6YPd.png)

What to do?What to do? First, the package is marked on Rosewill's site as for kernel 2.6.xx; you have 3.8.0-31. The package is old, old, old and won't ever work.

Second, most rtl819xx drivers are included in 3.8.0-xx by default. If yours isn't working as expected, we ought to troubleshoot it rather than go shopping for antiques. 

Let's identify your exact device:```
lspci -nn | grep 0280
```

---

### Post by ThoseTimesAreGone on 2013-10-14
The wireless card connects and holds a stable connection, but the speed at which it connects is way too low. ~3MBPS with drops down to 1 mbps. This makes gaming very difficult, and a lot of times impossible. Very frustrating. 

The output from the terminal is as follows:


domce@HAF932 ~ $ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
domce@HAF932 ~ $ 


I need to have a well working wireless card. This one is rated at 300 mbps but can only give 1/100th of its rated speed. If it means I need to buy a new PCI card for my desktop then I will order it immediately. My laptop has a centrino wireless card and gets up to 15-17 mbps (even though i am only paying for 10 mbps) ... which is quite amazing. If we cant get to the bottom of this I will ask you to recommend me the best wireless PCI card that money can buy for linux so I can game in peace. Also i bought this card like 2 years ago so im not sure if I would call it ancient.

---

### Post by chili555 on 2013-10-14
Let's see if we can figure out its low speeds. Please run and post:```
dmesg | grep -e wlan -e rtl
```

---

### Post by ThoseTimesAreGone on 2013-10-14
domce@HAF932 ~ $ dmesg | grep -e wlan -e rtl
[   21.533556] rtl8192se: FW Power Save off (module option)
[   21.533579] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   21.533579] Loading firmware rtlwifi/rtl8192sefw.bin
[   21.633639] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   22.069279] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.069449] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.199427] wlan0: authenticate with 00:14:bf:8f:12:01
[   24.218746] wlan0: send auth to 00:14:bf:8f:12:01 (try 1/3)
[   24.221699] wlan0: authenticated
[   24.221836] rtl8192se 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   24.221838] rtl8192se 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   24.222735] wlan0: associate with 00:14:bf:8f:12:01 (try 1/3)
[   24.224940] wlan0: RX AssocResp from 00:14:bf:8f:12:01 (capab=0x411 status=0 aid=3)
[   24.225941] wlan0: associated
[   24.225947] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14097.237015] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.72 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=49 ID=60774 PROTO=TCP SPT=443 DPT=34734 WINDOW=0 RES=0x00 RST URGP=0 
[14097.237240] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.72 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=49 ID=60775 PROTO=TCP SPT=443 DPT=34734 WINDOW=0 RES=0x00 RST URGP=0 
[14098.298996] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.131.106 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=40 ID=11712 PROTO=TCP SPT=443 DPT=58155 WINDOW=0 RES=0x00 RST URGP=0 
[14098.307516] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.131.106 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=40 ID=11714 PROTO=TCP SPT=443 DPT=58155 WINDOW=0 RES=0x00 RST URGP=0 
[14100.217743] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=173.194.46.34 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=49 ID=14613 PROTO=TCP SPT=443 DPT=53774 WINDOW=0 RES=0x00 RST URGP=0 
[14100.222867] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=173.194.46.34 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=49 ID=14615 PROTO=TCP SPT=443 DPT=53774 WINDOW=0 RES=0x00 RST URGP=0 
[14118.238839] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.37 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=49 ID=24099 PROTO=TCP SPT=443 DPT=56235 WINDOW=0 RES=0x00 RST URGP=0 
[14118.239486] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.41 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=49 ID=46739 PROTO=TCP SPT=443 DPT=57036 WINDOW=0 RES=0x00 RST URGP=0 
[14118.239775] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.41 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=49 ID=46740 PROTO=TCP SPT=443 DPT=57036 WINDOW=0 RES=0x00 RST URGP=0 
[14118.240204] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=173.194.46.41 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=5829 PROTO=TCP SPT=443 DPT=38484 WINDOW=0 RES=0x00 RST URGP=0 
[14123.231963] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.130 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=26507 PROTO=TCP SPT=443 DPT=50601 WINDOW=0 RES=0x00 RST URGP=0 
[21552.387358] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.130 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=64356 PROTO=TCP SPT=443 DPT=51560 WINDOW=0 RES=0x00 RST URGP=0 
[21552.388019] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.130 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=64358 PROTO=TCP SPT=443 DPT=51560 WINDOW=0 RES=0x00 RST URGP=0 
[21552.388232] [UFW BLOCK] IN=wlan0 OUT= MAC=00:08:54:9e:f4:6b:00:14:bf:8f:11:ff:08:00 SRC=74.125.225.130 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=64359 PROTO=TCP SPT=443 DPT=51560 WINDOW=0 RES=0x00 RST URGP=0 
domce@HAF932 ~ $





Check out my speedtest results with this card...This is my gaming rig mind you and unfortunately ethernet is not an option. now usually it hovers around 3-4 mbps, sometimes rises to 8 mbps, and sometimes falls to very low speeds. When i play Dota 2= i get owned b/c of this. Sometimes i even get disconnected. Sometimes youtube videos stop loading etc... Just generally not very stable. Although it never says the connection is dropped.

[http://i.imgur.com/j59ee06.png](http://i.imgur.com/j59ee06.png)



And on my laptop which has an intel centrino wireless card (on the same network), about 3 minutes after i did the dekstop test:

[http://i.imgur.com/qPCAtr6.png](http://i.imgur.com/qPCAtr6.png)

Also i put computers in the same spot in the house which is literally about 10 ft from the router. Obviously something isnt working here b/c the desktop card is rated for even higher speed than the laptop one. Also weird how the upload speed isnt affected only download.

---

### Post by chili555 on 2013-10-14
Are conditions better or worse with the firewall temporarily disabled?```
sudo ufw disable
```

---

### Post by ThoseTimesAreGone on 2013-10-14
I tried before running the command and now its at 5 mbps. the firewall turn off didnt really change it (still at 5). So I do not think it worked unfortunately. Thank you so much for trying to help !

---

### Post by chili555 on 2013-10-15
Let's try the driver suite from kernel 3.11. I suggest you download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:```
cd Desktop/backports-3.11-rc3-1/
make defconfig-rtlwifi
make
sudo make install
sudo modprobe -r rtl8192se && sudo modprobe rtl8192se
sudo ufw enable
```Any improvement?

If this helps, we'll have a few extra steps to take.

---

### Post by ThoseTimesAreGone on 2013-10-15
I just executed the command. Upon restart I got a pop up message with an error regarding the display server or something. Clicking enter like 4-5 times got me through it though lol. Its no worries if this system breaks though this is for a good cause. No vital info is on this pc.

Anyway, so I ran the tests and i got very variable results at first i noticed it was much quicker to load speedtest.net website. Either way i ran like 4 tests, and I got as low as 1.2 mbps, and for the first time a high of 9.8mbps. So Its hard for me to tell. Obviously a drop to 1 is no good, but ive never seen this card put out 9.8 either. What do you think?

EDIT: moving the antennas helped an additional amount. So now the max was up to 12-13 mbps. This is def high enough even like 7-8 would be good enough for me. Any way to ensure it doesnt drop to as low as 1 mbps?

---

### Post by chili555 on 2013-10-15
> Any way to ensure it doesnt drop to as low as 1 mbps? Not that I know of; I've done all I know to do. I'd just be sure the antannae and the router itself are aligned for the best result. For example, in my router, to reach all parts of my two-story house, it needs to sit at about a 45° angle. Of course, your results will probably vary.

---

### Post by ThoseTimesAreGone on 2013-10-15
you mentioned in the previous thread a few extra steps. do we need to do that or no?

---

### Post by chili555 on 2013-10-15
> **ThoseTimesAreGone said:**
> you mentioned in the previous thread a few extra steps. do we need to do that or no?Yes.Whenever Update Manager installs a later kernel version, known in Ubuntu as linux-image, after reboot, you'll need to recompile the newer driver:```
cd Desktop/backports-3.11-rc3-1/
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe -r rtl8192se && sudo modprobe rtl8192se
```Please retain the files and these instructions for that time.

---

