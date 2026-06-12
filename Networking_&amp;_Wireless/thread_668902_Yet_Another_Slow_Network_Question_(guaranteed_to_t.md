---
title: "Yet Another Slow Network Question (guaranteed to top the slowest of the slow!!)"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by krazyj on 2008-01-15
I'm getting some seriously painful transfer speeds. I dont know how you networking nuts do this. :)

(via iperf)
**Windows (wireless) -> Ubuntu (wireless):** 3-4 Mbps
**Ubuntu (wireless) -> Windows (wireless):** 3-4 Mbps

**Windows (wireless) -> Ubuntu (wired):** 8-10 Mbps
**Ubuntu (wired) -> Windows (wireless):** 9ish Mbps

**Windows (wired) -> Ubuntu (wired):** 85-86 Mbps
**Ubuntu (wired) -> Windows (wired):** 83-84 Mbps

**Windows (wired) -> Ubuntu (wireless):** 6 Mbps
**Ubuntu (wireless) -> Windows (wired):** 427-462-Kbps

_OUCH!_
FTP averages 350KB/s, too.
Samba? Hah. Its painful.


Im using a Buffalo WHR-G125 wireless router with DD-WRT default settings. Windows is claiming a 48+Mbps connection. Ubuntu Fiesty Fawn (updating to Gusty Gibbon as we speak) with an Edimax EW-7128G PCI Wireless Card (802.11b/g) using newest (as of 1/16/08) serialmonkey rt61 drivers.  I turned IPv6 OFF, too. No luck.

Says its getting 48Mbps....

**_ifconfig_**
```
wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXXXXXXXX  
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: XXXXXXXXXXXXd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:533745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:823156 errors:10904 dropped:10904 overruns:0 carrier:0
          collisions:54006 txqueuelen:1000 
          RX bytes:475142495 (453.1 MiB)  TX bytes:266322217 (253.9 MiB)
          Interrupt:9 
```

**_iwconfig_**
```
wlan0     RT61 Wireless  ESSID:"JoshsKingdom"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: XXXXXXXXXXXXXXXX   
          Bit Rate=48 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:XXXXXXXXXXXXXXXXXXX
          Link Quality=79/100  Signal level:-53 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Somebody PLEASE help me!!!! It would be much appreciated. :)

Thanks for reading this far!
-Josh

---

### Post by HermanAB on 2008-01-15
So what happens when you use a cable?

Cheers,

Herman

---

### Post by psyburn on 2008-01-16
I've had this one plague me on one machine after installing Ubuntu 7.10 on it with a rt61 PCI
I fixed it by installing the daily CVS of the [serialmonkey]("http://rt2x00.serialmonkey.com/") drivers (I used the 12-12-2007 as that was current the day I installed it)
I followed the HOWTO on the site and it work just fine
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61")

I ended up having to edit /etc/network/interfaces and make the configuration static since Network Manager doesn't work yet with these drivers yet.
```
gksu gedit /etc/network/interfaces
```
and adding
```
iface [ra0/wlan0] inet dhcp 
  pre-up iwconfig [ra0/wlan0] essid YOUR_SSID
  pre-up iwpriv [ra0/wlan0] set AuthMode=WPAPSK
  pre-up iwpriv [ra0/wlan0] set WPAPSK="YOUR_WPA_KEY"
  pre-up iwpriv [ra0/wlan0] set EncrypType=TKIP
```
You'll need to replace [ra0/wlan0] with whatever your adapter ends up being after installing the new drivers, as well as YOUR_SSID and "YOUR_WPA_KEY" with whatever they are.

Works great and gets full speeds...

EDIT: this was a problem known to happen with rt61cards in Gutsy that I tried to follow after the release.
My card would only get 100KBps tops. I waited 2 months for any kernel patches and after a few, the speed limit upped to 250KBps
Installed serialmonkey and I get full 4MBps over ssh over 802.11g-only (do the math I'm getting full realistic speeds)

---

### Post by krazyj on 2008-01-16
@HermanAB: Havent tried that yet but I will. Why dont I try this other gentleman's suggestion first and I'll get back to you on that if it doesnt work

@psyburn: Thanks!!!!!!!  Ill give this a shot.

---

### Post by krazyj on 2008-01-16
@psyburn: Well, that didn't fix it unfortunately. I now have the newest daily CVS (for today) driver from serialmonkey for the rt61, though!

@HermanAB: Ok. So I did the entire batch of tests for you in every possible combination... Enjoy. :) 

**Windows (wireless) -> Ubuntu (wireless):** 3-4 Mbps
**Ubuntu (wireless) -> Windows (wireless):** 3-4 Mbps

**Windows (wireless) -> Ubuntu (wired):** 8-10 Mbps
**Ubuntu (wired) -> Windows (wireless):** 9ish Mbps

**Windows (wired) -> Ubuntu (wired):** 85-86 Mbps
**Ubuntu (wired) -> Windows (wired):** 83-84 Mbps

**Windows (wired) -> Ubuntu (wireless):** 6 Mbps
**Ubuntu (wireless) -> Windows (wired):** 427-462-Kbps

Keep in mind now I just updated to the newest CVS version of the serialmonkey rt61 drivers, too. Running Gusty Gibbon, as well. And this is all through my Buffalo WHR-G125 running DD-WRT v24 beta factory settings.

HALP! :)

---

### Post by HermanAB on 2008-01-16
Hmm, if I were you, I'd string some cat5 wires through the cold air return ducts...

You should also try to adjust the channel used by the WiFi access point.  If it is in the middle (default), crank it down/up to either end of the spectrum and see if things improve.  You may have 20 different neighbours all on the same channel.

Cheers,

H.

---

### Post by krazyj on 2008-01-16
@HermanAB: Thanks. I was kind of hoping to get this working wirelessly since I live in an apartment and both boxes are in the same room. I do appreciate your help thusfar though :)

It seems like Ubuntu just needs some tweaking. Or, perhaps, my router.

As per netztier's post [_here_](http://ubuntuforums.org/showpost.php?p=2285878&postcount=22), Id like to at least be able to reach 20-25Mbps wirelessly. Especially since its claimed to be 54Mbps.

Anyone else? :confused::confused::confused:

---

### Post by boomcat on 2008-01-17
I have a similar speed problem on my NFS WiFi network between a desktop and a laptop. So I put a packet sniffer up on a Windows laptop (Ethereal) and it reported hundreds of "TCP Out-of-order" errors in just a few minutes. I have no idea how to fix this, but I guess my next step will be to run some CAT5 cable between the router and the desktop and then "sniff" again.

---

### Post by krazyj on 2008-01-17
Alright well I went into #ubuntu last night and was told that, since I was using WEP, I would be limited to 802.11b.

I spent all yesterday and can say that** Im now using WPA2 Personal PSK in forced G-mode **(router and card) and not anything more than marginally faster.

****.

Suggestions? :confused::confused:

---

### Post by krazyj on 2008-01-17
Switching to ndiswrapper didnt do squat, either.

---

### Post by HermanAB on 2008-01-17
Well, you may have to buy a new WiFi router, since some of them just don't work properly no matter what you do.

---

### Post by krazyj on 2008-01-20
Im just going to wire it. Whatever. Im using a quality Buffalo router with hacked DD-WRT firmware which makes it even better.

It is a shame Ubuntu has such awful support for wireless networking.

---

