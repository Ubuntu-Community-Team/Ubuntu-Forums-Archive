---
title: "Slow WiFi connection - Ubuntu 18.04"
date: 2018-05-26
forum: Networking &amp; Wireless
---

### Post by gitsad on 2018-05-26
Hi, 

I've posted here ealier: [https://ubuntuforums.org/showthread.php?t=2392862](https://ubuntuforums.org/showthread.php?t=2392862) . 
It was successfully resolved but still I have one problem with WiFI.

I have two OS on my laptop: Windows and Ubuntu. I have done speed test on both. Here is the results:
Ubuntu
Download: 3.68 Mb/s
Upload: 6.83 Mb/s

Windows
Download: 109.94 Mb/s
Upload: 30.22 Mb/s

As you can see the difference is enormous. I have tried every solution from this page [https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/) which could be connected with my problem. However, nothing has helped. 

Here is my network controller
```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter
```

Every help would be appreciated. Thanks!

---

### Post by praseodym on 2018-05-26
Lets check

```
echo "options rtl8821ae swenc=1 swlps=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl88821ae_options.conf
```
Reboot

---

### Post by gitsad on 2018-05-26
It doesn't solve slow connection. Still the same :(.

---

### Post by praseodym on 2018-05-27
Please run the wireless script from the sticky thread and show the outputs

---

### Post by gitsad on 2018-05-27
Could you be more specific? What are **wireless script and sticky thread** ?

---

### Post by praseodym on 2018-05-27
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

;)

---

### Post by amvitty on 2018-05-27
Open a terminal (Ctrl+Alt+T in Ubuntu) and use the following commands one by one:
sudo su
echo "options ath9k nohwcrypt=1" >> /etc/modprobe.d/ath9k.conf
Restart your computer and you should be good to go

---

### Post by wildmanne39 on 2018-05-27
Hello amvitty and welcome to the forum, what you told this user to do will not work, the command you posted is for devices that use the ath9k driver and the OP of this thread does not have that device, before giving recommendations you must first now the device that is being used and do research to see what is most likely the cause of the users issue.

Thanks

---

### Post by gitsad on 2018-05-28
Oh right, thank you @praseodym for your help. I have done the wireless script. Here's the output: [https://pastebin.com/YWU7jthq](https://pastebin.com/YWU7jthq)

---

### Post by jeremy31 on 2018-05-28
gtisad, that was the script itself not the results, post URL from terminal for ```
cat wireless-info.txt | nc termbin.com 9999
```

---

### Post by gitsad on 2018-05-29
Oh sorry for that. Here you are: [http://termbin.com/yxg7](http://termbin.com/yxg7) O:)

---

### Post by praseodym on 2018-05-29
Lets try
```

sudo iwconfig wlp2s0 power off
```
Change the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2

---

### Post by gitsad on 2018-06-09
Hi, I hope that somebody will check this thread again :D

I've checked router configuration. I do not have mixed WPA/WPA2. I have this configuration which you have mentioned ([COLOR=#000000]WPA2-AES[/COLOR]) 
And command didn't help :(

---

### Post by jeremy31 on 2018-06-09
Do ```
sudo rm /etc/modprobe.d/rtl8821ae.conf
```
As you have a incorrect parameter there
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf && systemctl restart network-manager.service
```
That should keep wifi power management off
Check router settings again and see if you can disable TKIP as the script results showed
```
                   Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"5G-vnet-DB7D72"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000278c626733
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by gitsad on 2018-06-09
Thank you so much! :D
These changes solved everything. @Jeremy you are the best.

---

### Post by gitsad on 2018-06-09
However, no. Everything goes back after rebooting. What can I do to make these changes permanently?

---

### Post by jeremy31 on 2018-06-09
I wonder if you have a different issue
```
sudo apt install git build-essential dkms
git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Reboot

---

### Post by gitsad on 2018-06-09
Still the same :(

---

### Post by jeremy31 on 2018-06-09
Run the script again ```
./wireless-info
```
Post new results

---

### Post by gitsad on 2018-06-09
Here you are: [http://paste.ubuntu.com/p/CwxVvvWndz/](http://paste.ubuntu.com/p/CwxVvvWndz/)

---

### Post by jeremy31 on 2018-06-09
Your access point settings haven't changed, still using mixed mode encryption
```
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by gitsad on 2018-06-09
What do you mean? Is my router`s condiguration is incorrect ? As I said, my router is set to WPA2-AES encryption. :?:

---

### Post by jeremy31 on 2018-06-09
But the script results are showing WPA1/WPA2 with AES and TKIP
You might need to reboot the router

---

### Post by sinsoff on 2018-08-15
Hi, Jeremy. My issue with wireless seems to be similar with gitsad's one. I've tried many solutions, but nothing helps. Could you check my wireless-info?

[https://pastebin.com/fWvDE1Yx](https://pastebin.com/fWvDE1Yx)

---

