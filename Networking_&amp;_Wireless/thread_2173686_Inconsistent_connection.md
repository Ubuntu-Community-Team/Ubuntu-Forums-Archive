---
title: "Inconsistent connection"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by HJQG3wT on 2013-09-10
[FONT=arial]My connection is inconsistent on my desktop, and is good on my adjacent laptop. Both are 13.04.[/FONT]

[FONT=arial]Most recently, pinging 192.168.1.1 i got 17% packet loss and average ping time ~400ms.[/FONT]

[FONT=arial]varunendra had me run a script -- the output is here: [/FONT][http://paste.ubuntu.com/6082590/](http://paste.ubuntu.com/6082590/) (I've replaced my network name with "mynetwork".)

[FONT=arial]I'm willing to purchase a new card if that will make this problem go away, but it would of course be nice if that weren't necessary.[/FONT]

[FONT=arial]Thanks in advance.[/FONT]

---

### Post by chili555 on 2013-09-10
Varun is such a sweet person, isn't he; tossing me the hard ones.

Here are some things I suggest you try. Please do one at a time and when we find the first thing that works, stop.

Please open a terminal and do:```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```If it helps, we'll write one file and make it persistent.

Turn off N speeds in the router:> wlan0     IEEE 802.11bgn  ESSID:"mynetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          [COLOR="#FF0000"]Bit Rate=117 Mb/s [/COLOR]  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:838   Missed beacon:0

Some drivers work very well at N speeds and some not well at all.

Last, we might try a newer driver version. Please get a temporary wired ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential
```I suggest you download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2)  Right-click it and select 'Extract Here.' Now open a terminal and do:
```
cd Desktop/backports-3.11-rc3-1/
make defconfig-ath9k
make
sudo make install
sudo modprobe -r ath9k
sudo modprobe ath9k

```
Any improvement?

---

### Post by varunendra on 2013-09-11
> **chili555 said:**
> Varun is such a sweet person, isn't he; tossing me the hard ones.

Yup ! That's what true disciples are meant for.. :D

---

### Post by HJQG3wT on 2013-09-12
The last step seems to have improved things -- my connection seems to generally work now. Thanks very much!!

Are those changes permanent? If not, how do I make them stay?

Could you possibly explain what that does?

Thanks.

---

### Post by chili555 on 2013-09-12
> **HJQG3wT said:**
> The last step seems to have improved things -- my connection seems to generally work now. Thanks very much!!

Are those changes permanent? If not, how do I make them stay?

Could you possibly explain what that does?

Thanks.It simply installs the later ath9k driver and all its dependents ath9k_hw, ath9k_common, mac80211, ath and cfg80211 backported from kernel version 3.11. You are currently running 3.8. It is compiled only for your current kernel version. When Update Manager offers a shiny new linux-image, also known as kernel version, after you reboot, you will need to re-compile:```
cd Desktop/backports-3.11-rc3-1/
[COLOR="#FF0000"]make clean[/COLOR]
make defconfig-ath9k
make
sudo make install
sudo modprobe -r ath9k
sudo modprobe ath9k
```Please retain the files and these notes for that time. 

When you upgrade to Ubuntu 13.10 which uses kernel version 3.10, you may find your wireless working well. If so, you can probably chalk this experience up to a temporary work-around.

Glad it's working!

---

### Post by HJQG3wT on 2013-09-12
Sounds good! Thanks Chili555 and varunendra!

---

### Post by varunendra on 2013-09-12
> **HJQG3wT said:**
> Sounds good! Thanks Chili555 **and varunendra!**

Haha.. a broker's commission, happily accepted !! :P

---

