---
title: "Slow WiFi on Lenovo Yoga Ubuntu 14.10"
date: 2015-01-26
forum: Networking &amp; Wireless
---

### Post by PaulFrmBrn on 2015-01-26
Hi, everyone!
I've got Ubuntu 14.10 installed on my Lenovo Yoga. Everyting looks fine, but WiFi connection is too slow comparing with Windows 8.1.
I've searched for info in this forum but did not find the clue.

lsusb shows:

```
Bus 001 Device 005: ID 0bda:1724 Realtek Semiconductor Corp.
```

i've ried to insall [rtl8723ae]("https://github.com/lwfinger/rtlwifi_new/tree/master/rtl8723ae") from here [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) , becouse it was suggested in some other thread.
Also tried ti install this driver [https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au), posted in [http://ubuntuforums.org/showthread.php?t=2178572](http://ubuntuforums.org/showthread.php?t=2178572), 
But the final step
```
[COLOR=#000000]sudo modprobe 8723au[/COLOR]
``` 
triggered this:
```
modprobe: ERROR: could not insert '8723au': Device or resource busy
```
And now i'm stuck.

I would be very apriciate for help

Thank's in advance

---

### Post by chili555 on 2015-01-26
Just for the benefit of you and the searchers, your device isn't *both* an rtl8723ae and an rtl8723au device. A Google search of the usb.id of 0bda:1724 suggests r8723au. We can then check modinfo:```
modinfo r8723au | grep 1724
```And we see:```
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]1724[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*
```So we confirm that your device is driven, in 14.10, by r8723au.

> modprobe: ERROR: could not insert '8723au': Device or resource busyThat simply means that the native driver r8723au is driving your device and there is no room at the table for the newly compiled 8723au. You can solve that by blacklisting the in-kernel driver, rebooting and allowing the compiled version to take over. 

We have, however, no evidence whatever that the compiled version is better and the in-kernel version less good. There are a few things we can do to troubleshoot the in-kernel version. 

You have already gone down the long road to compile a possibly better, possibly not driver. We need to blacklist one or the other or else they will conflict and neither will work well! Experimentally, from the terminal:```
sudo -i
echo "blacklist r8723au"  >>  /etc/modprobe.d/blacklist.conf
reboot
```Any improvement?

---

### Post by PaulFrmBrn on 2015-01-27
Thanks for quick reply!
Unfortunatelly, now i'm at work and that's why i can not try the solution you've suggested.
As soon as i get home i will try it. I will reply in 7-8 hours.
Thanks once again!

---

### Post by PaulFrmBrn on 2015-01-27
[COLOR=#000000][FONT=Verdana][COLOR=#222222][FONT=Verdana]Hi again![/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Sorry for late response but i've faced some strange behaviour.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Before trying your solution i've decided to test my WiFi connection.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Transmition was showing 1.5-2.5 MB/s. speedtest utility - 16-20 Mbits/s too. for several requests[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]So it seemd fine. And this is strange - i did nothing since my first post in this thread.
Then i've found that if i reboot the laptop and start win8.1 (in windows no WiFi nwetwork could be found in this case) and then start Ubuntu once again WiFi connection will fall down to 0.3-0.4 Mbits/s. 
The only way to speed up the connection is to shut down the laptop for a while (5-10 seconds) and than start ubuntu. In this case speed will be normal (up to 25 Mbits/s).
[/FONT][/COLOR]
For now i've  did not performed this commands[COLOR=#222222][FONT=Verdana]:[/FONT][/COLOR]
[/FONT][/COLOR]
```
sudo -i
echo "blacklist r8723au"  >>  /etc/modprobe.d/blacklist.conf
reboot
```
[COLOR=#000000][FONT=Verdana]
[COLOR=#222222][FONT=Verdana]Because i [/FONT][/COLOR]thought my last experience will change your reccomendatrion.[COLOR=#222222][FONT=Verdana] 

Should i?

Thank you a lot.[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by chili555 on 2015-01-27
I don't think it's a good idea to have two drivers, probably conflicting, loaded. Do you?```
lsmod | grep 8723
```

---

### Post by PaulFrmBrn on 2015-01-28
I don't, of course.

```
paulfrmbrn@paulfrmbrn-Lenovo-IdeaPad-Yoga-13:~$ lsmod | grep 8723
r8723au               598271  0 
cfg80211              510218  1 r8723au

```

---

### Post by chili555 on 2015-01-28
The native driver, not the one you compiled, is loaded. Let's see what it's doing behind the scenes:```
dmesg | grep -e 8723 -e 80211 | tail -n15
```

---

### Post by PaulFrmBrn on 2015-01-28
The output is:

```
paulfrmbrn@paulfrmbrn-Lenovo-IdeaPad-Yoga-13:~$ dmesg | grep -e 8723 -e 80211 | tail -n15
[    2.932241] Error: Driver 'rtl8723au' is already registered, aborting...
[    3.239818] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[    3.241518] RTL8723AU: Firmware Version 33, SubVersion 0, Signature 0x2302
[    5.148198] RTL8723AU: ERROR set ssid [YM] fw_state = 0x00000008
[    5.341411] RTL8723AU: ERROR start auth
[    5.373879] RTL8723AU: ERROR auth success, start assoc
[    5.389595] cfg80211: Calling CRDA for country: RU
[    5.391795] cfg80211: Regulatory domain changed to country: RU
[    5.391799] cfg80211:  DFS Master region: unset
[    5.391800] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    5.391803] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    5.391805] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (N/A, 3000 mBm), (N/A)
[    5.402194] RTL8723AU: ERROR send eapol packet
[    5.416091] RTL8723AU: ERROR send eapol packet
[    5.416414] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4

```

---

### Post by chili555 on 2015-01-28
We see errors; we don't like errors! Please execute the command above, blacklisting the native driver, reboot, and try again:```
dmesg | grep -e 8723 -e 80211 | tail -n15
```

---

### Post by PaulFrmBrn on 2015-01-28
Agree about errors :)

done:

```
sudo -i
echo "blacklist r8723au"  >>  /etc/modprobe.d/blacklist.conf
reboot
```

the output of 

```
dmesg | grep -e 8723 -e 80211 | tail -n15
```

is:

```
paulfrmbrn@paulfrmbrn-Lenovo-IdeaPad-Yoga-13:~$ dmesg | grep -e 8723 -e 80211 | tail -n15
[    3.533336] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.533338] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.533340] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.540607] RTL8723AU: ERROR indicate disassoc
[    3.558711] RTL8723AU: ERROR set bssid:00:00:00:00:00:00
[    3.558740] RTL8723AU: ERROR set ssid [g\xffffffc6isQ\xffffffffJ\xffffffec)&#890;\xffffffab\xfffffff2\xfffffffb\xffffffe3F|\xffffffc2T\xfffffff8xffffffe8\xffffffe7\xffffff8dvZ.c3\xffffff9f&#602;\xffffffcb\xffffffe2W7] fw_state=0x00000008
[    4.930950] RTL8723AU: ERROR set ssid [YM] fw_state=0x00000008
[    4.930976] RTL8723AU: ERROR set bssid:20:3a:07:18:40:d0
[    5.031311] RTL8723AU: ERROR start auth
[    5.071119] RTL8723AU: ERROR auth success, start assoc
[    5.078121] RTL8723AU: ERROR assoc success
[    5.090777] RTL8723AU: ERROR send eapol packet
[    5.097346] RTL8723AU: ERROR send eapol packet
[    5.097379] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4
[    5.098973] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:1

```

---

### Post by chili555 on 2015-01-28
Let's try a different driver altogether: ```
sudo apt-get install git
git clone https://github.com/lwfinger/rtl8723au.git
cd rtl8723au/
make
sudo make install
sudo reboot
```It makes with no warnings or errors on my 14.10 system.

Then let us see again:```
dmesg | grep -e 8723 -e 80211 | tail -n15
```We are very quickly running out of available options.

---

### Post by PaulFrmBrn on 2015-01-29
I've got already git installed.

These executed with no warnings or errors:


```
git clone https://github.com/lwfinger/rtl8723au.git
cd rtl8723au/
make
sudo make install
sudo reboot
```

The output of:

```
dmesg | grep -e 8723 -e 80211 | tail -n15
```

is:

```
[    3.519332] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.519334] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.519337] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.519339] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.537642] RTL8723AU: ERROR set bssid:00:00:00:00:00:00
[    3.537677] RTL8723AU: ERROR set ssid [g\xffffffc6isQ\xffffffffJ\xffffffec)&#890;\xffffffab\xfffffff2\xfffffffb\xffffffe3F|\xffffffc2T\xfffffff8xffffffe8\xffffffe7\xffffff8dvZ.c3\xffffff9f&#602;\xfffffffee6b] fw_state=0x00000008
[    4.908689] RTL8723AU: ERROR set ssid [gena] fw_state=0x00000008
[    4.908702] RTL8723AU: ERROR set bssid:c4:04:15:8e:b0:14
[    4.922952] RTL8723AU: ERROR start auth
[    4.925181] RTL8723AU: ERROR auth success, start assoc
[    4.929321] RTL8723AU: ERROR assoc success
[    4.934999] RTL8723AU: ERROR send eapol packet
[    4.942131] RTL8723AU: ERROR send eapol packet
[    4.942158] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4
[    4.943661] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:1

```

---

### Post by chili555 on 2015-01-29
I saw this: [https://github.com/lwfinger/rtl8723au/issues/17](https://github.com/lwfinger/rtl8723au/issues/17) Your exact errors and a few more are listed. The suggested fix resulted in:> So I've been using this for almost 2 weeks now. Haven't seen this issue since. Closing.Let's try:```
sudo -i
echo "options 8723au rtw_power_mgnt=0"  >  /etc/modprobe.d/8723au.conf
modprobe -r 8723au
modprobe 8723au
exit
```Improved? Same? Worse?

---

### Post by PaulFrmBrn on 2015-01-29
Great idea about power management!

[COLOR=#000000]This code executed with no warnings or errors:

[/COLOR]```
sudo -i
echo "options 8723au rtw_power_mgnt=0"  >  /etc/modprobe.d/8723au.conf
modprobe -r 8723au
modprobe 8723au
exit
```

But, unfortunately, situation is the same as i've described earlier

> [COLOR=#222222][FONT=Verdana]Transmition was showing 1.5-2.5 MB/s. speedtest utility - 16-20 Mbits/s too. for several requests[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]So it seemd fine. And this is strange - i did nothing since my first post in this thread.
Then i've found that if i reboot the laptop and start win8.1 (in windows no WiFi nwetwork could be found in this case) and then start Ubuntu once again WiFi connection will fall down to 0.3-0.4 Mbits/s. 
The only way to speed up the connection is to shut down the laptop for a while (5-10 seconds) and than start ubuntu. In this case speed will be normal (up to 25 Mbits/s).[/FONT][/COLOR]


The output of

```
dmesg | grep -e 8723 -e 80211 | tail -n15

```
is:

```
[    3.567008] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.567010] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.567012] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.574281] RTL8723AU: ERROR indicate disassoc
[    3.646227] RTL8723AU: ERROR set bssid:00:00:00:00:00:00
[    3.646264] RTL8723AU: ERROR set ssid [g\xffffffc6isQ\xffffffffJ\xffffffec)&#890;\xffffffab\xfffffff2\xfffffffb\xffffffe3F|\xffffffc2T\xfffffff8xffffffe8\xffffffe7\xffffff8dvZ.c3\xffffff9f&#602;d\xffffff99U\xffffffe0] fw_state=0x00000008
[    4.988371] RTL8723AU: ERROR set ssid [gena] fw_state=0x00000008
[    4.988385] RTL8723AU: ERROR set bssid:c4:04:15:8e:b0:14
[    5.073940] RTL8723AU: ERROR start auth
[    5.078548] RTL8723AU: ERROR auth success, start assoc
[    5.082681] RTL8723AU: ERROR assoc success
[    5.085394] RTL8723AU: ERROR send eapol packet
[    5.092752] RTL8723AU: ERROR send eapol packet
[    5.093405] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4

```

---

### Post by chili555 on 2015-01-29
> [    [COLOR="#FF0000"]5.093405[/COLOR]] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4The timestamp indicates that these happened in the first 5 seconds of the boot process. It would be more informative to see the same readings as the internet is connected but slowing down. Also, may I see:```
sudo iwlist wlan0 scan
```Strip away all but your network and obscure your details like this:> wlan0     Scan completed :
          Cell 01 - Address:[COLOR="#FF0000"]xx[/COLOR]:D7:19:41:54:[COLOR="#FF0000"]xx[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"[COLOR="#FF0000"]my_router[/COLOR]"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


---

### Post by PaulFrmBrn on 2015-01-30
[COLOR=#000000][FONT=Verdana][COLOR=#222222][FONT=Verdana]By saying this:[/FONT][/COLOR]

> [FONT=Verdana]It would be more informative to see the same readings as the internet is connected but slowing down. Also, may I see:[/FONT]

[COLOR=#222222][FONT=Verdana]you mean I need to get the info when when connection speed is low? if so, the output is:

[/FONT][/COLOR][/FONT][/COLOR]
```

[    3.478237] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.478239] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.478242] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.495727] RTL8723AU: ERROR indicate disassoc
[    3.515984] RTL8723AU: ERROR set bssid:00:00:00:00:00:00
[    3.516018] RTL8723AU: ERROR set ssid [g\xffffffc6isQ\xffffffffJ\xffffffec)&#890;\xffffffab\xfffffff2\xfffffffb\xffffffe3F|\xffffffc2T\xfffffff8xffffffe8\xffffffe7\xffffff8dvZ.c3\xffffff9f&#602;\xfffffff5\xffffffd9\xffffffca] fw_state=0x00000008
[    4.855963] RTL8723AU: ERROR set ssid [gena] fw_state=0x00000008
[    4.855977] RTL8723AU: ERROR set bssid:c4:04:15:8e:b0:14
[    4.963065] RTL8723AU: ERROR start auth
[    4.965427] RTL8723AU: ERROR auth success, start assoc
[    4.969569] RTL8723AU: ERROR assoc success
[    4.972176] RTL8723AU: ERROR send eapol packet
[    4.984777] RTL8723AU: ERROR send eapol packet
[    4.984816] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4
[    4.986411] RTL8723AU: ERROR set group key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:1

```
[COLOR=#000000][FONT=Verdana]
[COLOR=#222222][FONT=Verdana]The output of [/FONT][/COLOR]

[/FONT][/COLOR]```

sudo iwlist wlan0 scan
```[COLOR=#000000][FONT=Verdana]

[COLOR=#222222][FONT=Verdana]for my network is:[/FONT][/COLOR]

[/FONT][/COLOR]```

wlan0     Scan completed :
          Cell 01 - Address: xx:04:15:8E:B0:xx
                    ESSID:"router"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDA40050F204104A0001101044000102103B0001031047001063041253101920061228C404158EB0141021000D4E4554474541522C20496E632E102300174A574E5232303030763228576972656C657373204150291024000A4A574E523230303076321042000830303030303030301054000800060050F2040001101100174A574E5232303030763228576972656C657373204150291008000220081049000600372A000120
                    Quality=100/100  Signal level=72/100  

```

---

### Post by PaulFrmBrn on 2015-02-06
May be there is something else I can try to solve the problem?

---

### Post by chili555 on 2015-02-07
Let's first remove the ineffective driver parameter:```
sudo rm  /etc/modprobe.d/8723au.conf 
```Next, let's see if the native driver gives a better result:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```The last line should be:```
blacklist r8723au
```Remove the 'r' so it now reads:```
blacklist 8723au
```Proofread carefully, save and close gedit. Reboot. Is it better, worse or the same?

If worse, again post:```
dmesg | grep -e 8723 -e 80211 | tail -n15
```Thanks.

---

### Post by PaulFrmBrn on 2015-02-08
Thanks a lot for your reply!

After reboot my wifi adapter couldn't esatblish the connection. After second rebooot and switch off/in wifi adapter (programmatically in settings) connectiond established, speedtest shows normal speed.

The output of :

```
dmesg | grep -e 8723 -e 80211 | tail -n15
```

is:

```
[    2.864714] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    2.864717] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    2.864719] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    2.864722] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    2.864724] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    2.868835] r8723au: module is from the staging directory, the quality is unknown, you have been warned.
[    2.989368] usbcore: registered new interface driver rtl8723au
[    3.068997] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[    3.069994] RTL8723AU: Firmware Version 33, SubVersion 0, Signature 0x2302
[    5.030485] RTL8723AU: ERROR set ssid [gena] fw_state = 0x00000008
[    5.145471] RTL8723AU: ERROR start auth
[    5.148325] RTL8723AU: ERROR auth success, start assoc
[    5.155505] RTL8723AU: ERROR send eapol packet
[    5.160579] RTL8723AU: ERROR send eapol packet
[    5.169820] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4

```

---

### Post by chili555 on 2015-02-08
I don't much like the errors, but I do like this very much:> connectiond established, speedtest shows normal speed.So, are we solved?

---

### Post by PaulFrmBrn on 2015-02-08
```
[COLOR=#000000]I don't much like the errors, but I do like this very much:[/COLOR]
```

I do agree with you totally.

Tahnk you very much for your help and patience!

---

