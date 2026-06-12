---
title: "Suddenly Slow Wireless - Intel Centrino N 6235"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by victorbrca2 on 2014-02-16
I've been running 12.10 on my Asus ultrabook for a while, but since last week my wireless has become extremely slow. I have a tried a couple of solutions for iwlwifi that I found online (11n_disable=1 and bt_coex_active=0), but I can't seem to figure out what the issue is. When I boot into Windows 8 on the same machine my connection is fine, so I'm guessing an update must have changed something. 

Here's some info from my system:

```
# cat /etc/issue.net ; uname -a
Ubuntu 12.10
Linux asus-linux 3.5.0-45-generic #68-Ubuntu SMP Mon Dec 2 21:58:52 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```


```
# lspci -nnk | grep -iA2 net03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
	Kernel driver in use: iwlwifi
```


```
# cat /etc/modprobe.d/iwlwifi.conf # /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
```


```
# lsmod | grep iwiwlwifi               386882  0 
mac80211              535936  1 iwlwifi
cfg80211              206797  2 iwlwifi,mac80211
```


```
# rfkill list all2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
5: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```



```
# nm-tool 

NetworkManager Tool


State: connected (global)


- Device: wlan0  [1RADA] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        C4:85:08:42:1B:02


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    HR00126:         Infra, 00:24:01:29:42:9F, Freq 2457 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    BELL575:         Infra, 2C:E4:12:7D:A5:27, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2
    BELL999:         Infra, D8:6C:E9:29:1F:E1, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BELL471:         Infra, C8:CD:72:DB:95:3B, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2
    *1RADA:          Infra, 4C:72:B9:33:70:3B, Freq 2437 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             64.71.255.204
    DNS:             64.71.255.198
```


Timing on pinging google.ca
```
$ ping google.caPING google.ca (66.185.84.59) 56(84) bytes of data.
64 bytes from 66.185.84.59: icmp_req=1 ttl=59 time=105 ms
64 bytes from 66.185.84.59: icmp_req=2 ttl=59 time=986 ms
64 bytes from 66.185.84.59: icmp_req=3 ttl=59 time=1111 ms
64 bytes from 66.185.84.59: icmp_req=4 ttl=59 time=130 ms
64 bytes from 66.185.84.59: icmp_req=5 ttl=59 time=1230 ms
64 bytes from 66.185.84.59: icmp_req=6 ttl=59 time=238 ms
64 bytes from 66.185.84.59: icmp_req=7 ttl=59 time=1203 ms
64 bytes from 66.185.84.59: icmp_req=8 ttl=59 time=197 ms
64 bytes from 66.185.84.59: icmp_req=9 ttl=59 time=1139 ms
64 bytes from 66.185.84.59: icmp_req=10 ttl=59 time=143 ms
64 bytes from 66.185.84.59: icmp_req=11 ttl=59 time=1162 ms
64 bytes from 66.185.84.59: icmp_req=12 ttl=59 time=165 ms
64 bytes from 66.185.84.59: icmp_req=13 ttl=59 time=1127 ms
64 bytes from 66.185.84.59: icmp_req=14 ttl=59 time=141 ms
64 bytes from 66.185.84.59: icmp_req=15 ttl=59 time=1101 ms
64 bytes from 66.185.84.59: icmp_req=16 ttl=59 time=120 ms
64 bytes from 66.185.84.59: icmp_req=17 ttl=59 time=1250 ms
```


Timing on a name lookup
```
# date ; nslookup cbc.com ; dateSun Feb 16 14:56:19 EST 2014
Server:        127.0.1.1
Address:    127.0.1.1#53


Non-authoritative answer:
Name:    cbc.com
Address: 121.78.127.249


Sun Feb 16 14:56:21 EST 2014
```


```
# date ; nslookup yahoo.com ; date
Sun Feb 16 14:56:37 EST 2014
Server:        127.0.1.1
Address:    127.0.1.1#53


Non-authoritative answer:
Name:    yahoo.com
Address: 206.190.36.45
Name:    yahoo.com
Address: 98.138.253.109
Name:    yahoo.com
Address: 98.139.183.24


Sun Feb 16 14:56:40 EST 2014
```

Any help is appreciated. 

Thanks,Victor.

---

### Post by varunendra on 2014-02-16
> **victorbrca2 said:**
> ```

    *1RADA:          Infra, 4C:72:B9:33:70:3B, Freq 2437 MHz, Rate 54 Mb/s, Strength 48 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
```

Please try changing the encryption in the router to pure WPA2-AES (CCMP). No mixed mode, no TKIP. Save the change > reboot the router > retry the connection. Any improvement? If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by mikailornek on 2014-02-17
dear friends, my english is not good but i have lot of experince about this subject. This problem is not about wireless card or iwlwifi driver. &#304;t's about your modem or router settings. &#304;'ve tried everthing but i can not found a solution with drivers or special settings. &#304;ts so simple, open your modem or router interface and set to wireless settings to "auto", all channel and frequency settings.

---

### Post by victorbrca2 on 2014-02-18
Thanks for both replies. I have been doing some testing and it seems that is a modem/router issue. I'll play around with the settings that you both advised and see if it makes any difference. The weird part is that it used to work without any issues before... and it works with Windows 8.

Anyways, thanks for your time. 

Vic.

---

### Post by frankie3 on 2014-05-17
I let my self bump this thread a bit, 

It looks like I have something similar. For my Centrino Advanced-N 6235, 
Right now my router TL-WDR4300 with OpenWRT([http://wiki.openwrt.org/toh/tp-link/tl-wdr4300](http://wiki.openwrt.org/toh/tp-link/tl-wdr4300)), works perfectly fine with mac, not really with ubuntu. 

Tested with iperf 

```
 /tmp > iperf -c nas.local -t 10 -f m------------------------------------------------------------
Client connecting to nas.local, TCP port 5001
TCP window size: 0.08 MByte (default)
------------------------------------------------------------
[  3] local 192.168.1.218 port 43911 connected with 192.168.1.227 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  27.4 MBytes  22.8 Mbits/sec
[SIZE=2]
```[/SIZE]

[SIZE=2]Where nas.local is [/SIZE]arbitrary[SIZE=2] storage machine. 

Ubuntu laptop gives [/SIZE]**22.8 Mbits/sec **while laptop gives MacOS **215 ****Mbits/sec**. 
The difference is significant, and there is space to complain about.
 
I have similar feeling that victorbrca2 had, I remember seeing Samba sending files with 20MB/s (around 200Mbits/sec) at some point.  

I decided to use wireless_script to help myself with this issue, [http://pastebin.com/raw.php?i=5B6TdAwt](http://pastebin.com/raw.php?i=5B6TdAwt)[SIZE=2]  [/SIZE]

[SIZE=2]My current router [/SIZE]security WPA2-PSK AES. [SIZE=2] [/SIZE]

---

### Post by frankie3 on 2014-05-18
Just an update, for my case. I've tested every single encryption algorithm (WEP, WPA1/2, none). It doesn't look like encryption problem right now. 

Also funny fact discovered during tests. While laptop with Ubuntu with Centrino Advanced-N 6235 is performing really badly, it looks like that WPA2 TKIP is the best choice for laptop with MacOS.

---

### Post by varunendra on 2014-05-18
Can you try 2.4 GHz band in the router/access-point? The current 5 GHz band is usually helpful in areas where there is a congestion problem due to a lot of neighbouring APs working at same frequencies, and that doesn't seem to be a problem with you. Generally, the 2.4 GHz band has been reported to be working better with iwlwifi driver (or most of the Linux drivers). To see how to change the frequency band in the router, please refer to its user manual.

And regardless of the base for what you found, I have to disagree that "WPA2 TKIP" can be the 'best choice' for ANY wifi network, it is bad, if not the worst.

For now, please just try changing the frequency band to 2.4 GHz as suggested above, and if it doesn't seem to help, please follow the instructions in this post to run an experimental version of the wireless_script which provides much more (still safe) info about the wireless setup : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Please post back the fresh report generated by above new script in case the problem persists.

---

### Post by frankie3 on 2014-05-18
Ok I see, 

So I lied a bit in the wireless script output. I cut off those networks since I thought this won't be relevant to the problem. 
 
I have plenty 2.4 Ghz networks around this why I'm using 5 Ghz. 2.4 is out of the question for me, interference is so huge that I'm losing packets while using ping to router. 

Thanks for your interested and here is the output from the script

- **5 Ghz** [http://pastebin.com/raw.php?i=0JhrGiv9](http://pastebin.com/raw.php?i=0JhrGiv9)

```

 /tmp > iperf -c nas.local -t 10 -f m
------------------------------------------------------------
Client connecting to nas.local, TCP port 5001
TCP window size: 0.08 MByte (default)
------------------------------------------------------------
[  3] local 192.168.1.218 port 41453 connected with 192.168.1.227 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  27.6 MBytes  23.0 Mbits/sec
```

- **2.4 Ghz** [http://pastebin.com/raw.php?i=ySbXa4Zn]("http://paste.pound-python.org/show/y2UY35HkRh45nLaDq76X/")

```

 /tmp > iperf -c nas.local -t 10 -f m
------------------------------------------------------------
Client connecting to nas.local, TCP port 5001
TCP window size: 0.08 MByte (default)
------------------------------------------------------------
[  3] local 192.168.1.218 port 41552 connected with 192.168.1.227 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  24.6 MBytes  20.6 Mbits/sec
```

---

### Post by varunendra on 2014-05-18
When did you apply "11n_disable=1" parameter? That is meant to disable 'N' channel support on the driver, limiting it to 54 Mbps or less speed. Please remove that parameter if you want 'N' channel support (speeds higher than 54 Mbps)-
```
sudo sed -i '/11n_disable/ d' /etc/modprobe.d/iwlwifi.conf
```
..followed by a reboot.

An explanation of some of the common iwlwifi driver parameters : [http://ubuntuforums.org/showpost.php?p=12943350](http://ubuntuforums.org/showpost.php?p=12943350)

---

### Post by frankie3 on 2014-05-18
It had to be somewhere between: try all the things (found on the Internet) related to the Intel Centrino N 6235 and Ubuntu and now. But, to the point. 

Removed the "11n_disable=1" parameter, the proof [http://pastebin.com/raw.php?i=gAm8TUnV](http://pastebin.com/raw.php?i=gAm8TUnV)

Now iperf looks slightly better, but way bellow expected performance.  
 
```

 /tmp > iperf -c nas.local -t 20 -f m
------------------------------------------------------------
Client connecting to nas.local, TCP port 5001
TCP window size: 0.08 MByte (default)
------------------------------------------------------------
[  3] local 192.168.1.218 port 41048 connected with 192.168.1.227 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-20.0 sec  83.8 MBytes  35.0 Mbits/sec

```

---

### Post by varunendra on 2014-05-20
Please try "bt_coex_active=N" and "swcrypto=1" parameters as suggested in the link I posted earlier.

---

### Post by Lekensteyn on 2014-06-16
Frankie, you are running a newer kernel than OP, I think you have different issues. At some point (Linux v3.13-10103-g205e221, will end up in 3.14 and newer), AMPDU was disabled for iwldvm devices ("iwlwifi: disable TX AMPDU by default for iwldvm"). For me, that caused a performance drop from about 80 Mbit/s to about 20 Mbit/s (measured with iperf).

Saucy users are affected if they have upgraded their kernel to at least 3.11.10.8: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1311196](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1311196)
I couldn't find if 3.13 are affected, but if Ubuntu patched their kernel to include this change, then you will also need to apply the below configuration.

To test whether you are affected, check whether you are actually using the iwldvm module (and not iwlmvm):
```
$ lsmod | grep iwlwifi
iwlwifi               178135  1 iwldvm
cfg80211              521351  3 iwlwifi,mac80211,iwldvm
```

If you are indeed using iwldvm, is your module affected? Affected kernels will have a bitmap option with option 8:
```
$ modinfo iwlwifi  | grep 11n_disable
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
```

To restore previous behavior (and alleviate the performance regression), create **/etc/modprobe.d/iwlwifi.conf** (exact filename does not matter, you could also chose modprobe.conf if you would like) containing **options iwlwifi 11n_disable=8**. Or, if you do not know what I am talking about, just run the command:
```
echo options iwlwifi 11n_disable=8 | sudo tee /etc/modprobe.d/iwlwifi.conf
```

Reload the module (**sudo modprobe -vr iwldvm iwlwifi && sudo modprobe -v iwlwifi**) or reboot.

---

### Post by finknottle2 on 2014-07-23
> **Lekensteyn said:**
> Frankie, you are running a newer kernel than OP, I think you have different issues. At some point (Linux v3.13-10103-g205e221, will end up in 3.14 and newer), AMPDU was disabled for iwldvm devices ("iwlwifi: disable TX AMPDU by default for iwldvm"). For me, that caused a performance drop from about 80 Mbit/s to about 20 Mbit/s (measured with iperf).

Saucy users are affected if they have upgraded their kernel to at least 3.11.10.8: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1311196](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1311196)
I couldn't find if 3.13 are affected, but if Ubuntu patched their kernel to include this change, then you will also need to apply the below configuration.

To test whether you are affected, check whether you are actually using the iwldvm module (and not iwlmvm):
```
$ lsmod | grep iwlwifi
iwlwifi               178135  1 iwldvm
cfg80211              521351  3 iwlwifi,mac80211,iwldvm
```

If you are indeed using iwldvm, is your module affected? Affected kernels will have a bitmap option with option 8:
```
$ modinfo iwlwifi  | grep 11n_disable
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
```

To restore previous behavior (and alleviate the performance regression), create **/etc/modprobe.d/iwlwifi.conf** (exact filename does not matter, you could also chose modprobe.conf if you would like) containing **options iwlwifi 11n_disable=8**. Or, if you do not know what I am talking about, just run the command:
```
echo options iwlwifi 11n_disable=8 | sudo tee /etc/modprobe.d/iwlwifi.conf
```

Reload the module (**sudo modprobe -vr iwldvm iwlwifi && sudo modprobe -v iwlwifi**) or reboot.


Thanks. This really helped. I have a dual boot system, and windows' speedtest results were almost twice as fast for me. I could hit 100Mbps on windows, but would stay at 60ish on ubuntu. I don't know if this will affect the stability, but I'm glad I found this. Also, it's particularly difficult to find information like this because there are a large no. of posts recommending 11n_disable=1. I guess most people are limited by their ISP's bandwidth and hence don't notice this.

---

### Post by varunendra on 2014-07-24
> **finknottle2 said:**
> Also, it's particularly difficult to find information like this because there are a large no. of posts recommending 11n_disable=1.

That's because most of the posts were written before the additional values (other than 0 and 1) were introduced in the driver. And even the current posts often suggest that because most of them are copied suggestions, not from someone who notices the changes and likes tinkering (even I missed those additional values for quite some time, despite my curious nature).

But above all, cooperation and confirmations from users like you are vital, because we usually have no other way to know what is helpful and what is not. So.. a big thanks for your feedback! :)

---

### Post by Paper Bag on 2014-09-05
Above **11n_disable=8** cured my issue too on Centrino 2230 / Ubuntu 14.04. Now it at least just and just matches what Win7 gives me as downstream, 70-80Mbps (still not near the maximum I get from a wired connection, but I guess that's up to the crappy router throughput or then this card is simply weak on Windows too). Without this trick downstream is maximum 30-40 Mbps. I knew there was something going on because Fedora 20 gave better results (Fedora / 3.11.10-301.fc20.x86_64, Ubuntu / 3.13.0-32-generic, same firmware: 18.168.6.1)

On the other hand, additionally **bt_coex_active=N** seemed to lower the downstream again below 40 Mbps and first when I tried that together with **swcrypto=1**, downstream was below 20Mbps. Not sure what was up with that, because swcrypto=1 alone didn't make a difference.

130Mbps is the maximum connection speed I get (on Windows too, again my router is probably the reason), on 802.11n, altough on Ubuntu it seems to usually drop to 64-78 Mbps.

* Downstream = repeated speedtest.net tests, always same server.

---

### Post by varunendra on 2014-09-06
Thanks for the detailed feedback Paper Bag, much appreciated!

The **bt_coex_active=N** parameters disables an advanced technique in the driver that tries to let both bluetooth and wifi signals work simultaneously without interfering with each other. I don't know exactly how it is implemented, but sometimes that added complexity to the wifi communication method causes troubles. Although obviously it is developed to actually 'help' in a _particular situation_.

So my guess is that either the technique has just matured in current drivers, or that you are using bluetooth simultaneously (on this very same laptop, or on other devices around) which starts interfering with the wifi signal with this feature disabled, thus resulting in bad quality signal and lower speeds.

---

