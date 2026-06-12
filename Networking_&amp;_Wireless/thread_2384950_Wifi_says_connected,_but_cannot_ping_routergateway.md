---
title: "Wifi says connected, but cannot ping router/gateway or access internet"
date: 2018-02-14
forum: Networking &amp; Wireless
---

### Post by orangethaddeus on 2018-02-14
I'm having an issue on Xubuntu 16.04 where the network manager says I am connected to the wifi network, but I cannot access the internet or even ping the router/gateway ip. It doesn't do it all the time. Sometimes it works fine, sometimes it doesn't. Also it seems to fix when I reboot the router. I can connect fine from any other device and from the windows dual-boot. I've been forum crawling and have seen a lot of other people with similar problems, but I can't seem to find a solution.
It all worked fine until a few weeks ago. The only thing I can think of that I have changed in my system was that I ran "sudo apt autoremove".

Here is the output of running the 'wireless-info' script:
[http://paste.ubuntu.com/p/zCp9TTGP26/](http://paste.ubuntu.com/p/zCp9TTGP26/)

---

### Post by wyliecoyoteuk on 2018-02-19
Dual boot may be the issue, as it is an intermittent fault.
Many wifi cards load firmware on cold boot, which is not always flushed on a warm boot, so if you boot into Windows, then reboot into Linux, the firmware may be in an incorrect state. 
I have also seen this when windows updates the firmware and Linux has an older version.
Sometimes it goes the other way, i.e. Windows loses connectivity after a warm boot from Linux.
If you shut the PC down (i.e. power off) between boots does it work?

Also noticed it may be making an IPv6 connection instead of IPv4

---

### Post by orangethaddeus on 2018-02-19
Shutting down between seems to make no difference. Also, I hardly ever boot into windows.

---

### Post by fizikz on 2018-02-19
I'm having the exact same issue on Ubuntu (mate) 17.10 on a Live USB. [https://ubuntuforums.org/showthread.php?t=2385055](https://ubuntuforums.org/showthread.php?t=2385055)

Have you thought of any diagnostics?

I don't notice any errors in the system log. The most suspicious were messages like "systemd-resolved: Using degraded feature set for DNS server", and  "avahi-daemon: Joining mDNS multicast group on interface wlp2s0.IPv6 with address [...]" even though IPv6 is set to 'ignore' in Network Manager.

Is there any common point in network hardware/software or is this all due to Ubuntu? I'm using dd-wrt on both my wireless access point (TP-Link WR841N) and router (Netgear R7000).

My wild guess is the problem has something to do with systemd-resolved and resolv.conf setup, but really who knows. Considering how many people seem to have the same issue, I would have thought this would be addressed more actively.

---

### Post by wildmanne39 on 2018-02-19
Hi fizikz, please work in your thread and do not ask for support in someone else's, it creates confusion and is not fair to the person that started this thread, you can bump your thread once every twelve hours.

---

### Post by fizikz on 2018-02-20
Considering the problem the OP and I, and many others, have seems identical, I thought it would be helpful to combine efforts. But fine, to each their own thread.

---

### Post by wyliecoyoteuk on 2018-02-20
It does look like an IP v6 issue.
Have you tried setting a fixed IP v4 address for the wifi?

---

### Post by orangethaddeus on 2018-02-23
Fixed IP makes no difference.

---

### Post by Hadaka on 2018-02-23
Hi, there are a few issues that need addressing/correcting..

First the router is indeed communicating with the wifi card
as in noted by the router assigning an ip addtess -as seen below.

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0

**[COLOR=#ff0000]*[/COLOR]**BIOS Let's start the correction process by first going into bios
and disabling 'Secure boot'

[COLOR=#ff0000]*****[/COLOR]Router -Edit connections and DELETE all configurations to ssid Snowglobe
Snowglobe <MAC 'Snowglobe' [AC1]>  Infra  9 2452 MHz  54 Mbit/s  86 &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes *
wlp2s0  Cell 01 - Address: <MAC 'Snowglobe' -Group Cipher : TKIP - Pairwise Ciphers (2) : TKIP CCMP
```
Add back in ssid 'Snowglobe' wpa2 aes ccmp NO tkip
```

Please open a terminal ctrl/alt/t then Copy and Paste the following commands.

[COLOR=#ff0000]*****[/COLOR]Power Management is on and should be off
wlp2s0    IEEE 802.11abgn  ESSID:"Snowglobe"   Power Management on
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

[COLOR=#ff0000]*****[/COLOR]Country code is unsett-00
Region: America/New_York (based on set time zone) country 00 DFS-UNSET
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```

[COLOR=#ff0000]*****[/COLOR]ipv6 is set to auto- should be set to ignore
/etc/NetworkManager/system-connections/Snowglobe]] (600 root) [ipv6] method=auto
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Snowglobe
systemctl restart network-manager.service
```

***If after completing EVERY command and issues still esxist
Please post a NEW wireless report.
Thanks.

---

### Post by orangethaddeus on 2018-02-27
> **Hadaka said:**
> 
```
Add back in ssid 'Snowglobe' wpa2 aes ccmp NO tkip
```


Can you please clarify how to do this step?

---

### Post by orangethaddeus on 2018-03-06
Right. Well assuming I've done the above mentioned step correctly (which I haven't heard a response on yet), then I have done all that and the problem still persists. Here is the new wireless report:

[http://paste.ubuntu.com/p/fFNgZXfgS4/](http://paste.ubuntu.com/p/fFNgZXfgS4/)

---

### Post by Hadaka on 2018-03-06
Hi, from the latest wireless report, there are zero changes as per
the suggested commands to correct current configuration. Sorry
if i was not able to communicate in  a manner that you understand.
I have no further suggestions,good luck to you.

---

### Post by orangethaddeus on 2018-03-06
Can you not just explain to me what you mean by 
Add back in ssid 'Snowglobe' wpa2 aes ccmp NO tkip

?

---

### Post by chili555 on 2018-03-06
> **orangethaddeus said:**
> Can you not just explain to me what you mean by 
Add back in ssid 'Snowglobe' wpa2 aes ccmp NO tkip

?He means that your router Snowglobe says:> Cell 01 - Address: <MAC 'Snowglobe' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"Snowglobe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013f8c6c568
                    Extra: Last beacon: 434ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKHe hopes that you will check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

There are many instances of TKIP not working well at all and WPA2-AES working perfectly well.

I also would like to see, after you make these changes:```
sudo resolvconf -u
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by orangethaddeus on 2018-03-07
Thank you chili555. I have done what you said. It is working currently, but it always works after rebooting the router, so I'll have to wait and see.

Here is the result of those three commands:
```
thaddeus@k6000:~$ sudo resolvconf -u
thaddeus@k6000:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=60 time=9.49 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=60 time=67.0 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=60 time=8.07 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 8.072/28.191/67.007/27.453 ms
thaddeus@k6000:~$ ping -c3 www.ubuntu.com
PING www.ubuntu.com (91.189.89.110) 56(84) bytes of data.
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=1 ttl=51 time=91.8 ms
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=2 ttl=51 time=90.5 ms
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.110): icmp_seq=3 ttl=51 time=90.2 ms

--- www.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 90.228/90.870/91.813/0.681 ms


```

---

### Post by orangethaddeus on 2018-03-07
Also, can I ask what changing the regulatory domain actually does?

---

### Post by chili555 on 2018-03-07
> **orangethaddeus said:**
> Also, can I ask what changing the regulatory domain actually does?Certain frequencies; that is channels, are allowed in certain countries and not in others. For example, channels 12, 13 and 14 are not supposed to be used in the USA but are common in the EU countries. Here is a clue from:```
sudo iw reg get
``````
global
country US: DFS-FCC
	([COLOR="#FF0000"]2402 - 2472[/COLOR] @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

```When our wireless devices ask a router for an IP address, the router is supposed to say, roughly, I am in the US and I can give you channels 1-11, etc. Usually, our wireless devices are compliant and, even if they were sold in Germany or manufactured in China, they switch channels and connect. In a very few cases, they stumble.

Setting the regulatory domain explicitly just puts the router and the wireless device on the same page; speaking the correct frequency range. 

I don't honestly know if t helps in 5% of cases or 95% but it's easy and quick to do, so why not? I know that I have a USB wireless that refuses to connect without it, so I know that it helps.

---

### Post by orangethaddeus on 2018-03-22
The problem has not returned, so I believe the issue is fixed. Thank you to everyone.

---

