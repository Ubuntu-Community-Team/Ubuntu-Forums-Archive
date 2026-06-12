---
title: "Wi-Fi is Gone After Update - Any Advice?"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by twinhead on 2007-09-27
Hi All!

I have been using Ubuntu Feisty Fawn for a while, and everything was just fine... but when I updated my Ubuntu (from the Update Manager), after a reboot, my wireless connection were "down".

What happens, is, my knowledge to Ubuntu are very restrict, and I don't know anything about it, when it comes to more specific information... but apparently, I can't see the "task bar icon" for networks, and right now, I'm posting using Cable (LAN).

What i'm missing also, is: SYSTEM > ADMINISTRATION > NETWORK
I can only see: Network Tools.

Ok, before someone might ask me, here's what i get:

```
zzz@feisty:~$ ndiswrapper -l 
net5211 : driver installed
        device (168C:001A) present (alternate driver: ath_pci)
```

and

```
zzz@feisty:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Than, reading the forums, i've tried:

```
zzz@feisty:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Denied permission
```

Well, it looks like everything is installed... but I can't activate the Wireless...
Can someone help me in this? Many thanks in advance.

---

### Post by Travisher on 2007-09-27
I had a lot of fun and games with wifi. The network manager completely failed to get the ESSID and key into the interface even though it wrote the information into the /etc/network/interfaces file. After much head scratching and using iwconfig and iwlist and ifconfig as root I did get it to sometimes connect as long as I didn't touch the GUI interface.
In the end I downloaded a utility called wicd. You have to un-install the default network manager but then it ain't working anyway is it?
This just worked, displaying a list of possible APs and letting me select mine and feed it the ESSID and key. Sorted!

---

