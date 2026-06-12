---
title: "Ubuntu won't associate with my router"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by alwbsok on 2006-10-27
My Billion 7401VGP will not communicate with Ubuntu. I'm currently dual-booting from an Inspiron 630m. Ubuntu recognises the wireless card as eth1, and recognises that it's wireless (i.e. you can configure it with iwconfig). My windows partition has no problem.

The router recently replaced a Belkin wireless router. The Belkin router worked perfectly with Ubuntu and Windows, and so, when it died, I tried to configure the Billion router so that no client-side configuration changes were necessary. It succeeded in Windows, but obviously not in Ubuntu.

I have tried the GUI, but that hasn't worked. When I try "iwconfig eth1" in terminal, it gives me this:

eth1      unassociated  ESSID:" "  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It recognises the existence of the network, as I get this from iwlist eth1 scan:

                    Cell 02 - Address: 00:13:D3:6E:92:99
                    ESSID:"benthop"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-18 dBm  
                    Extra: Last beacon: 236ms ago

I've tried these commands:

$ sudo iwconfig eth1 essid benthop
$ sudo iwconfig eth1 key <My key>
$ sudo iwconfig eth1 channel 11
$ sudo iwconfig eth1 ap 00:13:D3:6E:92:99

But none have worked. The changes register in iwconfig, but it still stays "unassociated". Every time I restart, all these settings reset. The GUI, however, manages to keep my settings.

It's not just my wireless card. I've tried two other wireless cards, both recognised under Ubuntu, and they've all had similar problems.

Any help would be great. It may not look like it, but I'm pretty new to Linux. The only reason why I know iwconfig/iwlist is that I have tried to get help before, and they were commands I was asked to run.

---

### Post by wildframe on 2006-10-28
Ditto here as well.

My Billion 7401VGP wired LAN works flawlessly but wireless via my Broadcom bcm4309 on my Dell D800 using ndiswrapper is not working at present. I have managed to get it to a stage where it picks up the correct ESSID and cell address and the wireless client filter sees the Broadcom's mac address but a networking stop/start results in "No DHCPOFFERS received."

Makes no difference for me if I use WEP or not.

Like you I'm flumixed and would be more than pleased to hear from someone who has got their wireless working with the Billion 7401VGP or similar.

---

### Post by alwbsok on 2006-10-31
You say no DHCP offers? Have you tried to connect with a static IP to the router (as opposed to DCHP)? I think I did once, but it didn't work. Maybe I'm just not experienced with it.

---

### Post by wildframe on 2006-11-10
Luckily I also have a D600 Latitude so I was able to swap out its rt2500 for my Broadcom and dispense with the whole ndiswrapper thing. This made detection of my wireless card on Ubuntu very straightforward. However, in the end I had to disable WEP encryption on the router and change the channel to get my D800 to receive DHCP offers from the 7401VGP.

Needless to say that I am typing this over wireless and will have another go at re-enabling the WEP encryption later. :-D

---

### Post by freund on 2006-11-24
> **alwbsok said:**
> My Billion 7401VGP will not communicate with Ubuntu. I'm currently dual-booting from an Inspiron 630m. Ubuntu recognises the wireless card as eth1, and recognises that it's wireless (i.e. you can configure it with iwconfig). My windows partition has no problem.

The router recently replaced a Belkin wireless router. The Belkin router worked perfectly with Ubuntu and Windows, and so, when it died, I tried to configure the Billion router so that no client-side configuration changes were necessary. It succeeded in Windows, but obviously not in Ubuntu.

I have tried the GUI, but that hasn't worked. When I try "iwconfig eth1" in terminal, it gives me this:

eth1      unassociated  ESSID:" "  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It recognises the existence of the network, as I get this from iwlist eth1 scan:

                    Cell 02 - Address: 00:13:D3:6E:92:99
                    ESSID:"benthop"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-18 dBm  
                    Extra: Last beacon: 236ms ago

I've tried these commands:

$ sudo iwconfig eth1 essid benthop
$ sudo iwconfig eth1 key <My key>
$ sudo iwconfig eth1 channel 11
$ sudo iwconfig eth1 ap 00:13:D3:6E:92:99

But none have worked. The changes register in iwconfig, but it still stays "unassociated". Every time I restart, all these settings reset. The GUI, however, manages to keep my settings.

It's not just my wireless card. I've tried two other wireless cards, both recognised under Ubuntu, and they've all had similar problems.

Any help would be great. It may not look like it, but I'm pretty new to Linux. The only reason why I know iwconfig/iwlist is that I have tried to get help before, and they were commands I was asked to run.

WEP is not that secure so I use WPA 
I have a script file on my 630 that I run through sudo.
My ssid is also hidden

WPA script:

#!/bin/bash
PATH=/sbin:/bin:/usr/bin:/usr/sbin/

#Shutting Down:
killall -s SIGUSR1 dhclient
/sbin/ifdown eth1
/usr/bin/killall -s SIGUSR1 wpa_supplicant
#/sbin/modprobe -r ipw2200

#/sbin/modprobe ipw2200
#sleep 1
iwconfig eth1 essid freund
#sleep 1
#iwlist eth1 scan
sleep 2
#/sbin/wpa_supplicant -ddK -ieth1 -c/etc/wpa_supplicant.conf -Dipw
#wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dipw
wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dwext
sleep 3
dhclient eth1
iwconfig
#/sbin/ifconfig

I found that sleep was important for it to work.
Just replace 

wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dwext

with

iwconfig eth1 key <My key>

might work for you

regards
al

---

