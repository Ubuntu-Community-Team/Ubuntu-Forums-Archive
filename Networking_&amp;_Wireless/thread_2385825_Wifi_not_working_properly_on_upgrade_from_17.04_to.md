---
title: "Wifi not working properly on upgrade from 17.04 to 17.10"
date: 2018-02-25
forum: Networking &amp; Wireless
---

### Post by vincentertainment on 2018-02-25
I also can't browse after upgrading to 17.10. It seems like a DNS issue but assigning static DNS vales doesn't resolve it.
Here is my Wireless Info Script output: [https://pastebin.com/GftaKVLH](https://pastebin.com/GftaKVLH)
Chrome gives the error _______'s server IP address could not be found. I can't ping google.com, but I can ping 8.8.8.8 & 74.125.21.139. I can ping my router and I can ping my router's WAN Gateway at my Comcast.
I can't browse to Google and I also can't browse to Google's IP: 74.125.21.139. I can't run Ubuntu updates. 
I can see my printers on my network and I can open their web config pages in my browser.
I've tried different WiFi SSIDs and a wired Ethernet connection.
I am getting assigned valid IP addresses and the behavior is the same whether I use DHCP or static IPv4. Same whether I use automatic DNS or static DNS. I have also tried disabling my firewall temporarily.

---

### Post by jeremy31 on 2018-02-25
Moved to it's own thread.  That isn't the wireless script results, it is the script itself.

---

### Post by vincentertainment on 2018-02-25
Thanks Jeremy. Here's the corrected paste.
[https://paste.ubuntu.com/p/VwNQ4VYYNG/](https://paste.ubuntu.com/p/VwNQ4VYYNG/)

---

### Post by jeremy31 on 2018-02-25
Try disabling the firewall as UFW is blocking a lot of local traffic between the computer and router

---

### Post by vincentertainment on 2018-02-25
Thanks Jeremy. I had tried sudo ufw status and verified my firewall was active. Then sudo ufw disable. I tested browsing again and there weren't any changes in my symptoms. After that, I ran sudo ufw enable to restore my settings. Should I try ufw reset?
Also, my Firewall GUI doesn't load since this upgrade either.

---

### Post by jeremy31 on 2018-02-25
Try changing some router settings, set channel to 1 and set encryption to WPA2 only, then in Network Manager settings for your wifi change IPv6 to disable/ignore and see if you have any better luck

---

### Post by vincentertainment on 2018-02-25
Update:
I rebooted and launched a Unity session instead of Gnome. My Firewall Configuration application (gufw.py) generated a crash report. I reinstalled with Synaptic. Synaptic also doesn't open in Gnome.
I can now launch the utility and switch between profiles like public and home, switch on and off and verify with ufw status.
Still can't browse the web. Tried ufw reset.
Here's an updated Wireless Info script since then.
[https://paste.ubuntu.com/p/27hX4hq7C7/](https://paste.ubuntu.com/p/27hX4hq7C7/)

---

### Post by vincentertainment on 2018-02-25
Switched to Channel 1. Encryption was already WPA2 Personal. Set IPv6 to Ignore.
Still can't browse. Here's an updated WiFi script output.
[https://paste.ubuntu.com/p/r8CVH4VdxF/](https://paste.ubuntu.com/p/r8CVH4VdxF/)

---

### Post by jeremy31 on 2018-02-25
Check the encryption settings again as it has TKIP enabled and it would be better if it just used AES
It might be power management causing some issues ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
I am not sure what is going on with the wifi channel occupancy as I had you move to channel 1 when there was only 1 other AP on it, your last report shows 15 AP's on channel 1

---

### Post by vincentertainment on 2018-02-25
I have virtual SSID's for different VLANs (Home workgroup, home lab, Internet of things devices, & Guest WiFi) There's a WiFi range extender that duplicates one of those but that only accounts for about 5 SSIDs. I live in an apartment and radio waves can get congested. For the most part, I dominate whatever channel I grab since other routers set to automatic will then pick different channels. I still only have 1 apartment's worth of traffic. Its just split up on different SSIDs and VLANs.
Ran the sed command and rebooted. Still can't browse. Here's the latest script output. Thanks again for working through this with me.
[https://paste.ubuntu.com/p/VNKphHbB42/](https://paste.ubuntu.com/p/VNKphHbB42/)

---

### Post by jeremy31 on 2018-02-26
It looks like you are trying to connect to this one
```
          Cell 01 - Address: <MAC 'jp5vmRJcO8' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"jp5vmRJcO8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a71cb4b4
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```
I see that TKIP is being used and that caused issues for my Atheros wifi, but there is also 'jp5vmRJcO85_2GEXT and this is not using TKIP and in one script result I saw it trying to connect to YPsaRSzK24 which is another using TKIP

Do you still have the USB/DVD that you installed Ubuntu with to see if you can connect using the Try without installing option?
It might also help to set the country code
```
sudo iw reg set US
```
What happens if you add a DNS in Network Manager of 8.8.8.8 for the wifi connection you want to use?

---

### Post by vincentertainment on 2018-02-26
I'm pleased to be posting from my Ubuntu laptop this time. It was a DNS issue. Fixed it with ```
[COLOR=#111111][FONT=Consolas]sudo dpkg-reconfigure resolvconf[/FONT][/COLOR]
``` and a reboot.

---

### Post by again? on 2018-02-27
> **vincentertainment said:**
> I'm pleased to be posting from my Ubuntu laptop this time. It was a DNS issue. Fixed it with ```
[COLOR=#111111][FONT=Consolas]sudo dpkg-reconfigure resolvconf[/FONT][/COLOR]
``` and a reboot.
resolvconf is not included in a 17.10 install.
Appears that resolvconf doesn't play well with systemd-resolved. 
If you have further problems you might consider removing the resolvconf package.

---

