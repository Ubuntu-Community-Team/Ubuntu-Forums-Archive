---
title: "no Internet connection though connected to router"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by raneko on 2013-11-05
Hi,

I have a HP Pavilion Sleekbook, and I can connect to internet almost anywhere - just not at home. I have an Xfinity Comcast router, and it seems to me that my laptop is connecting to the router, but not to the internet. The router does assign an IP address to my machine, but when I try to ping 8.8.8.8 or [www.google.com]("http://www.google.com"), I get no reply. When I ping the router or my own IP address, everything is fine. I can also connect to the router through my browser, but it does not show my laptop as connected to it.
The issue is always the same, whether I connect through cable or wireless makes no difference.

This is the output of some basic commands after I connected to the router through wireless:

---ifconfig:

> eth0      Link encap:Ethernet  HWaddr 84:34:97:80:12:9e  
          inet6 addr: fe80::8634:97ff:fe80:129e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:280465 (280.4 KB)  TX bytes:282114 (282.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130967 (130.9 KB)  TX bytes:130967 (130.9 KB)


wlan0     Link encap:Ethernet  HWaddr 20:68:9d:ca:27:80  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:0:af80:443:2268:9dff:feca:2780/64 Scope:Global
          inet6 addr: fe80::2268:9dff:feca:2780/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38141 (38.1 KB)  TX bytes:133306 (133.3 KB)
[COLOR=#000000]
[/COLOR]
----route -n:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

To me it seems that there is an entry missing in the routing table, but I could not quite solve it.

As I said, pinging something outside my network, using name or IP address does not work, so I don't think it's an DNS related issue.
I also tried adding my machine to the router network with a reserved IP address, but that does not work either.

ping 10.0.0.1 and ping 10.0.0.6 works.

Any help would be greatly appreciated.

---

### Post by varunendra on 2013-11-06
Welcome to the forums raneko ! :)

Please edit your above post to wrap the codes within 'Code' tags. Follow the "Using Code Tags" link in my signature to see how. It will preserve its formatting, making it much more readable.

You seem to have been assigned an IPv6 address (probably by your router?) -
```
wlan0 Link encap:Ethernet HWaddr 20:68:9d:ca:27:80 
inet addr:10.0.0.6 Bcast:10.0.0.255 Mask:255.255.255.0
**inet6 addr: 2601:0:af80:443:2268:9dff:feca:2780/64 Scope:Global**
inet6 addr: fe80::2268:9dff:feca:2780/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:258 errors:0 dropped:0 overruns:0 frame:0
TX packets:1093 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:38141 (38.1 KB) TX bytes:133306 (133.3 KB)
```

It is not bad, instead good in many ways, but unfortunately it is not yet supported everywhere. If your ISP does not yet support IPv6, it may be the reason of your problem.

Please set "IPv6" to "Ignore" in Network Manager *(Network Manager Icon drop-down menu > "Edit Connections..." > "Wireless" tab > "Edit" your connection > "IPv6 Settings" tab > set "Method" to "Ignore")*, then try again.

You can also permanently disable it following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

If that does not help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by raneko on 2013-11-06
Hi Varun,

thanks for your suggestions. I will try tonight at home and then post the results..

---

### Post by raneko on 2013-11-07
I've tried disabling IPv6, but it did not seem to help. Here's the output of the wireless script (see attachment) -

again thanks for your help, this has really been bugging me for weeks now and I really don't know how to resolve it!!

---

### Post by varunendra on 2013-11-08
Sorry for a late response. I'm out of home (travelling), hardly getting time to check on the forums.

Based on the report, please try these (one by one, or all of them together if required) -

1) Try turning off the power management on the interface -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
Does the "Power Management" appear to be "off"? Does it help connecting? If not, try next (while keeping this change we just did) -

2) Try changing the channel from 6 to 1 or 11 in the router. These usually work better with Linux drivers, and besides, there seem to be many access-points around using channel 6, possibly causing too much interference.

3) If the above two don't help, try an old trick along with the above changes -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
Can you connect now? This would be a temporary change (will be lost at next boot) which we'll make permanent if it helps.

If none of these help, please post the outputs of (while having the above changes effective) -
```
grep -R [[:alnum:]] /sys/module/ath9k/parameters
nm-tool
iwconfig
dmesg | egrep -i 'ath9k|network'
```

---

### Post by raneko on 2013-11-08
Thanks, I'll try them at home!

---

### Post by raneko on 2013-11-08
Ok, I tried your suggestions but unfortunately it did not help. As I said, this problem only occurs with my Xfinity router, at work and at any other place I can connect to wireless.

Here are the outputs:

grep -R [[:alnum:]] /sys/module/ath9k/parameters
> 
/sys/module/ath9k/parameters/enable_diversity:0/sys/module/ath9k/parameters/blink:0
/sys/module/ath9k/parameters/nohwcrypt:1
/sys/module/ath9k/parameters/btcoex_enable:0


nm-tool
> 
NetworkManager Tool

State: connected (global)

- Device: wlan0  [home] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        20:68:9D:CA:27:80

Capabilities:
    Speed:           9 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    2WIRE142:        Infra, 28:16:2E:F9:E8:79, Freq 2452 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    beatrice:        Infra, 00:1D:7E:41:B7:E6, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    Cyberslum:       Infra, 08:86:3B:45:00:5E, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Immoral-Den:     Infra, 00:26:F2:9C:3E:96, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    HOME-1CF8:       Infra, B8:9B:C9:41:1C:F8, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    ATT8773:         Infra, 74:44:01:1A:FC:BE, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Cisco24983:      Infra, C0:C1:C0:82:F0:7E, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    2WIRE899:        Infra, C0:83:0A:43:DC:E9, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ATT129:          Infra, 98:2C:BE:F7:B9:6E, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    vistamount:      Infra, 44:32:C8:CB:E4:70, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    cyberslum.guest: Infra, 08:86:3B:45:00:5F, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    *HOME-CBD2:      Infra, 00:1D:D3:49:CB:D0, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2

  IPv4 Settings:
    Address:         10.0.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        84:34:97:80:12:9E

Capabilities:
    Carrier Detect:  yes

Wired Properties
    Carrier:         off


iwconfig
> 
lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"HOME-CBD2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:D3:49:CB:D0   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0




dmesg | egrep -i 'ath9k|network'
> 
[   19.108594] type=1400 audit(1383964806.431:3): apparmor="STATUS" operation="profile_load" parent=408 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=409 comm="apparmor_parser"
[   19.108726] type=1400 audit(1383964806.431:6): apparmor="STATUS" operation="profile_replace" parent=362 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   19.109148] type=1400 audit(1383964806.431:8): apparmor="STATUS" operation="profile_replace" parent=408 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=409 comm="apparmor_parser"
[   19.109312] type=1400 audit(1383964806.431:10): apparmor="STATUS" operation="profile_replace" parent=362 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   68.666370] ath9k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  178.291325] ath9k: ath9k: Driver unloaded
[  204.542198] ath9k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  208.042877] ath9k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use


Thanks!

---

### Post by varunendra on 2013-11-09
> **raneko said:**
> ```
[ 208.042877] ath9k 0000:01:00.0 **wlan0: disabling HT/VHT [COLOR="#FF0000"]due to WEP/TKIP use[/COLOR]**
```
How did I miss that earlier? Guess the word "WPA2" tricked me.

Can't say for sure if this will fix the problem, but WPA2+TKIP is one of the weirdest settings that *some* routers allow. As much as I know, you shouldn't even get the choice to use "TKIP" with WPA2 (its standard use is only with WPA or WPA/WPA2 mixed mode). *(a small discussion about it [post=12817442]here[/post], if you're interested)*

Anyway, without discussing unnecessary details, please change the encryption in the router to **WPA2-PSK with [COLOR="#0000CD"]AES/CCMP[/COLOR]**. No WEP, no WPA(1), no WPA/WPA2 mixed mode, and definitely not TKIP.

If that does not help, there is another parameter you may try, temporarily of course, to be made permanent if helps -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k enable_diversity=1
```
This parameters seems to be specifically meant for AR9565 cards (while yours is AR9485), so this may be more of a 'trying luck' rather than a logical approach, but let's just try it as there is no harm in trying.

---

### Post by raneko on 2013-11-09
Thank you for your suggestions!
I set the wireless security to WPA2PSK-AES, but no change :-(

I also tried the modprobe commands, but no improvement either..

I will also contact Comcast about it, in the end it is their router, I just have the feeling that it may not be very helpful. But I will try nonetheless..

Thank you very much for your help. If you have any other ideas, I would gladly try it!

Is there a way maybe to fix the routing table manually, by adding a route?

---

### Post by varunendra on 2013-11-09
Quick reply, before getting busy for the day -
> **raneko said:**
> Is there a way maybe to fix the routing table manually, by adding a route?

What route do you wish to add? If you don't know already, the command for manually adding routes to existing routing table is "**route add <desired route>**". Check "man route" for details with a few examples, or post back what kind of route you wish to try (to which network/host, what scope etc.).

---

### Post by raneko on 2013-11-10
I though maybe one could add a specific(static) route for 10.0.0.11?
Something like 
route add -net [COLOR=#000000]10.0[/COLOR][COLOR=#000000].0.11[/COLOR] netmask [COLOR=#000000]255.255[/COLOR][COLOR=#000000].255[/COLOR][COLOR=#000000].0[/COLOR] gw [COLOR=#000000]10.0.0.1
[/COLOR]

---

### Post by steeldriver on 2013-11-10
what exactly do you think is wrong with your routing table?

---

### Post by varunendra on 2013-11-10
> **steeldriver said:**
> what exactly do you think is wrong with your routing table?

Yup, I'd like to know that too, with an output of -
```
route -n
```

---

### Post by raneko on 2013-11-10
I'm not sure, I just thought adding a specific route for my reserved IP might help. 

route -n returns

> 
[COLOR=#000000]*Kernel IP routing table*[/COLOR]
[COLOR=#000000]*Destination Gateway Genmask Flags Metric Ref Use Iface*[/COLOR]
[COLOR=#000000]*0.0.0.0 10.0.0.1 0.0.0.0 UG 0 0 0 wlan0*[/COLOR]
[COLOR=#000000]*10.0.0.0 0.0.0.0 255.255.255.0 U 9 0 0 wlan0*[/COLOR]


---

