---
title: "Install Tenda_W311MI on Ubuntu 15.04 (beginner)"
date: 2016-08-28
forum: Networking &amp; Wireless
---

### Post by arun24 on 2016-08-28
I am trying to install Tenda wifi adapter on my desktop pc running 15.04 - 64bit. (I have tried some instructions here [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M) , and few other threads, but didnt help. )
I am Linux beginner and the install instructions on the CD's linux driver folder are a bit overwhelming for me.

This is the readme text file.

> 
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2870sta



Can anyone **kindly explain steps 2 to 4 in simpler terms**, please.
Thanks a million in advance.

---

### Post by Bucky Ball on 2016-08-28
Welcome. 15.04 has reached end of life and is no longer supported. It is better you install a supported release so we can give you better help as things change a bit from one release to the next. Your wireless may work 'out of the box' in 16.04 LTS as drivers improve all the time. Also, 16.04 is LTS, long-term support, so supported for five years until 2021. The interim releases are supported for nine months for now.

15.04 hasn't had updates since January, including security updates, so better you upgrade.

(PS: The Linux drivers on the CD that comes with the dongle are often useless.)

---

### Post by arun24 on 2016-08-28
Thanks a lot Bucky Ball. 
Please tell me if I can upgrade directly to 16.04 from 15.04? 
Do I just boot with the 16.04 dvd?
I have a program running on Wine, is there a chance that it will work after the upgrade.
Thanks again.

---

### Post by Bucky Ball on 2016-08-28
> **arun24 said:**
> Please tell me if I can upgrade directly to 16.04 from 15.04? 

Not without some difficulty. It is not a smooth path, but do-able, though wouldn't advise. You might [take a look here]("https://help.ubuntu.com/community/EOLUpgrades") and see how you go.
 
> Do I just boot with the 16.04 dvd?

Apparently that can be done, but I've never done it. The usual way is to check update manager and you should be offered an upgrade to the latest release there. You would then simply agree to upgrade and the upgrade would be done online, no disk/USB required. Don't think that will happen for you and if it does, it will probably offer 15.10, also EOL so don't go there. Have a look and see.

> I have a program running on Wine, is there a chance that it will work after the upgrade.


Under normal circumstances where you upgrade from a supported release to another, probably, everything would/should remain as was with the OS and apps, where necessary, upgraded. Not sure under these circumstances, though. It also depends on how you have your partitions set up and what data you have where. After a clean install, naturally, no, everything would be wiped and written over (so good backups imperative and if you don't already have them I'd do them now as you are about to do something which may go pear-shaped, but probably won't of course!). :)

---

### Post by arun24 on 2016-08-29
Thanks a lot Bucky Ball for your comprehensive reply..
All other devices are running perfectly & I am in a dilemma whether to upgrade for this (wifi dongle; I do have a wired connection) as it is not as easy as upgrading to the next version.
Or first to 15.10 and to 16.04 from there? :confused: just so that I can retain my current configuration - hopefully. 
Thanks again..

---

### Post by Bucky Ball on 2016-08-29
> **Bucky Ball said:**
> The usual way is to check update manager and you should be offered an upgrade to the latest release there. You would then simply agree to upgrade and the upgrade would be done online, no disk/USB required. Don't think that will happen for you and if it does, *_**it will probably offer 15.10, also EOL so don't go there**._* Have a look and see.

;)

You have a long a treacherous road to 16.04 via upgrades, but if you're willing to go for it and have your learning and thinking hats on, do so! 

Personally, I'd back up what I have to, clean install 16.04 LTS and be done with it.

---

### Post by arun24 on 2016-08-29
Thanks again bucky ball.. Ok, so the best option is a fresh install.
Will try that..

---

### Post by Bucky Ball on 2016-08-29
Good luck and see you on the flip side. As long as you have reliable back ups, what could possibly go wrong? :)

Just be aware of any UEFI stuff you need to do if you are dual-booting with Win, but you're probably across all that if you've installed on this before.

---

