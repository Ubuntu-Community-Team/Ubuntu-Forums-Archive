---
title: "What basic config is needed for a wifi connection ?"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by robertak on 2006-11-23
Hello,
I cannot get wifi on my DELL laptop ( built-in LAN and WIFI cards). The wired ethernet works fine, but am really struggling with wifi.  

Can anyone tell me what should or should'nt be in the ifconfig.    

Do I have to have the wlan0 declared  ?  

I suspect this is a simple misconfiguration; I am not familiar enough with UBUNTU (Edgy) to tell. 

Also strange:  in XP my broadcom card is seen with a mac address ending in :8c and in UBUNTU it ends in :8d !!! 

Thanks for any help,  Robertak

---

### Post by Joe_CoT on 2006-11-23
It needs to be in your interfaces file. this is what my entry looks like:

```
iface ra0 inet dhcp
wireless-essid dd-wrt

auto ra0
```

if yours is wlan0, it'll be wlan0 instead of ra0. The wireless-essid is the essid of your network (you can run "iwlist scan" to get a list of them). There's wifi managers, like gnome network manager, etc, but i've always found hard-coding it easier and more reliable.

As for the mac address, unless you specifically overwrote it in ifconfig or interfaces, linux has the correct one. Odds are that windows is spoofing it (do you have a bridged connection in windows?)

---

### Post by Charles Hand on 2006-11-23
Wifi is a problematic area, so you can probably turn up a lot of information by searching for "dell wifi" on the ubuntu forums. When all else fails, you could install ndiswrapper and install the Windows driver for the wifi.

---

### Post by FrodoB on 2006-11-23
There are many different Broadcom chipsets out there in the bcm43xx series. You need to find out which one you have by using lspci and report to the forum what you have an also you will need to search the web for your particular model.  

I was able to get my bcm4311 working using ndiswrapper, which I usually do not like to use, but it does work well for this particular card.

Let the forum know what you find.

---

