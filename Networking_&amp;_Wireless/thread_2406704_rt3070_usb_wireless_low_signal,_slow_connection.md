---
title: "rt3070 usb wireless low signal, slow connection"
date: 2018-11-24
forum: Networking &amp; Wireless
---

### Post by severin_double on 2018-11-24
I have run the wireless info script which can be found at: [http://paste.ubuntu.com/p/9Mf3STTqrj/](http://paste.ubuntu.com/p/9Mf3STTqrj/)

As per the instructions here: [https://answers.launchpad.net/ubuntu/+question/244410](https://answers.launchpad.net/ubuntu/+question/244410), I ran the commands: echo "options rt2800usb nohwcrypt=1" | sudo tee -a /etc/modprobe.d/rt2800usb.conf
 sudo depmod -a to no avail

I have tried to find up-to-date drivers, but no luck. Is there a bug in the kernel? Any help much appreciated. Thanks beforehand. I'm running the latest version of ubuntu (18.04) and have not been able to find any help. I bought this particular device because I read that it was compatible with linux and have since discovered it works fine with kali (apparently, I have not tested it), but I do not want to use kali as it is a bit hard core. Cheers

---

### Post by chili555 on 2018-11-24
> Cell 01 - Address: <MAC 'virginmedia8501228' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"virginmedia8501228"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e06fd62495
                    Extra: Last beacon: 200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
Most Linux drivers, as well as old Chili, hate hate hate TKIP.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.  

After rebooting the computer and the router, post back the result. Any improvement?

---

### Post by severin_double on 2018-11-25
Hi there chili. Thanks for all your help thus far. I have a virgin superhub 2. I have changed the security mode to WPA2-PSK{AES] and set it to explicitly use channel 6. It is capable of N speed and it is set to the 2.4GHz setting, but I cannot find how to change it to the 20MHz range. I also have not been able to find how to change it from N speed to B/G and N. I have changed the domain to GB, rebooted the router and the computer, but still no change

---

### Post by praseodym on 2018-11-25
Please run
```

sudo iwconfig wlx<IF power off
```

---

### Post by severin_double on 2018-11-26
Sorry [**[COLOR=#000000]praseodym[/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497"), but that just comes back with bash: IF: No such file or directory

---

