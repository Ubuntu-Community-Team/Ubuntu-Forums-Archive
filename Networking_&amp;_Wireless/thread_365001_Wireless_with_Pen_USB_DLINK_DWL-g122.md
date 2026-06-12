---
title: "Wireless with Pen USB DLINK DWL-g122"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by Neo4 on 2007-02-19
I've got an USB wireless Pen DWL-g122 ver B1 and I'm using Ubuntu Edgy, and when I connect it to my laptop Ubuntu recognise it as unkown usb vendor specific interface and iwconfig detect it too:

rausb0 RT2500USB WLAN ESSID:""
Mode:Managed Frequency=2.412 GHz Bit Rate=11 Mb/s
RTS thr:off Fragment thr:off
Link Quality=0/70 Signal level:-120 dBm Noise level:-207 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

But When I try to search for wireless AP's it don't work, even when I turn off my laptop 2200bg wireless card! also I've tried add manually my wireless AP but can't connect!

and If I try to put it on Monitor mode it doesn't work too!
with "iwconfig rausb0 mode Monitor" it return no errors on the console but if I tipe iwconfig my rausb0 will still be in Managed mode!

I tried to install Windows drivers with ndiswrapper but no sucess :(

any help?

---

### Post by Floppyjoe on 2007-02-19
I pulled this information off the ndiswrapper list site:
> Card: D-Link DWL-G122 rev. B1 (USB)

    * Chipset: Ralink 2500
    * usbid: 2001:3c00
    * Label: P/N: EDWLG122..B1 FCC ID:KA2DWLG122B1
    * Native linux driver: Download from Ralink. Tested with Fedora Core 4, kernel 2.6.13-1.1526_FC4.
    * Driver: Latest WinXP driver downloaded from [78].
    * Other: Working great!
    * Other: Got WPA-PSK encryption working on Debian Linux with kernel 2.6.15.3. I used ndiswrapper-1.10 with original driver version 2.03 (shipped on CD with the Wireless USB Adapter) and wpa_supplicant-0.4.8 (got it from wpa_supplicant ) and it is working great. You only have to install the original driver in ndiswrapper, load the ndiswrapper module, use wpa_supplicant compiled with Driver-interface for ndiswrapper, then make a wpa_supplicant config (like in the examples shipped with the sourcecode of the wpa_supplicant) Edit it with your own key or passphrase and SSID, and then start wpa_supplicant -w -i wlan0 -c /path/to/your-created-config-file -D ndiswrapper -B thats all, enjoy it :-D . 

According to this is should work with ndiswrapper.
Did you blacklist the native driver when you tried ndiswrapper?

---

### Post by Neo4 on 2007-02-19
yes, But I don't know how to follow that steps! can you tell me the comands?


btw, how do I install the original drivers?

---

### Post by Neo4 on 2007-02-19
one more think! if I put iwconfig rausb0 mod Ad-Hoc

the pen start working! and my other laptop can see the connection!

but monitor mode don't work!!!!

---

### Post by Neo4 on 2007-02-19
any help?

---

