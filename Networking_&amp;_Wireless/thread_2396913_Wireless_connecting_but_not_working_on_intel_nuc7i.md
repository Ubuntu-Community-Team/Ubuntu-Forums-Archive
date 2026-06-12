---
title: "Wireless connecting but not working on intel nuc7i7bnh"
date: 2018-07-22
forum: Networking &amp; Wireless
---

### Post by luisma31 on 2018-07-22
Installed Ubuntu 16.04.4 on NUC, configured the wireless following different sites. It is configured and connected but no layer3 connectivity apparently. Found some topics in this forum as well as en experimental script for troubleshooting. Output enclosed, can anyone help?
Thank you

---

### Post by chili555 on 2018-07-23
Is this your access point?>  Cell 02 - Address: <MAC 'LVN' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"LVN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002b8bdb4b794
                    Extra: Last beacon: 3510ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKOld Chili and your driver iwlwifi don't like mixed mode WPA and WPA2 and we also don't like auto channel selection one bit!

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I suspect your problem is actually DNS. With the ethernet detached, what do these commands report? ```
sudo resolvconf -u
ping -c3 8.8.8.8
ping -c3 www.google.com
```

---

### Post by luisma31 on 2018-07-23
Thanks, the access point is a very very sophisticated Ruckus AP which I'm about to change now

The DNS I will try but I don't think is the issue as ping to IP directly failed and the ifconfig reports errors in Tx and Rx traffic so most likely the AP may be creating the issue

It is actually Fixed to AES (no TKIP at all) which I will leave as it is and will move from Mixed Mode to WPA2 only

rebooting now if it doesn't work I will remove auto channeling and change from 40 mhz to 20 mhz which shoud improve things a bit

the adapter shows connection though on the 5 GHz spectrum not the 2.4

---

### Post by luisma31 on 2018-07-23
Wow look at that, just removing the mixed mode did the trick that was all what's needed .... 
Old chili thanks so much for your help you got it working with the recommendations, I may move to fixed channel and 20 MHZ band later on.

Some more odd questions.

You mentioned 2.4 GHz but iwcopnfig shows only connected to 5 GHz, is that accurate? I mean I prefer 5 GHz of course but did you see anywhere connection at 2.4?
If you look at my ifconfig and interfaces files you will see I have an IP 192.168.95.224 for the ethernet adapter and 192.168.95.225 for the wireless. When the wire is connected I can SSH either adapter, when I disconnect the ethernet I cannot longer ping or access via SSH either IP including the wireless but from the NUC itself I can ping out just fine, what could be so wrong that I have connectivity but cannot see the local network and I can see the internet even though everything is local? the AP is not doing any type of isolation that I'm aware of, I even cleared the ARP/MAC address tables restarting the switch router and same thing

root@nucplayer:~# iwconfig 
wlp2s0    IEEE 802.11  ESSID:"LVN"  
          Mode:Managed  Frequency:5.32 GHz  Access Point: 38:FF:36:13:1A:FC   
          Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:0


eno1      no wireless extensions.


lo        no wireless extensions.


root@nucplayer:~# 
root@nucplayer:~# 
root@nucplayer:~# ifconfig
eno1      Link encap:Ethernet  HWaddr 94:c6:91:1b:02:5f  
          inet addr:192.168.95.224  Bcast:192.168.95.255  Mask:255.255.255.0
          inet6 addr: fe80::96c6:91ff:fe1b:25f/64 Scope:Link
          inet6 addr: 2601:588:4101:a100:96c6:91ff:fe1b:25f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1038 errors:0 dropped:1 overruns:0 frame:0
          TX packets:2482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:156394 (156.3 KB)  TX bytes:229019 (229.0 KB)
          Interrupt:16 Memory:dfc00000-dfc20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:201893 (201.8 KB)  TX bytes:201893 (201.8 KB)


wlp2s0    Link encap:Ethernet  HWaddr 68:ec:c5:2a:25:01  
          inet addr:192.168.95.225  Bcast:192.168.95.255  Mask:255.255.255.0
          inet6 addr: 2601:588:4101:a100:6aec:c5ff:fe2a:2501/64 Scope:Global
          inet6 addr: fe80::6aec:c5ff:fe2a:2501/64 Scope:Link
          inet6 addr: 2601:588:4101:a100:a978:ebd4:411a:3205/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7271273 (7.2 MB)  TX bytes:112125 (112.1 KB)


root@nucplayer:~#

---

### Post by chili555 on 2018-07-23
> When the wire is connected I can SSH either adapter, when I disconnect the ethernet I cannot longer ping or access via SSH either IP including the wireless but from the NUC itself I can ping out just fineI am always very skeptical of any arrangement that connects both wireless and ethernet where both are expected, somehow, to access the internet. Frankly, if you are close to an ethernet cable, use ethernet as it is faster and more secure. If not, use wireless as it is a necessity. 

My own NUC connects flawlessly by ethernet. 

Is the behavior changed at all if you detach the ethernet and reboot, using only wireless?>  iwcopnfig shows only connected to 5 GHz, is that accurate? I mean I prefer 5 GHz of course but did you see anywhere connection at 2.4?You are quite correct. Your wireless card and the AP have negotiated up to 5 gHz and are both happy!

Here is an interesting thread about auto channel select and wht we recommend against it: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection) Why not give yourself the best possible chance at a fast, smooth connection?

---

### Post by luisma31 on 2018-07-23
Adding the networking config

root@nucplayer:/etc/network# cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eno1
iface eno1 inet static
address 192.168.95.224
netmask 255.255.255.0
network 192.168.95.0
broadcast 192.168.95.255
#gateway 192.168.95.1
dns-nameservers 1.1.1.1 8.8.8.8
dns-domain nss.com
dns-search nss.com


auto wlp2s0
iface wlp2s0 inet static
wpa-driver nl80211
wpa-conf /etc/wpa_supplicant.conf
address 192.168.95.225
netmask 255.255.255.0
network 192.168.95.0
broadcast 192.168.95.255
gateway 192.168.95.1
dns-nameservers 1.1.1.1 8.8.8.8
#dns-domain nss.com
#dns-search nss.com

---

### Post by luisma31 on 2018-07-23
rebooting only using wireless, done, not wireless communications, I mean no answer to ping or anything but the NUC has access so it could be the wired interface conflicting? let me test that

---

### Post by chili555 on 2018-07-23
> auto wlp2s0
iface wlp2s0 inet static
wpa-driver nl80211
wpa-conf /etc/wpa_supplicant.conf
address 192.168.95.225
netmask 255.255.255.0
network 192.168.95.0
broadcast 192.168.95.255
gateway 192.168.95.1
dns-nameservers 1.1.1.1 8.8.8.8
#dns-domain nss.com
#dns-search nss.comThat is one busy file!

I suggest:```
auto wlp2s0
iface wlp2s0 inet static
address 192.168.95.225
netmask 255.255.255.0
gateway 192.168.95.1
dns-nameservers 1.1.1.1 8.8.8.8
wpa-ssid LVN
wpa-psk <your_secret_key>

```Where <your_secret_key> is the key in clear text, not the obfuscated version.

---

### Post by luisma31 on 2018-07-23
well after disabling the ethernet the wireless allows me to connect to the NUC somehow I get the feeling IPv6 may be involved I don't know ... 
so you recommend to put the wireless secret in plain text, what about the supplicant file and package? are these needed ?

---

### Post by chili555 on 2018-07-23
I doubt that there is any need to remove them because the interfaces file no longer refers to them.

The interfaces file requires the password in clear text. I understand the implied security hole, but if someone has physical access to your computer, that's really all they need.

---

