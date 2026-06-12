---
title: "Wifi connection problem Ubuntu 15.10 Toshiba Satellite-L750"
date: 2015-12-26
forum: Networking &amp; Wireless
---

### Post by Don Martin on 2015-12-26
Hi,

I've read the sticky for this forum and updated my system.  However when I attempt to run the info script as indicated in the sticky, I get numerous "unable to resolve" messages, so can not create the info file.

I've just recently acquired the machine noted above.  When I attempt wifi connection, I enter my password, but it does not connect.  In a matter of seconds my password is requested again, repeatedly, and it never connects.

If anyone could help me with running the info collection script, or have any suggestions for solving the problem, I would appreciate it.

Don

---

### Post by praseodym on 2015-12-26
Please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
cat /etc/resolv.conf
route -n
```

---

### Post by Don Martin on 2015-12-26
Hard blocked: no
1: acer-wireless: Wireless Lan
Soft blocked: no
Hard Blocked: no
don@don - laptop: ~$ iwconfig
lo no wireless extensions
wlan  IEEE 802.11bgn ESSID:"Chelito"
mode:Managed  Frequency:2.417 GHz  Access Point:  68:7F:74:5D:57:9A
Bit Rate = 54 Mb/s  Tx-Poer=15dBm
Rx invalid nwid:0  Rxinvalid crypt:0  Rx invalid frag:0
Tx excessive retries:8 Invalid misc:471  Missed beacon:0

eth0   no wireless extensions

don@don - laptop: $ can /etc/rsolv.conf

I've realized I hit the post button with two output lines not included;

nameserver 127.0.0.1
search  no-domain-set-bellcanada

---

### Post by jeremy31 on 2015-12-27
An Acer module loaded on a Toshiba?  Let's try after blacklisting it
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by Don Martin on 2015-12-27
The computer I've been using with Ubuntu for the past five years is an Acer Gateway, and that is what is connected wireless now while I'm trying to get the Toshiba to work.  Does that explain anything?  Or should I still blacklist it?

---

### Post by chili555 on 2015-12-27
> **Don Martin said:**
> The computer I've been using with Ubuntu for the past five years is an Acer Gateway, and that is what is connected wireless now while I'm trying to get the Toshiba to work.  Does that explain anything?  Or should I still blacklist it?I'm confused. Are the readings you posted in post #3 from the working Acer or, as we expected, from the non-working Toshiba?

---

### Post by brian-mccumber on 2015-12-27
> **Don Martin said:**
> 
I've just recently acquired the machine noted above.  When I attempt wifi connection, I enter my password, but it does not connect.  In a matter of seconds my password is requested again, repeatedly, and it never connects.

This is acting just like it does when the wrong wifi password is entered. Are you entering your wifi password or your sudo password cause it should be the wireless password for the router.

---

### Post by Don Martin on 2015-12-27
Well I did the blacklist as suggested, but it has had no effect.  I'm still getting repeated requests for my wifi password, but no connection.

---

### Post by Don Martin on 2015-12-27
The readings in post #3 are from the non - working Toshiba.  I made a direct cable connection to the Toshiba to access the net, but since there are several other devices in use by other people, I then go back to the Acer for these posts.

---

### Post by Don Martin on 2015-12-27
Yes I'm using the wireless password for the router.

---

### Post by jeremy31 on 2015-12-27
Post ```
lspci -nnk | grep -iA2 net
``` from the Toshiba

---

### Post by Don Martin on 2015-12-27
02:00.0 Network controller [0280]; Realtek Semiconductor Co.; Ltd. RTL8188CE 802
.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
Subsytem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
Kernbel driver in use: rtl8192ce
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
Subsystem Toshiba America Info Systems Device [1179:fc50]
Kernel driver in use: atlic

---

### Post by jeremy31 on 2015-12-27
Try ```
echo "options rtl8192ce fwlps=N" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```

And it could be that your chipset doesn't like TKIP enabled networks like my Atheros, so check ```
iwlist scan | egrep -i 'ssid|cipher'
```
And check the group and pairwise ciphers under your networks name, you want to see CCMP only, no TKIP

---

### Post by Don Martin on 2015-12-27
Oh Oh!  On the first script I get a simple echo.  On the second I get TKIP on  both the Group and Pairwise Ciphers.  Is there anything to be done about this?

---

### Post by jeremy31 on 2015-12-27
Can you change the encryption settings on the router?  If you can, change it to WPA2 only, it might be called WPA2-PSK or WPA2-AES

Reboot router and computer

---

### Post by Don Martin on 2015-12-28
Hi Jeremy,  The router already indicates only WPA2 encryption.  Wikipedia indicates that TKIP started being disallowed on wireless devices back in 2010.  Does this likely mean that there is no way to use my Toshiba wirelessly?  I got the machine free so it isn't heartbreaking, and I can still use it with a hard connection in any case.

---

### Post by praseodym on 2015-12-28
Check if your router firmware could be updated.

---

### Post by Don Martin on 2015-12-28
Would an updated router accept TKIP?

---

### Post by jeremy31 on 2015-12-28
You want nothing to do with TKIP,  it is outdated an easy to hack.  WPA2 is a big improvement.

I don't use TKIP and my 12 year only Sony laptop worked well with my current network

---

### Post by Don Martin on 2015-12-28
Yes that is what I gathered when I looked up what it meant.  Do you know whether I can update the encryption protocol on the Toshiba?  I'm not sure where to go from here.

---

### Post by Don Martin on 2015-12-28
I've relocated the router so that I have the Toshiba hardwired and we all have wireless connection on our other machines.

---

