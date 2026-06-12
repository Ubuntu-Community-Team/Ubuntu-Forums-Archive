---
title: "Tired of failed wifi. Need tips to get good usb wifi."
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by pokipoki08 on 2008-06-19
After 2 weeks of trying to get my DLink DWL-G132 to work, I just give up on it.

I need some tips to buy a linux-friendly usb wireless card. Please advise on the brand, model, chipset or revision. Thanks.

---

### Post by kennedyjch on 2008-06-19
> **pokipoki08 said:**
> After 2 weeks of trying to get my DLink DWL-G132 to work, I just give up on it.

I need some tips to buy a linux-friendly usb wireless card. Please advise on the brand, model, chipset or revision. Thanks.

I was having difficulties with my NetGear WG111v2. It would automatically connect; then drop-out and I'd need to unplug the adapter and re-plug in.

I purchased the D-Link DWL-G132 and was disappointed that it did not "work out of the box'. However, I did use package manager to install the NDISWRAPPER graphic interface tool and was successful in usign it to install the WIndows driver that came with the card. Only complaint now is that it appears that for the network connection to become active, I must log-in to the PC. But no drop-outs and need to play with the adapter once it is up and running.

---

### Post by dmizer on 2008-06-19
> **pokipoki08 said:**
> After 2 weeks of trying to get my DLink DWL-G132 to work, I just give up on it.

I need some tips to buy a linux-friendly usb wireless card. Please advise on the brand, model, chipset or revision. Thanks.

i suggest starting here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

the above link is posted at the top of the networking & wireless forum.

---

### Post by pokipoki08 on 2008-06-19
My wireless config (WPA2) is here
[http://ubuntuforums.org/showthread.php?t=832669](http://ubuntuforums.org/showthread.php?t=832669)

I did connect with the DLink DWL-G132 but the connection will drop after a few minutes, but sometimes lasts about an hour.

[B][COLOR="RoyalBlue"]I followed someone's tip to boot up using the Hardy CDROM and tested the wifi connection.

uninstalled Network Manager
installed ndisgtk
installed windows driver (copied from system32 dir)
installed wicd[/COLOR][/B]
[B][COLOR="Red"]
And hey IT WORKS, even with WPA/WPA2!!! Best experience from Ubuntu just yet. Hassle free![/COLOR][/B]

Been testing the connection for 45 mins or so with wget, downloading large files. So far, the wifi is intact.

My question now :

[B]Why did the local hdd installation did not work?

Is it because I did the Updates?[/B]
[B][COLOR="Blue"]
For those using ndiswrapper, do a test run of wifi card with the CDROM![/COLOR][/B]

pokipoki08

---

### Post by pokipoki08 on 2008-06-19
This is very frustrating!

When I tested Hardy using the bootCD, wifi (WPA2) was working with ndiswrapper + wicd for almost 4 hours.

So, I did a fresh install of Hardy and followed the same steps as in the bootCD.

And now, it doesn't work anymore!!!

What is wrong with the distro??? It's now 5.30am and I just can't figure out, wth???

```


Steps that got wifi (wpa2) to work in the BootCD

remove network mgr
install ndis
install oem
install wicd

run wicd
unable to detect wlan0
sudo rmmod ndiswrapper
unplug dlink
plug in dlink
detected wlan0
run wicd, ensure wext wlan0 is set in preferences
disconnect network (eth0) in wicd
hall 1 wpa1/2
========================================
/etc/network/interfaces 
auto lo
iface lo inet loopback
========================================
no /etc/wpa_supplicant file
========================================
/opt/wicd/data/manager-settings.conf 
[Settings]
wireless_interface = wlan0
signal_display_type = 0
auto_reconnect = 1
window_height = 400
dns3 = None
dns2 = None
dns1 = None
wired_interface = eth0
window_width = 580
debug_mode = 0
global_dns_1 = None
global_dns_2 = None
global_dns_3 = None
wpa_driver = wext
use_global_dns = 0
wired_connect_mode = 1
always_show_wired_interface = 0
========================================
wired-settings.conf
empty
========================================
/opt/wicd/data/wireless-settings.conf 
[00:1E:52:78:CD:4F]
afterscript = None
bssid = 00:1E:52:78:CD:4F
ip = None
quality = 29
gateway = None
use_global_dns = False
strength = -77
encryption = True
beforescript = None
hidden = False
channel = 13
essid = Low TK Sports Hall 1
use_static_ip = False
has_profile = False
netmask = None
key = marisstella
enctype = wpa
dns3 = None
dns2 = None
dns1 = None
use_static_dns = False
encryption_method = WPA2
mode = Managed
disconnectscript = None
automatic = False
========================================

both eth0 & wlan0 are issued ip

removing eth0
sudo dhclient -r eth0
sudo ifconfig eth0 down
```

---

### Post by dmizer on 2008-06-19
please post the output of:
```
lshw -C network
```
and
```
lsmod
```

---

