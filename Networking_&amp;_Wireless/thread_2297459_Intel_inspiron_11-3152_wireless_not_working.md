---
title: "Intel inspiron 11-3152 wireless not working"
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by Lucian257 on 2015-10-03
Hey all, been trying most of the day to get a new laptop up and running and can't for the life of me figure it out... ok, so wifi has not worked a single time, when I first went to install 14.04 I had ZERO luck with it, would only boot in low graphics mode, finally got 15.04 on it and it is working great like every ubuntu does normally... except for the wireless... It has no eth port so I'm kinda SOL there as far as just running a sudo apt-get update, I have been trying to find anything that I can on it but everything I am finding is for broadcom issues. What I am getting with lshw -c network is as follows
*-network UNCLAIMED
        description: Network controller
       product: Intel Corporation
       vendor:Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version :79
       width:64 bits
       clock: 33Mhz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:91200000-91201fff


HALP!!! anyone?

---

### Post by jeremy31 on 2015-10-04
Post the result of ```
lspci -nnk | grep -iA2 net
```

---

### Post by Lucian257 on 2015-10-04
Thanks so much for your quick response, see below for lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Intel Corporation Device [8086:3165] (rev 79) 
           Subsystem: Intel Corporation Device [8086:3310]

---

### Post by jeremy31 on 2015-10-04
Do you know if this is a dual band AC chipset or just single band AC?  It isn't supported in the kernel from what I see

From what is in the kernel source now, it seems they are all dualband ac

---

### Post by Lucian257 on 2015-10-04
I believe it is dual band ac, is there any way to check?

---

### Post by jeremy31 on 2015-10-04
I think it is a safe bet that it is dual band AC, it should be on the sticker on the wifi card.  Some you can read by removing a panel on the bottom of the laptop

```
sudo apt-get install build essential linux-headers-$(uname -a)
wget https://www.dropbox.com/s/gyuvdlhzx5ho277/backports-20150731.tar.gz
tar -zxvf backports-20150731
cd backports-20150731
make defconfig-iwlwifi
make
sudo make install
```

Then reboot,

Nevermind, forgot no ethernet

What kernel do you have?```
uname -a
```

I might be able to compile the modules and upload them

---

### Post by Lucian257 on 2015-10-04
Again, you are my hero if you can send em up here

Linux lucian2579Inspiron01103152 3.19.0-15-generic#15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 GNU/Linux

whoops, seems like i cant type today

Linux lucian257-Inspiron-11-3152 3.19.0-15-generic#15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 GNU/Linux

---

### Post by jeremy31 on 2015-10-04
Actually you can do it yourself download [COLOR=#000000][FONT=Ubuntu Mono]https://www.dropbox.com/s/gyuvdlhzx5ho277/backports-20150731.tar.gz and get it on the desktop of Ubuntu 15.04 then
```
cd Desktop
[/FONT][/COLOR]tar -zxvf backports-20150731
cd backports-20150731
make defconfig-iwlwifi
make
sudo make install
```

Reboot and tell us what ```
dmesg | grep iwl
```
reveals.  I know Chili555 knows what to do with the firmware so I will look for his post[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-10-04
[http://ubuntuforums.org/showthread.php?t=2296254&p=13362521#post13362521](http://ubuntuforums.org/showthread.php?t=2296254&p=13362521#post13362521)

For instructions on getting the firmware installed, reboot again after that

---

### Post by Lucian257 on 2015-10-04
ok... you are my hero offically, took a bit of reworking on the  firmware, for some reason, the firmware for 3.19 didnt work but the one  for 4.1 did, who knows, but its up and running in the wireless  department now!!! thanks a bunch I also have a feeling that the firmware  for 4.2 would have worked as well and if I have any issues in the  future I may try going up to that. dmesg | grep iwl is now passing when  it hits 25.30.13.0 , gunna run a sudo apt-get update reboot, then if it  is still working, i ill solve this thread

---

### Post by jeremy31 on 2015-10-04
After you update, you may have a newer kernel that will temporarily break this
```
[COLOR=#000000][FONT=Ubuntu Mono]cd Desktop/backports-20150731
make clean
[/FONT][/COLOR]make defconfig-iwlwifi
make
sudo make install
```

reboot, and you will have to repeat these steps after every kernel update

The 25.30.13.0 makes sence after looking at the source I used as it is the minimum version suspported, great job figuring that out

I learned from some of the best here

---

### Post by Lucian257 on 2015-10-04
alright, looks like i did need to grab the newest version of the firmware, number 15, after the update and upgrade. everything is up and running, speedtest shows 128 mbps down and 20 up so everything is good to go. THANKS again

---

