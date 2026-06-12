---
title: "Reverting back from Manual network configuration"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by easwars on 2008-11-21
I recently installed Ubuntu 8.04 and I did all the steps that I found online to get my wireless card up and running. I had this network manager applet at the top right of my screen and I could select which network I wanted to connect and everything was fine. Good times :)

Then, I had to configure static IP on my machine and I tried to manually configure it by editing /etc/network/interfaces and /etc/resolv.conf files. I could not get the static IP to work. So I gave up (atleast momentatirily) and wanted to get back to connecting to my wireless as before. But I am unable to do so now.

If I place the mouse pointer near the NM applet, it says "Manual Network Configuration". If I right-click and choose "Edit Wireless Networks" if shows no networks. If I choose manual configuration and enter the network settings, my wireless shows to be in roaming mode.

I tried uninstalling and reinstalling the NM package. But it didnt help.

Can anyone please let me know what I need to do to get back to connecting to wireless networks with ease.

Thanks in advance,
Easwar

---

### Post by superprash2003 on 2008-11-21
post output of /etc/network/interface .. and output of iwconfig

---

### Post by easwars on 2008-11-22
easwars@blackbox:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
auto wlan0

iface eth0 inet dhcp
auto eth0
easwars@blackbox:~$ sudo iwconfig
[sudo] password for easwars: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

easwars@blackbox:~$

---

### Post by superprash2003 on 2008-11-24
your interfaces file looks good.post output of iwlist wlan0 scan

---

### Post by easwars on 2008-11-25
easwars@blackbox:~$ sudo iwlist wlan0 scan
[sudo] password for easwars: 
wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:3A:B3:52
                    ESSID:"navprat"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level=-73 dBm  Noise level=-63 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001d50812181
          Cell 02 - Address: 00:1C:F0:EA:34:49
                    ESSID:"Mucherla"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/100  Signal level=-76 dBm  Noise level=-63 dBm
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001b93871221
          Cell 03 - Address: 00:14:A5:81:BF:C0
                    ESSID:"kondawifi"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=73/100  Signal level=-59 dBm  Noise level=-63 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001d5020e9f5
          Cell 04 - Address: 00:1B:11:5E:34:21
                    ESSID:"An insanely insecure network"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=81/100  Signal level=-51 dBm  Noise level=-63 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001d5090ce73
          Cell 05 - Address: 00:1D:6A:D0:44:85
                    ESSID:"69dtv69"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/100  Signal level=-72 dBm  Noise level=-63 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=0000001d505a14f4
 
easwars@blackbox:~$ 


Thanks
Easwar

---

### Post by superprash2003 on 2008-11-25
ok.. so looks like no harm done with the drivers.. as the above output shows existing wifi networks around you.. so first move to roaming mode and then try looking for available networks in the GUI.you should see them.Enabling Roaming mode( for wlan0 in your case) [http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html](http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html) follow till step 3 ( check "Roaming Mode" instead of unchecking)

---

