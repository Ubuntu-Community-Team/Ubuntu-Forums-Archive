---
title: "Wireless ndiswrapper from prompt"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by knj on 2008-02-24
Hi all.

I have a medie-center, which I want to bring on my wireless network. I have bought a Netgear WN121T USB-adapter, which I have installed using ndiswrapper. The is working fine with nm-applet. I can connect to my other machines and the internet.

If I try to get it up using the command-line, it doesnt.

I have tried to set it up with these commands:
```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid myessid enc myenc
```

Another "sudo iwconfig wlan0" gives me:
```
          wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated
          Bit Rate:300 Mb/s   Sensitivity=-200 dBm
          RTS thr=2346 B   Fragment thr=2346 B
          Encryption key:[removed]        Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


I found this in my syslog, when I tries to set it up via iwconfig:
```
Feb 24 13:11:20 knj-medie kernel: [ 2000.900000] ndiswrapper: driver wn121t (Marvell,09/29/2006,1.0.3.7) loaded
Feb 24 13:11:21 knj-medie kernel: [ 2001.668000] wlan0: ethernet device 00:1b:2f:c7:1b:23 using NDIS driver: wn121t, version: 0x1000206, NDIS version: 0x501, vendor: '', 0846:7100.F.conf
Feb 24 13:11:21 knj-medie kernel: [ 2001.668000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Feb 24 13:11:21 knj-medie NetworkManager: <debug> [1203855081.553484] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1b_2f_c7_1b_23').
Feb 24 13:11:21 knj-medie kernel: [ 2001.728000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 24 13:11:21 knj-medie NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'.
Feb 24 13:11:21 knj-medie NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
Feb 24 13:11:21 knj-medie NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
Feb 24 13:11:21 knj-medie NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'.
Feb 24 13:11:21 knj-medie NetworkManager: <info>  Deactivating device wlan0.
Feb 24 13:11:21 knj-medie NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument
```


I also find it in dmesg:
```
[   21.488000] NET: Registered protocol family 10
[   21.488000] lo: Disabled Privacy Extensions
[   21.492000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.416000] NET: Registered protocol family 17
[   45.068000] eth0: no IPv6 routers present
[   81.104000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```


What is wrong? I am using WEP as encryption, and I am connecting with WEP through NetworkManager as well...

---

### Post by spd106 on 2008-02-25
My first thought was that you were perhaps entering the key wrong, you need to use the hex version or use ascii, but prefix it with a "s:".
e.g.
```
sudo iwconfig wlan0 essid myessid enc 6d79656e63
sudo iwconfig wlan0 essid myessid enc s:myenc
```

But then by the looks of your iwconfig output you're not even associating with the AP. Are you able to see the AP in a scan?
```
sudo iwlist wlan0 scan
```

---

### Post by knj on 2008-02-28
Well. The scanning from the prompt via iwlist works just fine - I find every network nearby.

I have tried with enc as well. The key is not a passphrase, but I have tried anyway (out of desperation).

I has really begun to annoy me :'-(

---

### Post by kevdog on 2008-02-28
Take a look at this post, I'm not sure if it will help you, possibly:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by knj on 2008-03-03
kevdog, I have already been there and done that :'-(

---

### Post by unutbu on 2008-03-03
knj, just to isolate the problem, you might want to turn off WEP on your router, and move your computer (or your router) so the two are right next to each other. After you get a working connection, then try adding WEP back on.

Also, after you have tried changing your configuration (see below), you might want to  
power off and then reboot your computer. I find some changes to the system do not seem to work until after a real power off (not even a soft reboot works). 

Also, instead of typing in

```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid myessid enc myenc

```

have you edited /etc/network/interfaces? It should look something like this:

iface wlan0 inet dhcp
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key myenc
wireless-essid myessid
auto wlan0

Then you can try bringing up the interface with

```

sudo ifup wlan0

``` or

```
/etc/init.d/networking restart
```

or try the commands in
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
again after you have turned off WEP, put the computer and router physically next to each other, and do a power off/reboot. It's a pain, but it works.

---

