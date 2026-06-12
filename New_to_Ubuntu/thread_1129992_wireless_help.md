---
title: "wireless help?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-19
Ok just installed linux mint 6 (I know it's not ubuntu but it might as well be..) on my mums laptop but for some reason I cant turn the wireless on normally you press the button at the top until the light turns blue but unfortunately when I press it nothing happens...

I've tried the command iwconfig and I get the following:
```
sally@sallys-laptop ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by acimmarusti on 2009-04-19
what's the wireless device you have?

```

lspci -v | grep Network

```

Check if that particular device has some issues with ubuntu and thus with mint.

---

### Post by kamitsukai on 2009-04-19
```
sally@sallys-laptop ~ $ lspci -v | grep Network
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by kamitsukai on 2009-04-19
it's ok now for some reason it works...0_o

---

### Post by acimmarusti on 2009-04-19
awesome. Computers are sometimes a little funky...I had the same issue when I installed hardy for the first time on my laptop. I had everything I needed for the wireless to work and nothing happened...I started screwing around and checking the programs installed. Then I decided to click on network manager and suddenly my wireless network appeared and has never dissapeared ever since...

This is another, yet unrelated, story. I installed Debian lenny briefly but I decided to go back to ubuntu 8.10, so I reinstalled (I reformatted the hard drive). When booting for the first time, Debian's wallpaper appeared briefly on screen for a few seconds and then dissappeared (never to return) and ubuntu theme was visible...that was weird!

---

### Post by kamitsukai on 2009-04-19
Computers can be strange sometimes =] 

Thanks for your help!

---

