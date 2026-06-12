---
title: "Wireless is not working after upgrading to 6.10"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by johnny1978 on 2007-04-03
Hello all,
First of all, even if the problem cannot be solved, I have to tell you what a great work you all are doing. Thanks in advance!
I am a newbie in ubuntu. I installed 6.06 on my Toshiba Satellite Laptop and everything worked fine. But when I upgraded to 6.10, my wireless card stopped working. I have already installed network manager, but it does not help.
If I do iwconfig I get the following:

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:"ssid"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:2349  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

I have tried the how to's that are posted here on the forums, but they don't work, maybe because I don't have the same specs as in the examples.

Could you all help me with this one?
Thanks in advance.

---

### Post by Tilex on 2007-04-04
Try doing:
```

$sudo iwconfig ath0 essid YOUR_WIRELESS_NAME key YOUR_KEY mode managed
$sudo dhcpcd ath0

```

Tell me if it works.  Maybe you'll need to install dhcpcd, in which case you'll need to do so via the Synaptic Package Manager (type dhcpcd and you'll see it).

---

### Post by johnny1978 on 2007-04-04
Hi Tilex,
Thanks for such a quick reply.
It didn't work. When I wrote the iwconfig command it gave me this: 
SET failed on device ath0 ; Operation not permitted.
I  installed dhcpcd, but when I typed it into the terminal nothing happened. It only asked for my password and then it froze.
Can you think of any other suggestions?
Thanks

---

### Post by Floppyjoe on 2007-04-04
Make sure you have linux-restricted-modules for your kernel installed.

---

### Post by johnny1978 on 2007-04-04
Both synaptic and uname -r tell me I have linux-restricted-module 2.6.17-11-386.

---

### Post by Floppyjoe on 2007-04-04
Do you have all your network interfaces deactivated in System/Administration/Networking? This is a requirement for Network-Manager to work in 6.10.

---

### Post by johnny1978 on 2007-04-04
Yes, I already did that too.

---

### Post by Floppyjoe on 2007-04-04
What is the output of:
```
sudo iwlist ath0 scan
```

---

### Post by johnny1978 on 2007-04-05
Hello,
this is what happens when I type sudo iwlist ath0 scan

ath0      Scan completed :
          Cell 01 - Address: 00:18:39:3F:0C:3D
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/94  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:39:67:10:D7
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/94  Signal level=-70 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:09:5B:49:1C:7A
                    ESSID:"Wireless"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=11/94  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:0F:66:39:BE:77
                    ESSID:"darwin"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:14:6C:98:A5:8C
                    ESSID:"nerdlab"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 06 - Address: 00:0F:66:9C:16:3F
                    ESSID:"dan"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: 00:14:6C:D7:BB:CA
                    ESSID:"Helloagain"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/94  Signal level=-26 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101000e0000
          Cell 08 - Address: 00:13:46:07:C6:44
                    ESSID:"RezoDLink"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 09 - Address: 00:06:25:87:52:2B
                    ESSID:"Happy now, Juan Manuel?"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 10 - Address: 00:14:6C:DA:A8:82
                    ESSID:"RobotFamily"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 11 - Address: 00:18:4D:4C:CD:30
                    ESSID:"QuietNet"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101000eff7f

One of those is my wireless network.

---

### Post by Floppyjoe on 2007-04-06
Well we know that it scans then so you probably have the right drivers set up.
What type of encryption are you using?

---

### Post by johnny1978 on 2007-04-06
I'm using wep because not everybody in my network is capable of using wpa

---

### Post by johnny1978 on 2007-04-06
I tried to do again everything you have told me to do so far. When I typed
sudo iwconfig ath0 essid <Network Name> key <Key> mode managed  
I get the following, and this has not happened before.

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; Operation not permitted.

---

### Post by Floppyjoe on 2007-04-06
I've attached a screenshot which shows an icon in the top menu bar of what the network manager applet looks like. It's got four little blue bars for signal strength or two computer screens networking together if using wired. If you click on this it should allow you to set your network settings.

I have read that there are some kinds of cards that network manager does not play well with and will try to do a little more research about that.

---

### Post by johnny1978 on 2007-04-06
yup, that's the one I got.

---

### Post by Floppyjoe on 2007-04-06
> **johnny1978 said:**
> yup, that's the one I got.

What happens when your right click on it?
You should have enabled wireless and networking there.

---

### Post by johnny1978 on 2007-04-09
Well, I have wireless access at last. I don't know how but now it's working.
This thread can be closed now.

---

