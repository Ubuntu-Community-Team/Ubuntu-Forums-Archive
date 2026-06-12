---
title: "BCM43XX Able to Detect - Won't Connect"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by Nrbelex on 2007-05-10
Hi - I have my wireless card up and running. Using the network manager, I have previously used it to connect to a wireless network elsewhere on a corporate WPA system. However at home, I'm unable to connect to our standard WEP network with the correct hex key or any other nearby unsecured  wireless networks. In the system monitor, I see spikes of sent data but 0 received bytes. The card is a BCM43XX series and I used fwcutter to get it running properly.

Help is much appreciated!

~ Brett

---

### Post by Nrbelex on 2007-05-10
Bump...

---

### Post by ripper17 on 2007-05-11
I'm having the same problem. 
On my Laptop, I have a built-in BCM4318 WiFi card. I did 
sudo apt-get bcm43xx-fwcutter
bcm43xx-fwcutter (as supposed to) opens and offers to download the firmware (which it does through wired LAN) - the card shows up. 
BUT: no matter what I try, I'm not able to connect to my WLAN:
- set it to unencrypted to test
- used static IP instead of DHCP
- did 'ifdown eth0' (my wired card)

It can do iwscan and finds the WLAN and it's ESID, but fails to connect. 
Any help would be greatly appreciated

Martin

---

### Post by Aloir on 2007-05-11
Hi there

I'm also having similar problems.

Network is detected (unsecured) with iwlist:

alister@alister-laptop:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:05:5D:F1:70:CA
                    ESSID:"WLANGCHX"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=70/100  Signal level=-80 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 48ms ago


**iwconfig** reveals this:

alister@alister-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"WLANGCHX"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:05:5D:F1:70:CA   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=41/100  Signal level=-80 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifup:

alister@alister-laptop:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:6c:6e:b3
Sending on   LPF/eth1/00:14:a5:6c:6e:b3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


and when I do dhclient:

alister@alister-laptop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0a:e4:df:e4:e0
Sending on   LPF/eth0/00:0a:e4:df:e4:e0
Listening on LPF/eth1/00:14:a5:6c:6e:b3
Sending on   LPF/eth1/00:14:a5:6c:6e:b3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


My interface file looks like this:


auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid WLANGCHX



auto eth1



Like you guys I used fwcutter to get the bcm43xx driver to work, which has got me to this point. Can't seem to get an IP address assigned.

Can anyone help please?

---

### Post by NullHead on 2007-05-11
> **Nrbelex said:**
> Hi - I have my wireless card up and running. Using the network manager, I have previously used it to connect to a wireless network elsewhere on a corporate WPA system. However at home, I'm unable to connect to our standard WEP network with the correct hex key or any other nearby unsecured  wireless networks. In the system monitor, I see spikes of sent data but 0 received bytes. The card is a BCM43XX series and I used fwcutter to get it running properly.

Help is much appreciated!

~ Brett

Do you know what exactly your card is? you can find out bu typing ```
lspci
```and posting the results on hear.

---

### Post by Nrbelex on 2007-05-11
> **NullHead said:**
> Do you know what exactly your card is? you can find out bu typing ```
lspci
```and posting the results on hear.

Yea, it's a Broadcom 4303 (BCM4303). I reset the wireless router and the problem persists.

~ Brett

---

### Post by ghostboy on 2007-05-11
> **Nrbelex said:**
> Hi - I have my wireless card up and running. Using the network manager, I have previously used it to connect to a wireless network elsewhere on a corporate WPA system. However at home, I'm unable to connect to our standard WEP network with the correct hex key or any other nearby unsecured  wireless networks. In the system monitor, I see spikes of sent data but 0 received bytes. The card is a BCM43XX series and I used fwcutter to get it running properly.

Help is much appreciated!

~ Brett


I had the same problem with my BCM4318.  I used this thread to solve my problem.  [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

---

### Post by Nrbelex on 2007-05-11
> **ghostboy said:**
> I had the same problem with my BCM4318.  I used this thread to solve my problem.  [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

Ugh, I saw that but I've been told that's specific to the BCM4318... :mad: 

~ Brett

---

### Post by DarkN00b on 2007-05-11
[Here's]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx") one that should work on almost any BCM 43xx series card. Some users have reported problems but it works for most.

---

### Post by Nrbelex on 2007-05-11
> **DarkN00b said:**
> [Here's]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx") one that should work on almost any BCM 43xx series card. Some users have reported problems but it works for most.

No such luck - same exact problem. How do you uninstall whatever stuff got installed by that script?

~ Brett

---

### Post by Nrbelex on 2007-05-11
I've tried switching to WPA and I've tried disabling security with no luck...

Also, I loaded Feisty off a liveCD and installed fwcutter and I get the same problem...

~ Brett

---

### Post by Annalisa on 2007-12-03
try adding # to make  /etc/network/interfaces like this:

auto lo
iface lo inet loopback

I saw for many it works
I've got the same problem but I'm still looking for an answer, it doesn't work for me...
but, just try

---

