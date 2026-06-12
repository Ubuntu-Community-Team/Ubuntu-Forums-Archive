---
title: "HP 455 G3 amd 64bit with rtl8723be 16GB 1TB - Connection is very slow and unreliable"
date: 2016-12-05
forum: Networking &amp; Wireless
---

### Post by pilotaids on 2016-12-05
Hello everyone,
this is my first post to this forum, and also my first time using ubuntu.
I have successfully installed 16.04 lts on my new laptop, and after a lot of online research I was able to get my wireless card to work, but it keeps disconnecting, the speed is incredibly slow even if I am sitting right next to the router, and I finally connect to the network it goes extremely slow. The mac I have next to it works just fine and the signal is strong and fast.

The wireless card config I have modified so far are the following:
swenc=1
fwlps=1
ips=0
ant_sel=2

When everyone else in the house went to sleep, the speed pick-up slightly, and I am not trying to do an update using:
sudo apt-get update && sudo apt-get upgrade

Any suggestions?
Should I install a different version of ubuntu? If so, what should I use to create the usb from which I should lunch it?
Should I install kali linux instead? would it have less problem with the connection?

---

### Post by chili555 on 2016-12-06
> The wireless card config I have modified so far are the following:
swenc=1
fwlps=1
ips=0
ant_sel=2May we see the file, please? Also:```
sudo iwlist scan
iwconfig
```Thanks.

---

### Post by pilotaids on 2016-12-07
marco@HP-ProBook455:~$ sudo iwlist scan
[sudo] password for marco: 
```
lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

wlp2s0    Scan completed :
          Cell 01 - Address: EC:AA:A0:01:06:E8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"HOME-59B1-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d1060edab5
                    Extra: Last beacon: 208ms ago
                    IE: Unknown: 000D484F4D452D353942312D322E34
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8D0050F204104A0001101044000102103B000103104700105FC873FE73515423A95B6E03CC907EA110210013436973636F2053797374656D732C20496E632E10230007445043333934311024000744504333393431104200093030303030303030311054000800060050F20400011011000744504333393431100800020000103C0001011049000600372A000120
          Cell 02 - Address: EC:AA:A0:01:06:EA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d112a1c180
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 03 - Address: EC:AA:A0:01:06:E9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d112a1c180
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

marco@HP-ProBook455:~$ iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"HOME-59B1-2.4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: EC:AA:A0:01:06:E8   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42399   Missed beacon:0
```

---

### Post by wildmanne39 on 2016-12-07
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by pilotaids on 2016-12-08
Someone already change it for me.
Sorry I didn't know. I will remember next time.
Thanks for mentioning it

---

### Post by chili555 on 2016-12-08
> The wireless card config I have modified so far are the following:
swenc=1
fwlps=1
ips=0
ant_sel=2Where did you make these settings? May we see it?> IE: IEEE 802.11i/WPA2 Version 1
                        [COLOR="#FF0000"]Group Cipher : TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKMost wireless drivers as well as Dr. Chili, hate, *hate*, **hate** TKIP. Please change to CCMP, also known as AES, in the administration pages of the router. The sooner, the better, as TKIP is rather insecure.

---

### Post by pilotaids on 2016-12-09
> **chili555 said:**
> Where did you make these settings? May we see it?

Here is the code i used to set up those paramenters:

```
echo "options rtl8723be swenc=1 fwlps=1 ips=0 ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

> **chili555 said:**
> Most wireless drivers as well as Dr. Chili, hate, *hate*, **hate** TKIP. Please change to CCMP, also known as AES, in the administration pages of the router. The sooner, the better, as TKIP is rather insecure.

I live at some friends house renting out a room, and the router it's not mine.
Any suggestions on how to get around it?

---

### Post by chili555 on 2016-12-09
> echo "options rtl8723be swenc=1 fwlps=1 ips=0 ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.confI suggest that you amend the file:```
sudo gedit /etc/modprobe.d/rtl8723be.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the file from what it reads now:```
options rtl8723be swenc=1 fwlps=1 ips=0 ant_sel=2
```So that it reads:```
options rtl8723be ant_sel=1
```Reboot and let us hear your report.

Show your friends this: [https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)> TKIP uses the same underlying mechanism as WEP, and consequently is vulnerable to a number of similar attacks. The message integrity check, per-packet key hashing, broadcast key rotation, and a sequence counter discourage many attacks. The key mixing function also eliminates the WEP key recovery attacks.Tell him/her that it is therefore insecure and that everyone in the house would probably appreciate better security. 

The settings we see in the scan suggest that the router was put in place with default settings and, perhaps even the default administrative password. Many viruses depend on such vulnerability. [https://www.lifewire.com/changing-default-password-on-wifi-network-816567](https://www.lifewire.com/changing-default-password-on-wifi-network-816567)

---

### Post by pilotaids on 2016-12-10
> **chili555 said:**
> I suggest that you amend the file:```
sudo gedit /etc/modprobe.d/rtl8723be.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the file from what it reads now:```
options rtl8723be swenc=1 fwlps=1 ips=0 ant_sel=2
```So that it reads:```
options rtl8723be ant_sel=1
```Reboot and let us hear your report.

I followed one of the other posts on this forum to get to the configuration I currently have:
```
options rtl8723be swenc=1 fwlps=1 ips=0 ant_sel=2
```
With 
```
options rtl8723be ant_sel=1
```
I was not able to connect almost at all. Connection was horrible.
Once I set ant_sel=2 connection became steady. Now it's just very slow. 
I have my mac right next to my PC with ubuntu on it. While the mac it's surfing fine and at a good speed, ubuntu is very slow, and I have also noticed that the location inside the house changes the speed. By location I mean changing room but staying within the same distance from the router and whiting the same amount of walls from it as well.  

> **chili555 said:**
> Show your friends this: [https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)Tell him/her that it is therefore insecure and that everyone in the house would probably appreciate better security. 

The settings we see in the scan suggest that the router was put in place with default settings and, perhaps even the default administrative password. Many viruses depend on such vulnerability. [https://www.lifewire.com/changing-default-password-on-wifi-network-816567](https://www.lifewire.com/changing-default-password-on-wifi-network-816567)

I will definitely talk to them about this, and hopefully have them allow me to change the settings.
One I get their approval, how should I go about it? I know I should be able to get to the config page by typing the IP address of the router, but where would I find it. Any suggestions?

I also wanted to say ho much I appreciate the feedback and the help I received so far.
You guys are awesome.

---

### Post by chili555 on 2016-12-10
> One I get their approval, how should I go about it? I know I should be able to get to the config page by typing the IP address of the router, but where would I find it. It very much depends on the exact router model, but generally, under Wireless, you can find and change the encryption settings. As I said above, I recommend WPA2-AES. Her is an example: [http://www.howtogeek.com/wp-content/uploads/2014/12/ximg_548366be9a8c9.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.F324VO6Xj6.png](http://www.howtogeek.com/wp-content/uploads/2014/12/ximg_548366be9a8c9.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.F324VO6Xj6.png)

Good luck and report back if we can help you further.

---

