---
title: "Ubuntu 18.04 with TL-WN822N, can't connect"
date: 2018-08-13
forum: Networking &amp; Wireless
---

### Post by jacek81 on 2018-08-13
Hello! 
I can't get my wireless usb card to work. It is TP-Link model TL-WN822N v.4.
I always used LAN internet, but few months ago I moved, so I bought this wireless usb card. I had problems with it in Ubuntu 16.04 from the start, now I updated Ubuntu to 18.04.1 and still can't get the card to work. I never managed to install proper drivers, and I'm afraid I made mess trying to do so (using hints from the forum and the guide from TP-Link site). I'm not really good at Ubuntu.
I use some old card instead, but the speed is very slow. The old card is a/b/g and it gets around 5 Mbps (but still I managed to update from 16.04 to 18.04.1 with this card). I can see the TP-Link in Settings (as 802.11n NIC), but I don't think it ever really connects. And it doesn't even blink. It works in Windows 7. I've got dual boot desktop computer, 

Can you help me to get rid of useless drivers and to install the proper ones? Here is my wireless info: [http://paste.ubuntu.com/p/xdQGYKD6JG/](http://paste.ubuntu.com/p/xdQGYKD6JG/)

Thank you.

---

### Post by chili555 on 2018-08-13
We see several things amiss here. First:> ##### /etc/modules ######################

ath9k
ath9k_htc
ath9k_htcYour TP-Link is not the ath9k_htc model, so let's undo the addition to /etc/modules. From the terminal:```
sudo nano /etc/modules
```Remove completely the lines above. Save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Next, we see that *both* the internal and the USB are connected and have IP addresses. I suggest that you blacklist the internal:```
sudo -i
echo "blacklist rtl818x_pci"  >>  /etc/modprobe.d/blacklist.conf
exit
```Next, I notice that* all* of the networks you can see with a scan have very low signal strength. Yours, for example:> Address: <MAC 'Mesjasz Narodow XD' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    [COLOR="#FF0000"]Quality=26/70[/COLOR]  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Mesjasz Narodow XD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:MasterPlease shut down the computer. Remove the TP-Link and carefully check the integrity of the detachable antenna. Make sure it is connected securely and, ideally, pointed straight up. Reinsert it, restart the computer and tell us if there is any improvement.

---

### Post by jacek81 on 2018-08-13
Thank you so much for your answer. I did all the things you advised above. There's no real significant change in speed of download/upload, but I do connect with the wireless TP-Link now.

There's a weird thing I noticed. The wifi icon in the top right of Ubuntu 18.04 screen, which indicates signal strength, is going from 2, to 4, to 1, then back to 2. Seems not stable at all. May this be a problem with power supply to the tp-link?

There's current wireless info [http://paste.ubuntu.com/p/fTNBmnhR6F/](http://paste.ubuntu.com/p/fTNBmnhR6F/)

Now it's 22/70, but while ago it was 51/70. I also tried another usb port and another usb cable, I don't know what to do next.

---

### Post by chili555 on 2018-08-13
There are two different drivers attempting to run the USB wireless. Let's remove one and see if it helps:```
sudo modprobe -r 8192eu
```Any improvement? If so, we'll make it permanent.

---

### Post by jacek81 on 2018-08-13
It doesn't change the speed or the icon activity. But I didn't reboot - should I?

---

### Post by chili555 on 2018-08-13
Nope. But please next try:```
sudo modprobe 8192eu
sudo modprobe -r rtl8xxxu
```How about now; any improvement?

---

### Post by jacek81 on 2018-08-13
When I did these two commands, the internet connection was gone. Like there was not even select wifi / turn off / settings part in the top right corner of the screen. 
So I entered
[COLOR=#000000][FONT=&amp]
```
sudo modprobe rtl8xxxu
[/FONT][/COLOR]
```
And the connection came back again, but still slow.

---

### Post by chili555 on 2018-08-13
Is your router set to auto select the channel or a fixed channel? Fixed is very strongly preferred; generally 1, 6 or 11.

---

### Post by jacek81 on 2018-08-13
Yes, it's fixed on channel 6, mixed b/g/n. 

In the meantime I even tried using my smartphone as a router and spreading LTE signal (with the phone close to the antennas), but the speed was even lower.

---

### Post by chili555 on 2018-08-13
Without rebooting, so that only rtl8xxxu is loaded, let's check the log: ```
dmesg | grep -i rtl
```

---

### Post by jacek81 on 2018-08-13
I got such result:

```
~$ dmesg | grep -i rtl
[    2.233102] r8169 0000:02:00.0 eth0: RTL8168e/8111e at 0x        (ptrval), 48:5b:39:03:0f:f3, XID 0c100000 IRQ 29
[   32.628593] usb 2-1.3: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):
[   32.628678] usb 2-1.3: RTL8192EU rev B (SMIC) 2T2R, TX queues 3, WiFi=1, BT=0, GPS=0, HI PA=0
[   32.628679] usb 2-1.3: RTL8192EU MAC: 7c:8b:ca:16:3a:a7
[   32.628681] usb 2-1.3: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[   34.257158] usbcore: registered new interface driver rtl8xxxu
[   34.315144] RTL871X: module init start
[   34.315145] RTL871X: rtl8192eu v4.4.1_17696.20160509_BTCOEX20160412-0042
[   34.315146] RTL871X: build time: Aug 10 2018 21:56:17
[   34.315147] RTL871X: rtl8192eu BT-Coex version = BTCOEX20160412-0042
[   34.315175] usbcore: registered new interface driver rtl8192eu
[   34.315175] RTL871X: module init ret=0
[   34.335215] rtl8xxxu 2-1.3:1.0 wlx7c8bca163aa7: renamed from wlan0
[   35.437722] usb 2-1.3: rtl8xxxu_bss_info_changed: HT supported
[  195.877802] RTL871X: module exit start
[  195.877804] usbcore: deregistering interface driver rtl8192eu
[  195.877843] RTL871X: module exit success



```

But on the way I rebooted, so before this I had to use this command again:

```
sudo modprobe -r 8192eu
```

Was I right?

---

### Post by chili555 on 2018-08-13
> **jacek81 said:**
> 
But on the way I rebooted, so before this I had to use this command again:

```
sudo modprobe -r 8192eu
```

Was I right?Yes. Frankly, I don't see anything wrong and therefore fixable. Just for completeness, let's blacklist 8192eu:```
sudo -i 
echo "blacklist 8192eu"  >>  /etc/modprobe.d/blacklist.conf
exit
```Also, I notice that your router is on channel 6. It is the most congested channel in the neighborhood.> Channel occupancy:

      12   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      28   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      11   APs on   Frequency:2.462 GHz (Channel 11)You might try channel 11 instead.

Finally, I worked on a case recently where the name of the SSID contained spaces and connectivity was improved when the SSID was renamed without spaces. Is it possible to change the name in the router to MesjaszNarodowXD or similar?

I am running out of suggestions.

---

### Post by jacek81 on 2018-08-13
OK, thank you very much for your patience with this case. I blacklisted the driver, changed the SSID and the channel. The wifi still runs at frustrating ca. 5 Mbps. I've read somewhere that updating motherboard BIOS might help, but it's quite an old motherboard so I don't expect to find anything newer than I already have. If I find, I'll get back to you with the results.

It's odd that the internal wifi card, the a/b/g one, worked at roughly the same speed as the new TP-Link. I don't know what can be wrong here.

Thank you once again.

---

