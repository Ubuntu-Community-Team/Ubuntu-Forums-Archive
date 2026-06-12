---
title: "command line wireless for multiple AP NetworkManager woes"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by fwallace99 on 2007-06-26
Hi all --

Hope you can help me with this one. I am running Feisty 7.04 on my Toshiba Satellite A135-S2276 laptop.

My problem is that NetworkManager keeps dying or dropping my wireless connection in my house. With the same laptop booted into Windows I have no problems. Apple laptops have no problems either.

I have an old Apple Base Station with 128 bit WEP, and a Belkin repeater. I would like to connect to the Belkin repeater in parts of my house since it has a much stronger signal, obviously. With Windows or the Mac laptops this happens transparently.

NetworkManager ALWAYS picks the weakest signal, the Apple Base station. That's probably part of the problem. I'm also in a "noisy" part of the neighborhood with lots of broadcasts:

floyd@Prytania:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:74:82:F3
                    ESSID:"applenet"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/94  Signal level=-33 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:30:65:1C:B0:40
                    ESSID:"applenet"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:14:95:CF:CE:39
                    ESSID:"2WIRE973"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/94  Signal level=-55 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:12:17:11:DF:D0
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/94  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:14:BF:E8:CA:23
                    ESSID:"mcmillan"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
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

floyd@Prytania:~$ 

Obviously I want this AP: Cell 01 - Address: 00:15:E9:74:82:F3.

This is what I've tried:

[grep for NetworkManager pid and kill -9 the process, also NetworkManager dispatcher]

sudo ifconfig ath0 down
sudo killall dhclient
sudo iwconfig ath0  essid applenet mode Managed channel 1 ap 00:15:E9:74:82:F3 enc key "hex codes"
sudo dhclient ath0

I get a bunch of NO DHCPOFFERS messages (it can't connect) and it sleeps.

This is driving me nuts since I SHOULD be able to get to the AP the old-school way through the command line. [Right now NetworkManager will not come up at all, I've had to use WiFiRadar to connect and it gave me a weak signal.]

Can anyone help me with the old-school command line way which darn it should work? [Network Manager just isn't cutting it.]

Thanks!

---

### Post by spd106 on 2007-06-27
First of all have you tried adding the bssid of the repeater in gconf? You can have multiple bssids listed. [https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28)

Basically you need to add the wireless interface to the /etc/network/interfaces file along with the key and essid e.g.
```
:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid applenet
wireless-key 1234567890

```
Ubuntu has the networking scripts set-up so that Network Manager will ignore these interfaces. However you can disable it completely following the directions in the link above.

I would recommend that you step up to WPA if you don't have any incompatible hardware. There is a good guide to the older method in the 'Howto: Wireless Security...' sticky on page 1 of the forum.

Good luck

---

### Post by fwallace99 on 2007-06-27
Spd --

Thanks. Sadly my hardware does not support WPA. It's the original base station from Apple. Sigh. Don't have the bucks to swap it out now.

If I move the BSSIDs of the Access Points in the gconf editor, my assumption is that I can make the priority to connect. Is this correct, i.e. the "first" or top-level BSSID will be the one that Network Manager tries to connect to first?

What's frustrating is that for a short time, I was able to get old-school command line networking up, but after a while it simply died. 

What I did was grep the process list, kill -9 the two PIDs (Network Manager and the dispatcher); then specify the BSSID:


```
sudo iwconfig ath0 essid applenet mode Managed channel 1 ap 00:15:E9:74:82:F3 enc key "hex codes"
```

Any thoughts? Is it better to get the old-school command line style working, or should I stick to NetWorkManager? I'm concerned since I'll need roaming access, hopefully in a less noisy wireless place. I have local wireless networks on and off all the time around here.

ETA: I tried it today and no go, I STILL get the connection to the "master" base station instead of the bridging AP, while Mac OSX and Windoze machines connect properly to the higher-signal AP.

For some reason, only NetworkManager Gnome applet will connect, the command WILL NOT WORK.

Is there something special/weird/broken in Ubuntu that prevents the command line from working?

Thanks.

---

