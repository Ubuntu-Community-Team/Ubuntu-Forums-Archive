---
title: "TP-LINK WN823N - can see but can't connect to my network"
date: 2018-02-23
forum: Networking &amp; Wireless
---

### Post by cosmickid on 2018-02-23
Hi,
I'm new to Ubuntu. I use 16.04.3 LTS. I've just bought a wifi adapter I mentioned in the title. Everything seems to work fine, I can see my network in the network manager and type in my password. However, I can't connect to it, it tries to do so for some time but with no result.

I've previously tried to download and install rtl8192eu-dkms drivers but I couldn't make it work.

```
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rtl8192eu-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.13.0-36-generic (x86_64)
Consult /var/lib/dkms/rtl8192eu/4.4/build/make.log for more information.
```

Here's the result of wireless info script:

[http://paste.ubuntu.com/p/p8SctCbmRN/](http://paste.ubuntu.com/p/p8SctCbmRN/)

I'd appreciate if you could tell me what the problem is.

---

### Post by chili555 on 2018-02-23
Before we try more extreme measures, let's see if we can tweak your existing setup a bit.

We see this in your results:> Cell 02 - Address: <MAC 'ekchartnet' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"ekchartnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e78b0183
                    Extra: Last beacon: 1036ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher :[COLOR="#FFA07A"] TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FFA07A"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKMany wireless drivers and especially old Chili hate hate hate TKIP. [https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)> TKIP is vulnerable to a MIC key recovery attack that, if successfully executed, permits an attacker to transmit and decrypt arbitrary packets on the network being attacked.In short, TKIP is rather insecure.

WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Also, please set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Reboot the computer. Any improvement?

---

### Post by cosmickid on 2018-02-24
Thank you for the answer, I had to do some googling because I'm not  really familiar with this topic. I set my router to WPA-PSK, 2.4 GHz  band and channel 1. I also set my regulatory domain (it was 00 indeed).  Anyway, there's no improvement in overall. Also, I still can't connect to my network even  though it appears on the list.

I believe this is a problem with  my usb wifi card itself rather than my network (but still, I'm thankful  for the tips). It works fine when I try to connect to it from my laptop  running on windows. Also, if I run wifi hotspot on my android device, I  can connect to it from laptop with windows but still can't do that from  my PC with Ubuntu (with aforementioned wifi adapter). I think I may not  have drivers setup correctly but I'm not sure how I should go about it.

---

### Post by chili555 on 2018-02-24
>  I set my router to WPA-PSKI hope you set it to WPA[COLOR="#FF0000"]2[/COLOR]-[COLOR="#FF0000"]AES[/COLOR]. Is that the case? 

If so and if you are still having trouble, we'll dig a bit deeper.>  It works fine when I try to connect to it from my laptop running on windows. That only suggests that the hardware and the router are working correctly. It tells us nothing about the Ubuntu driver.

---

### Post by cosmickid on 2018-02-24
Sorry, I meant WPA2-PSK which as far as I can see uses AES encryption.

By the way, I solved my problem, I finally found suitable drivers here: [https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)
Compiled, installed, I can connect to my network as I desired.

[https://ubuntuforums.org/showthread.php?t=2335795](https://ubuntuforums.org/showthread.php?t=2335795) - this thread turned out to be useful, strange I didn't find it when I did some extensive search.
Anyway, thanks for your time, this thread can be marked as solved now.

---

