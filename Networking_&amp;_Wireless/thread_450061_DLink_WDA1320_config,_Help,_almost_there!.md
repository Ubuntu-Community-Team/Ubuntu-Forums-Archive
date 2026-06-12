---
title: "DLink WDA1320 config, Help, almost there!"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by gtfourdreams on 2007-05-20
ok, long story short. On Feisty Fawn, fresh install.

1) i ditched my Linksys WUSB54G
2) got the DLINK WDA-1320 with Atheros Chipset
3) went through all the HOWTO's and help threads i could find.
3) I have the WPA2 with AES set up and ready to go.
4) Static IP works and i can get on the web wirelessly
5) PROBLEM: can't connect to 192.168.0.1 modem or 192.168.0.50 router or 192.168.0.49 printer! **FIXED**

*UPDATE* i fixed it within a few minutes of posting this.

this is how i set mine up, if anybody wants this information. 
i did *NOT* use a /etc/wpa_supplicant.conf file.
i *DID* use the madwifi which came with Feisty Fawn
i *DID* everything command line
i put the DNS servers in the "Network Settings" | "Manual Configuration"

```

chao@pavilion:~$ sudo gedit /etc/network/interfaces
-------------------------------------------------------
auto lo
iface lo inet loopback

##### BY commenting these eth0 out. i could connect to local 192.168.0.*
#auto eth0
#iface eth0 inet dhcp
#iface eth0 inet static
#address 192.168.0.11
#netmask 255.255.255.0
#gateway 192.168.0.1

auto ath0
iface ath0 inet static
address 192.168.0.10
gateway 192.168.0.1
netmask 255.255.255.0
wpa-driver madwifi
wpa-ssid imwatchingu
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 64CharacterKeyHere

```

```

chao@pavilion:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:BF:0D:00:91
                    ESSID:"imwatchingu"
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality=27/94  Signal level=-68 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK

```

```

chao@pavilion:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

These are the links that helped me out.
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
[http://ubuntuforums.org/showthread.php?t=225290](http://ubuntuforums.org/showthread.php?t=225290)
[http://madwifi.org/wiki/Compatibility/D-Link](http://madwifi.org/wiki/Compatibility/D-Link)

---

### Post by KMW on 2007-05-21
Doesn't work! I've been playing around with this for over a week and have gotten nowhere. Have made 2 posts to the networking forum and haven't even gotten so much as a response. As a matter of fact, I've received more help from PCer Linux forums than I have here!

Before I started with the Wifi I looked through the supported list and it was stated there that the DWL-520+ "just plan works"! Bull!!!!
Sure, with some help I've run through all the checks, The card is there as acx100, even shows all the addrs, can even get it to send but it won't receive a thing. I even went so far as to reinstall an old 3com nic card and it connected immediately, though it still would not find my MS XP wifi laptop!
I've almost had enough and am ready to look elswere! From all the feedback I'd gotten on other forums that stated how easy Ubuntu is to use and the amount of support available I thought this was the way to go. Unfortuneately for me, where this PC has to be located there is no wired connection available.

---

