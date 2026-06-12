---
title: "wireless connects to open networks but not WEP protected networks"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by halfmanhalfbug on 2008-02-28
My wireless is able to detect networks:

```
broose@crash:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:A3:42:17:EE
                    ESSID:"NANOGEN"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```
But I cannot connect to a WEP-ascii network at work using Network Manager and a profile containing the WEP-ascii key. I am able to connect to a WPA network at home only through Network Manager and only if I make a new profile, save it, and load it fresh each time. Wifi Radar does not connect to either type of protected network. I would really like to do everything through wifi radar (or similar) and use DHCP exclusively.

Some details:
HP L2000 Turion (64 bit)
Broadcom 4318, ndiswrapper driver (detects hardware OK), wlan0 interface (in /etc/network/interfaces, /etc/modprobe.d/ndiswrapper, /etc/udev/rules.d/70-persistent-net.rules, and /etc/wifi-radar.conf)

```

broose@crash:~$ dmesg | grep wlan0
[   36.133416] wlan0: ethernet device 00:90:4b:f8:d4:e2 using NDIS driver: bcmwl5, version: 0x364400a, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   36.133470] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   42.228903] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

I've searched previous threads and my problem looks most similar to 
[this thread]("http://ubuntuforums.org/showthread.php?t=704127") which was unresolved. Sigh.

---

### Post by clb137 on 2008-02-28
HI,

Have u tried changing it to WEP Hexi key?


Clint

---

### Post by cosborn72 on 2008-02-28
I have had a similar problem with Broadcomm adapters and WEP.  WEP can use either an ASCII or a HEX key.  I have never gotten the adapter to work with an ASCII key.  

Can you log in to your router and see what your key is?  If it is ASCII (and assuming you are not going to screw up all the other network users by changing the key), go ahead and change to HEX and set a new key.  That might fix the problem.

---

### Post by mrobinson_sr on 2008-02-28
I am assuming then, that the only thing that needs done to WEP protect my wireless is to first turn back on the WEP in the router, then in the device settings on Linux input the WEP key and choose Hexidecimal.  Which is about the same as done in Windoes.  Am I correct that this would be the process?

Thank you.

---

### Post by fxjr on 2008-02-28
Hi all!

I have a broadcom 4306 and could configure it successfully through ndiswrapper. There are excellent tutoriais in ubuntu forums! Thanks!

I'm facing a similiar problem but in my case I can't connect to any protected AP. Only AP without password. Network manager shows me the protected AP's:

```

iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:13:46:CF:27:66
                    ESSID:"MW_Net"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1B:11:3F:42:F8
                    ESSID:"MERCADO_DF"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
```



My network device is called eth1, although I followed the procedure of adding ndiswrapper and put wlan0 to /etc/modprobe.d/ndiswrapper and I put the following line: alias wlan0 ndiswrapper.

I also added a file called /etc/default/wpasupplicant with the contents:
```
ENABLED=0
```

When I try to connect to a WPA AP, it seems to hang waiting for something and some time later connects with wired connection.

This is what I get from iwevent:

```

23:51:27.072811   eth1     Set Encryption key:off
23:51:28.396800   eth1     Set Mode:Managed
23:51:28.527754   eth1     Set ESSID:"PSAccess"


```


And doesn't do anything else.

Do you have any clues? Configuration or some other way I can use to check what can be happening?

I'd really want to be able to connect to encryption protected AP's.

Thanks in advance.

---

### Post by tgalati4 on 2008-02-28
WEP keys can be Open or Shared.  Your wireless setting and Access Point need to be set to the same protocol.

---

### Post by halfmanhalfbug on 2008-02-28
Sorry for the delayed reply (night here is day in North America).
 tgalati4, you're right! I opened the profile for my WEP-ascii network in wifi radar and there is a box for security with the options:
1. nothing (no text)
2. open
3. restricted
This time I selected "open" and it worked! Previously I had assumed "open" meant not to use a key at all, but I guess it refers to  an open key (vs shared key). Thanks again!
BTW I can find no way of setting open or shared keys in Network Manager profiles.

---

### Post by halfmanhalfbug on 2008-02-28
BBTW For those using ndiswrapper, I found I could specify "wlan0" rather than "eth1" for the name of the wireless interface by editing 4 files:
/etc/network/interfaces
/etc/modprobe.d/ndiswrapper
/etc/udev/rules.d/70-persistent-net.rules
/etc/wifi-radar.conf
Simply replace "eth1" with "wlan0".

---

### Post by halfmanhalfbug on 2008-02-28
After further experimentation, two things are needed to connect to the WEP-ascii network:
1. The profile for the network must be active in Network Manager (i.e. roaming mode is not good)
2. Security must be set to "open" (for my particular network) in wifi radar and I must connect through wifi radar (Network Manager is unable to connect by itself).
My settings are as follows:

Network Manager
ESSID: NETWORK-NAME (can be obtained from iwlist)
Password type: WEP key (ascii)
Network password: your-password
Configuration: Automatic configuration (DHCP)

Wifi Radar
Network Name: NETWORK-NAME  (same as ESSID above)
WifiOptions
  Mode: Managed
  Channel: auto
  Key: your-password
  Security: open
No WPA
Automatic Network Configuration (DHCP)

It would be really (REALLY!) nice in Hardy if the Network Manager could just be set on roaming and all connections could be made with a manager like wifi radar or kwifi.

---

### Post by tgalati4 on 2008-03-01
It's a common issue.  I'm glad you got it figured out.  Network Manager is improving but initial configuration can be difficult.  Thanks for your tips.

---

