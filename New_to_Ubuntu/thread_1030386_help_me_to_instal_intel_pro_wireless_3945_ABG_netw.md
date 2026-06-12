---
title: "help me to instal intel pro wireless 3945 ABG network connection"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by acho1 on 2009-01-04
i'm new user ubuntu 8.10 gnome i instal it in my notebook and i have problem with the wlan.the type is intel pro wireless ABG network connection.so pleas help me......

---

### Post by stderr on 2009-01-04
intel3945abg should be able to use the inbuilt iwl3945 kernel module, so you should be OK there. What's the problem exactly?

If you could also run the following in a Terminal (Applications -> Accessories -> Terminal) and post the output here:

```
ifconfig
```

```
iwconfig
```

```
lsmod | grep iwl3945
```

You should be able to configure your wireless network under System -> Preferences -> Network Configuration. Click on the Wireless tab, and click Add... enter your network name under SSID and if you have enabled any wireless security on your wireless router (which you should have...) you can choose WEP/WPA etc under the Wireless Security tab, and enter the relevant password/code.

---

### Post by Ickam on 2009-01-23
Hello! My 3945 seems to be installed because I can browse the web, but websites are loading slower than on Windows. Moreover my wifi led is blinking. Laptop model is HP 530.
```
ick@ick:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:18:35:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:09:2f:36  
          inet addr:12.168.1.101  Bcast:12.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe09:2f36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:10945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11737139 (11.7 MB)  TX bytes:1143192 (1.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-09-2F-36-66-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ick@ick:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Marek"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:21:29:75:8D:84   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=74/100  Signal level:-60 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ick@ick:~$ lsmod | grep iwl3945
iwl3945                98804  0 
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211

```
Any ideas?

---

### Post by stchman on 2009-01-23
> **acho1 said:**
> i'm new user ubuntu 8.10 gnome i instal it in my notebook and i have problem with the wlan.the type is intel pro wireless ABG network connection.so pleas help me......

The Intel 3945ABG should work OOB.

---

### Post by Ickam on 2009-01-24
> **stchman said:**
> The Intel 3945ABG should work OOB.

But it doesn't work properly.

---

### Post by Locutus_of_Borg on 2009-01-24
looks like it is working

try this:
```
sudo -i
ifconfig wlan0 up
iwlist wlan0 scan
```

what happens?

---

### Post by Ickam on 2009-01-24
```
ick@ick:~$ sudo -i
[sudo] password for ick: 
root@ick:~# ifconfig wlan0 up
root@ick:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:75:8D:84
                    ESSID:"Marek"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=73/100  Signal level:-61 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000148f480177
                    Extra: Last beacon: 8ms ago
          Cell 02 - Address: 00:40:F4:F6:FA:66
                    ESSID:"default"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level:-85 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000163345317e
                    Extra: Last beacon: 2220ms ago
          Cell 03 - Address: 00:17:9A:57:B8:45
                    ESSID:"nic"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000c938bcf16f
                    Extra: Last beacon: 2612ms ago
          Cell 04 - Address: 00:1E:37:11:38:C8
                    ESSID:"neostrada_7889"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000003678ec186
                    Extra: Last beacon: 1816ms ago


```

---

### Post by ken22 on 2009-01-24
Please ensure that the restricted driver is enabled.

System > Admin > Restricted Drivers.

---

### Post by Locutus_of_Borg on 2009-01-25
> **Ickam said:**
> ```
ick@ick:~$ sudo -i
[sudo] password for ick: 
root@ick:~# ifconfig wlan0 up
root@ick:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:75:8D:84
                    ESSID:"Marek"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=73/100  Signal level:-61 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000148f480177
                    Extra: Last beacon: 8ms ago
          Cell 02 - Address: 00:40:F4:F6:FA:66
                    ESSID:"default"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level:-85 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000163345317e
                    Extra: Last beacon: 2220ms ago
          Cell 03 - Address: 00:17:9A:57:B8:45
                    ESSID:"nic"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000c938bcf16f
                    Extra: Last beacon: 2612ms ago
          Cell 04 - Address: 00:1E:37:11:38:C8
                    ESSID:"neostrada_7889"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000003678ec186
                    Extra: Last beacon: 1816ms ago


```
obviously it is working just fine as you are able to scan for wireless signals, what more are you wanting it to do?

to connect to one of those signals use iwconfig
or easier, just use the nm-applet that should be in your taskbar already

---

### Post by Ickam on 2009-01-25
I am connected, but sites are loading pretty long. I've tried FF, Epiphany, Opera, I've changed DNS'es but performance is slower than on Windows. Can't it be any better?

---

### Post by kyeh on 2009-01-25
This thread may help you:

[http://ubuntuforums.org/showthread.php?t=887046](http://ubuntuforums.org/showthread.php?t=887046)

It helped me solve my 3945 wireless problems, in particular look at the posts by chili555 ;)

My problem was solved when i disabled hw scan, i believe this was a pretty widespread bug.

---

### Post by Ickam on 2009-01-25
So you type
```
sudo rmmod iwl3945
sudo modprobe iwl3945
```
all the time? It's seems to be helpful for me, but kidna anoying

---

### Post by ieshadover on 2009-01-25
I still just want to cry, is there no help for true newbie to the system.

---

### Post by ken22 on 2009-01-25
I still don't see why the restricted drivers don't work. They've worked fine under Ubuntu for 3 years now.

---

