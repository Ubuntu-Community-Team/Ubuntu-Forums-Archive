---
title: "Dell 1501 Wireless"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by Steve- on 2007-04-02
After following this guide: [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)
And trying a variety of different driver files from Dell, I'm unable to get a working wireless connection.

System->Administration->Networking  shows a wireless connection, it has a tick by it and it lets me enter my wireless connection details. 

In the system tray, if I go into the Network Connection thing and select eth1, it just says disconnected.

How do I connect it?


Show random information that might help:


sudo iwlist scanning:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:18:E4:70
                    ESSID:"default"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-28 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

sit0      Interface doesn't support scanning.
```

ndiswrapper -l:
```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
```


I'm in Edgy Eft.

Any ideas? Thanks for your help. If theres any other info you need, let me know.

Steve

---

### Post by chili555 on 2007-04-03
This: *(alternate driver: bcm43xx)* sometimes means the native driver is conflicting with your ndiswrapper install. Let's *sudo gedit /etc/modprobe.d/blacklist* to see if ```
blacklist bcm43xx
``` is in there. If not, add it on it's own line at the end. Reboot.

Did you connect? If not, let's give a few commands:```
sudo iwconfig eth1 essid default
sudo iwconfig eth1 ap 00:15:E9:18:E4:70
sudo iwconfig eth1 key <put_key_here>
sudo dhclient eth1
```Let us know.

---

### Post by Steve- on 2007-04-03
The driver is blacklisted.

Assuming "key" is the wifi password, I get this response:

```
~$ sudo iwconfig eth1 key my_key
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "my_key".
```

And if this is of any use:

```
~$ sudo iwconfig eth1
eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Otherwise, if you proceed with the last command:

```
~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:18:f3:92:cc:83
Sending on   LPF/eth1/00:18:f3:92:cc:83
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
...
```

Thanks

---

### Post by chili555 on 2007-04-03
Oops! I made a mistake. Your router is clearly set up for WPA, and iwconfig assumes the encryption is WEP. You will need to set up WPA on your Dell. Here is a guide: [http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)

I will now go clean my glasses!

---

### Post by Steve- on 2007-04-04
Thanks, that worked like a charm.

Upon rebooting I found the wireless was no longer being detected though, with iwconfig not even showing eth1.

Couple of tests finds that typing this gets everything working again
```
sudo modprobe ndiswrapper
```

Is it possible to automate this? (And while we're at it, what exactly is it doing?)

Thanks

Steve

---

### Post by chili555 on 2007-04-04
*sudo gedit /etc/modules* to add:```
ndiswrapper
```and let us know. Glad it's working.

---

### Post by Steve- on 2007-04-07
This message comes from wireless, but it takes so many random commands to get it working, hopefully someone can tell me which ones I need?


Today's path started with me on a wired connection, I decide to fix the wireless.

1) Unplug ethernet cable.

2) iwlist scanning - no result for eth1

3) modprobe ndiswrapper

4) iwlist scanning - eth1: no scan results

5) /etc/init.d/networking restart - sit through a minute of it not finding eth0 (my wired connection).

6) iwlist scanning - eth1: full results for my router

Then it comes to random modprobing of ndiswrapper, a couple of restarts and a dhclient eth1 for good measure.
I did get it seemingly connected, but after plugging my ethernet in and unplugging again, it needed another restart to use the wireless instead of the wired.


I'm really dreading when in a couple of weeks time I need to take this to the uni campus and attempt to get wireless working there :/

---

### Post by chili555 on 2007-04-09
If you added ndiswrapper to /etc/modules, then *sudo modprobe ndiswrapper* does nothing. 

I suggest you look into wifi-radar (available in Synaptic) or Wicd (available here: [http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)) to manage moving from location to location. I prefer Wicd. If you have installed NetworkManager, it will conflict with the first two.

NetworkManager gets mixed reviews; some people swear by it, others sweat *at* it.

Post back; we have to be fine-tuned in a day or so.

---

### Post by Steve- on 2007-04-12
I installed NetworkManager as I need to be able to connect to VPN, but it doesn't seem to have a Wifi option.
It also seems to have broken my wifi, or a least when I tried I couldn't get anything to work before I gave up and plugged myself in.

I'm leaving this house tomorrow and then I'll have a wire connection full time in my house, and will have to reconfigure my wifi for the university wifi anyway.
Will the new network things in Feisty ease the use of all these things together?

Thanks
Steve

---

### Post by chili555 on 2007-04-12
NetworkManager needs a bit of configuration to get going correctly. Check here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) Especially note this:> Any already configured devices that you want to be available in Network Manager will need to de-configured, as otherwise they will be ignored.

The easiest way to do this is by going to System -> Administration -> Networking and then going to "Properties" of each connection. In Properties, just untick the "Enable this connection" checkbox. Logout then log back in again. These connections should now be available in Network Manager. 

---

