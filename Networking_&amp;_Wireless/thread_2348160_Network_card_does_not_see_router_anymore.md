---
title: "Network card does not see router anymore"
date: 2017-01-01
forum: Networking &amp; Wireless
---

### Post by notsinglephoton on 2017-01-01
[COLOR=#111111][FONT=Ubuntu]Today I was working on some random stuff when suddenly windows asking me for password to my wifi connection. I had to miss-click something, as I was writing and window disappeared.
Now I can't connect to my main wifi router from my laptop. My network card:[/FONT][/COLOR]
```
lspci
Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
```
[COLOR=#111111][FONT=Ubuntu]stopped to seeing it. It sees, however other networks and can connect to them (but they are not comfortable to work with, I need my main).
When I use external wifi adapter, it works fine (but more usb cables on the desk = more mess). I can connect my mobile phone too.
I checked also booting from USB with xubuntu, but same situation, it looks like the issue is in blocked hardware.
I have tried to connect through command line, but:[/FONT][/COLOR]
```
iwlist wlan0 scan
```
[COLOR=#111111][FONT=Ubuntu]does not show up my wifi network.
I also tried[/FONT][/COLOR]
```
nmcli c up uuid <uuid>
```
[COLOR=#111111][FONT=Ubuntu]but it gives only:[/FONT][/COLOR]
```
Error: Connection activation failed.
```
[COLOR=#111111][FONT=Ubuntu]I've checked router settings, but didn't find anything wrong there - no MAC filtering or something like that.[/FONT][/COLOR]
```
rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

What looks very strange to me is:
```

#wpa_cli status wlan0
Selected interface 'wlx00c0ca826f3e'
bssid=xx:xx:xx:xx:xx:xx
freq=2467
ssid=NAME_OF_MY_LOST_WIFI_HERE
id=0
mode=station
pairwise_cipher=CCMP
group_cipher=CCMP
key_mgmt=WPA2-PSK
wpa_state=COMPLETED
ip_address=192.168.0.10x
p2p_device_address=yy:yy:yy:yy:yy:yy
address=yy:yy:yy:yy:yy:yy
uuid=<uuid number>

```Can it be blocked somehow? Can I reset those settings to get 'blank' wlan0 interface and then try to find connection?

---

### Post by gordintoronto on 2017-01-02
What version of Linux are you using? What is the output of ifconfig? Have you rebooted?

---

### Post by notsinglephoton on 2017-01-02
```
uname -a
Linux Unknown 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

```


```
ifconfig 
eth0      Link encap:Ethernet  HWaddr aa:aa:aa:aa:aa:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:422402 (422.4 KB)  TX bytes:422402 (422.4 KB)


wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


wlx00c0ca826f3e Link encap:Ethernet  HWaddr yy:yy:yy:yy:yy:yy 
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c081:b48d:872c:1456/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:671775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:385604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:905326692 (905.3 MB)  TX bytes:44178616 (44.1 MB)

```The last one is my external wifi adapter.
Yes, I did reboot few times, even tried on liveCD system, same issue.

---

### Post by jeremy31 on 2017-01-02
You may have issues with the internal broadcom card if the access point is on a channel higher than 11 in 2.4GHz

---

### Post by notsinglephoton on 2017-01-02
Wow, truly godlike solution. I changed in router conf website channel from 12 to 5 and it works again. Not sure why it stopped before, but thank you so much!

---

