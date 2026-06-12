---
title: "[SOLVED] Wireless U. users: Need your help testing wireless security config's (e.g. P"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by wieman01 on 2006-11-22
Hello to all of you:

I need some users who help me test a few scripts that I have prepared for various wireless (and wired) security settings. Since I do not own an authentication server, I would need others to support me in this matter.

I would appreciate your help very much. I'll post the results here & also mention your contribution: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

For details please refer to that thread where all the various settings (e.g. wpa-driver, wpa-ap-scan, etc.) are explained. Here we go...

**_EAP-PEAP (MSCHAPV2):_**
> auto [COLOR="Olive"]eth1[/COLOR]
iface [COLOR="Olive"]eth1[/COLOR] inet [COLOR="Navy"]dhcp[/COLOR]
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]your_essid[/COLOR]
[COLOR="Navy"]wpa-ap-scan 1[/COLOR]
wpa-eap PEAP
wpa-key-mgmt WPA-EAP
wpa-identity [COLOR="Red"]your_identity[/COLOR]
wpa-password [COLOR="Red"]your_password[/COLOR]
wpa-ca-cert [COLOR="Red"]/etc/cert/ca.pem[/COLOR]
wpa-phase1 [COLOR="Purple"]peaplabel=1[/COLOR]
wpa-phase2 auth=MSCHAPV2
wpa-priority 10

_**EAP-LEAP (with WEP):**_
> auto [COLOR="Olive"]eth1[/COLOR]
iface [COLOR="Olive"]eth1[/COLOR] inet [COLOR="Navy"]dhcp[/COLOR]
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]your_essid[/COLOR]
[COLOR="Navy"]wpa-ap-scan 1[/COLOR]
wpa-eap LEAP
wpa-key-mgmt IEEE8021X
wpa-identity [COLOR="Red"]your_user_name[/COLOR]
wpa-password [COLOR="Red"]your_password[/COLOR]

_**EAP-TTLS (with WEP):**_
> auto [COLOR="Olive"]eth1[/COLOR]
iface [COLOR="Olive"]eth1[/COLOR] inet [COLOR="Navy"]dhcp[/COLOR]
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]your_essid[/COLOR]
[COLOR="Navy"]wpa-ap-scan 1[/COLOR]
wpa-eap TTLS
wpa-key-mgmt IEEE8021X
wpa-anonymous-identity [COLOR="Red"]anonymous_identity[/COLOR]
wpa-identity [COLOR="Red"]your_identity[/COLOR]
wpa-password [COLOR="Red"]your_password[/COLOR]
wpa-phase2 [COLOR="Purple"]auth=PAP[/COLOR] [Also: CHAP, MSCHAP, MSCHAPV2]

_**EAP-FAST (with TKIP/AES):**_
> auto [COLOR="Olive"]eth1[/COLOR]
iface [COLOR="Olive"]eth1[/COLOR] inet [COLOR="Navy"]dhcp[/COLOR]
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]your_essid[/COLOR]
[COLOR="Navy"]wpa-ap-scan 1[/COLOR]
wpa-proto RSN WPA
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt WPA-EAP
wpa-eap FAST
wpa-identity [COLOR="Red"]your_user_name[/COLOR]
wpa-password [COLOR="Red"]your_password[/COLOR]
wpa-phase1 [COLOR="Purple"]fast_provisioning=1[/COLOR]
wpa-pac-file [COLOR="Red"]/path/to/eap-pac-file[/COLOR]
Thanks a lot in advance. Really appreciate your feedback.

---

### Post by wieman01 on 2006-11-22
If you need help, please post your results here.

---

### Post by wieman01 on 2006-11-23
Another BUMP... Last one.

---

### Post by compwiz18 on 2006-12-19
Ok, I stuck a message at the top of my thread, so let us see where that gets us.

---

### Post by usererror on 2006-12-20
Damn, is it too late to help?

I just posted this somewhere else, but here's our network setup that i am still failing at connecting to:

EAP-FAST (using our active directory account info)
Authentication: Open
802.1x
Dynamic WEP

Anyone else have a setup like that?  In our Dell Wireless software those are the settings we put into the software to connect our laptops the the wireless networks...  I hope i'm not too late! ](*,)

---

### Post by wieman01 on 2006-12-21
Repeating my post... But here you go. Please try this:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-group [COLOR="Red"]WEP104 WEP40[/COLOR]
wpa-key-mgmt [COLOR="Red"]IEEE8021X[/COLOR]
wpa-eap [COLOR="Red"]FAST[/COLOR]
wpa-identity [COLOR="Blue"]<your_user_name>[/COLOR]
wpa-password [COLOR="Blue"]<your_password>[/COLOR]
[COLOR="SeaGreen"]wpa-phase1 fast_provisioning=1
wpa-pac-file /path/to/eap-pac-file[/COLOR]
You also need the stuff in 'green'.

---

### Post by usererror on 2006-12-21
I'll be adding that today, and posting back the results, i also posted this in the other thread. :D

Well, hmm, I've given up on the EAP-FAST i think.

I created a new user in our Cisco ACS box and I was successful at getting it to authenticate in a windows box with LEAP...below is a screenshot of that config that works:

[IMG]http://gallery.iametarq.com/misc/.cache/1024x768-winxp-leap.jpg[/IMG]

the odd thing is, i cannot even see on the AP the laptop running linux trying to associate, but if i boot to windows and do it, it sees it just fine.

let me know what you need.  here is my current interfaces file:

```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid xxxxxx
wpa-group WEP104 WEP40
wpa-ap-scan 1
wpa-eap 1
wpa-eap LEAP
wpa-identity myusername
wpa-password mypassword

```

I also wonder if the dhcp timer is not long enough for the authentication.  it takes at least 30 seconds in Windows... I do not know how to increase the time out though...

---

### Post by Frem on 2006-12-21
If you can wait until January 8th, I can get/test a working config with LEAP, WPA2, DHCP, TKPI, and no ESSID broadcast. That wasn't on the list, but hey. The more the marrier, right?

---

### Post by usererror on 2006-12-21
> **Frem said:**
> If you can wait until January 8th, I can get/test a working config with LEAP, WPA2, DHCP, TKPI, and no ESSID broadcast. That wasn't on the list, but hey. The more the marrier, right?

Cool!, but are you talking to me or the original poster? :D

---

### Post by wieman01 on 2006-12-23
> **Frem said:**
> If you can wait until January 8th, I can get/test a working config with LEAP, WPA2, DHCP, TKPI, and no ESSID broadcast. That wasn't on the list, but hey. The more the marrier, right?
Man, be our guest! Would appreciate it, really.

---

### Post by wieman01 on 2006-12-23
> **usererror said:**
> ```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid xxxxxx
wpa-group WEP104 WEP40
wpa-ap-scan 1
wpa-eap 1
wpa-eap LEAP
wpa-identity myusername
wpa-password mypassword

```
I suggest this one for LEAP:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
wpa-ap-scan 1
wpa-eap LEAP
wpa-key-mgmt IEEE8021X
wpa-identity [COLOR="Red"]<your_user_name>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
Could you try?

---

### Post by usererror on 2007-01-03
wieman01,

sorry for the delay, holidays, new year, etc...

anyway i'm back, i'll give that LEAP setup a shot tomorrow at work! :)

---

### Post by wieman01 on 2007-01-04
Great! Appreciate it. Take your time then. :-)

---

### Post by usererror on 2007-01-04
> **wieman01 said:**
> I suggest this one for LEAP:

Could you try?

Tried it finally, no dice. :(  Perhaps we'll find out something when our friend comes back on the 8th!

---

### Post by wieman01 on 2007-01-04
Can you post error messages, etc.? Any idea what could be wrong?

---

### Post by usererror on 2007-01-07
> **wieman01 said:**
> Can you post error messages, etc.? Any idea what could be wrong?

I'm not getting any errors on the screen when it restarts networking, it just says it has no offers from a dhcp server.  i'm not sure where a log would be that would contain these errors, can you point me in a direction to look?  (sorry I'm still learning these details of linux!)

---

### Post by wieman01 on 2007-01-08
You could try this:
> sudo ifup -v [COLOR="Red"]eth1[/COLOR]
Replace [COLOR="Red"]"eth1"[/COLOR] with whatever interface you are using.

---

### Post by usererror on 2007-01-08
Here we go, I've ***-ed out my username and password... nmh450 the SSID is being broadcast and is an A Radio.  We have a G Radio but that SSID is hidden.  Would this being an A radio have any influence?
```

root@B-096229:/home/mtarquini# ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: terminating via ctrl_interface socket /var/run/wpa_supplicant/wlan0 -- OK
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "nmh450" -- OK
wpa_supplicant: wpa-key-mgmt IEEE8021X -- OK
wpa_supplicant: wpa-identity "******" -- OK
wpa_supplicant: wpa-eap LEAP -- OK
wpa_supplicant: wpa-password "******" -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4962
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:de:38:2c:e8
Sending on   LPF/wlan0/00:18:de:38:2c:e8
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
Trying recorded lease 10.15.210.109
PING 10.15.210.1 (10.15.210.1) 56(84) bytes of data.

--- 10.15.210.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntp-server
run-parts: executing /etc/network/if-up.d/ntpdate
Synchronizing clock to ntp.ubuntu.com...
Error : Temporary failure in name resolution
root@B-096229:/home/mtarquini# 

```

hopefully this will help somewhat. :-|

---

### Post by wieman01 on 2007-01-08
It appears that authentication is not the problem. A radio could be the problem since I assume that your laptop support wireless G/B only. Also I am not sure if Ubuntu currently support wireless A... Could you try the other network then? 

If the ESSID is hidden, then you need to set the value of "wpa-ap-scan" to "2".
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]**wpa-ap-scan 2**[/COLOR]
wpa-eap LEAP
wpa-key-mgmt IEEE8021X
wpa-identity [COLOR="Red"]<your_user_name>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
Please post the output once again. As said, authentication as well as encryption seem to be ok. Does the network in question use DHCP or Static IP?

---

### Post by usererror on 2007-01-10
The network in question does run DHCP.

My network card is an A/B/G card (Intel 3945).  All laptops in our campus owned by the organization run A radio wireless to connect to the wireless network.

I will try our hidden G Radio with your suggestion tomorrow and post the result!  Again, sorry for the delays, work has been busy...i can't believe i'm doing work at work! I thought i was there to play with Ubuntu. ;)

I forgot to mention, when I use the iwlist -scanning function, it does return the A Radio SSID's in range.  Would that 'prove' that A radio is supported in Ubuntu?

---

### Post by wieman01 on 2007-01-11
Detecting the network is different from eventually being able to connect to it. Let's give a go anyway. Looking forward to hearing from you. :-)

---

### Post by usererror on 2007-01-15
> **wieman01 said:**
> Detecting the network is different from eventually being able to connect to it. Let's give a go anyway. Looking forward to hearing from you. :-)

[SIZE="7"]YOU ARE AWESOME WIEMAN01!!!!![/SIZE]

[SIZE="5"]LEAP WORKS!!![/SIZE]

Three Million Cheers for him!!

This is my environment:

Network SSID is NOT Broadcast
G Radio (not A radio that I was trying before)
LEAP
Username & Password created on our Cisco ACS server.

I am now connected to my work's HIDDEN SSID SECURE G NETWORK with LEAP

I had to do a networking restart and then ifdown followed by an ifup and it worked!!!  

config used:

```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid xyz123
wpa-ap-scan 2
wpa-eap LEAP
wpa-key-mgmt IEEE8021X
wpa-identity username
wpa-password paSSwoRd

```

and no that is not my SSID and not my password I am using ;)

```

root@B-096229:/home/mtarquini# ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 2 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "xyz123" -- OK
wpa_supplicant: wpa-key-mgmt IEEE8021X -- OK
wpa_supplicant: wpa-identity "username" -- OK
wpa_supplicant: wpa-eap LEAP -- OK
wpa_supplicant: wpa-password "password" -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:de:38:2c:e8
Sending on   LPF/wlan0/00:18:de:38:2c:e8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.40.53.252
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 10.40.53.252
bound to 10.40.52.31 -- renewal in 337631 seconds.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntp-server
run-parts: executing /etc/network/if-up.d/ntpdate
Synchronizing clock to ntp.ubuntu.com...

```

I wonder if the same wireless radio will work using EAP-Fast, I'll have to try that.

The funny thing is that Network-Manager says that I am connected to "Internet"  but hell, I don't care!!! :D

UPDATE:  I did noticed as I rebooted to Windows to do some work that work only allows me to do in Windows that when I returned to Ubuntu the networking daemon Assosciated me to the AP I need, but did not get a DHCP offer.  running

```
sudo dhclient *interface*
```

interface = wlan0 in my case, got an offer after a bit of waiting.  but at least it connects, that's all that matters to me (for now)

---

### Post by wieman01 on 2007-01-15
Excellent... Thanks for helping us indeed. I'll post the results in my HOWTO. That's good news indeed.

If you want to test any other scripts/protocols, you know where you can find me. :-)

---

### Post by Pollywoggy on 2007-01-15
I have a Ralink rt2500 that is built-in on my laptop.  This laptop ran Linspire and Freespire until a few days ago and worked easily without any command-line work.  It worked from Linspire's KDE control interface.

A few days ago I decided to try kubuntu Edgy on this laptop.

The only way I have gotten it to work is by modifying /etc/network/interfaces and adding:

iface ra0 inet dhcp
pre-up iwconfig ra0 essid thepond
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=7
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="passphrase"
pre-up iwpriv ra0 set TxRate=0

Then I activate the wifi interface from KDE and I had to use RaConfig2500 as well.

I tried the new connection manager but it did not work for me, when I try to make the connection the wifi light on the laptop goes dim.

My router is a Linksys WRT54GS running DD-WRT ver 23 SP2 and I am now able to use WPA but not WPA2.  Under Linspire, I could use WEP but not WPA.

---

### Post by usererror on 2007-01-15
Which Network Manager exactly did you try?

---

### Post by Pollywoggy on 2007-01-15
> **usererror said:**
> Which Network Manager exactly did you try?

The one described at the top of this thread:

[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

It seems only RaConfig works for me, but I can use WPA (not WPA2).
If I had to use WEP, I don't know that I could do that in Edgy.  Fortunately, when at home, I can use WPA on the laptop.

---

### Post by Pollywoggy on 2007-01-15
> **Pollywoggy said:**
> The one described at the top of this thread:

[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

It seems only RaConfig works for me, but I can use WPA (not WPA2).
If I had to use WEP, I don't know that I could do that in Edgy.  Fortunately, when at home, I can use WPA on the laptop.


I just tried it again and this time it worked, I connected to my router.

---

### Post by Pollywoggy on 2007-01-15
> **Pollywoggy said:**
> I just tried it again and this time it worked, I connected to my router.

The connection is intermittent, but not if I use RaConfig instead.

---

### Post by usererror on 2007-01-16
> **Pollywoggy said:**
> The connection is intermittent, but not if I use RaConfig instead.

well, you've connected, that's good.  i have not used RaConfig, only Network-Manager and wifiradar before.

---

### Post by wieman01 on 2007-01-16
Usererror:

If you have the chance to test any other of these scripts, that'd be terrific. I will be here to help...

---

### Post by compwiz18 on 2007-01-16
Cool.  Me will be updating connection-manager v2 with LEAP method used above.

---

### Post by wieman01 on 2007-01-16
> **compwiz18 said:**
> Cool.  Me will be updating connection-manager v2 with LEAP method used above.
I hope more stuff will follow soon. We'll keep you posted for sure.

---

### Post by usererror on 2007-01-16
wieman01,

I will definately test out the EAP-FAST with PAC this week.  I just gotta find an open time at work to do it, this week is really busy.  I'd prefer to get EAP-FAST working since I created a new user in our ACS server to test LEAP, and I don't want to keep that in there. :D

Will post back results, I promise!

---

### Post by r4e on 2007-01-16
I'm really encouraged by usererror being able to get LEAP to work. :D I tried to use the script that worked for usererror, but it didn't work. I've unsuccessfully been trying to get a LEAP authenticated connection to our campus network for quite a while. ](*,) I did succeed in getting a WPA2 connection at home based on wieman01's excellent tutorial, so the wext driver seems to be working fine for my ipw2200 card.

I think there are two possible problems interfering:

1. In addition to LEAP authentication, our access points are configured to be WPA or WPA2 encrypted with TKIP or CCMP (iwlist scan provided below). Based on this, here's the script that I think should work:

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid campusnet
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP
wpa-eap LEAP
wpa-key-mgmt IEEE8021X
wpa-identity username
wpa-password password

(I've tried several other combinations with wpa-proto, wpa-pairwise, and wpa-group with no luck.)

I get the same problem that usererror was having with no dhcp offers:

```

root@caiman:/etc/network# ifup -v eth1
Configuring interface eth1=eth1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.eth1.pid -i eth1 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/eth1
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "campusnet" -- OK
wpa_supplicant: wpa-pairwise TKIP CCMP -- OK
wpa_supplicant: wpa-group TKIP -- OK
wpa_supplicant: wpa-key-mgmt IEEE8021X -- OK
wpa_supplicant: wpa-proto RSN -- OK
wpa_supplicant: wpa-identity "username" -- OK
wpa_supplicant: wpa-eap LEAP -- OK
wpa_supplicant: wpa-password "password" -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:1a:99:d0
Sending on   LPF/eth1/00:13:ce:1a:99:d0
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/50guarddog
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
Synchronizing clock to ntp.ubuntu.com...

```

```

                    Cell 01 - Address: 00:0E:38:FC:11:CF
                    ESSID:"campusnet"
                    Protocol:IEEE 802.11a
                    Mode:Master
                    Channel:149
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1X
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1X
                    Extra: Last beacon: 8088ms ago
Cell 02 - Address: 00:0E:38:FC:09:60
                    ESSID:"campusnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=62/100  Signal level=-63 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1X
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1X
                    Extra: Last beacon: 7916ms ago

```

2) The campus has both A and B/G radio access points, but they all have the same broadcasted ssids. Seeing as usererror had a problem with A radio, I think my laptop could be trying to associate with the A radio and failing instead of trying the B/G radio access point. Does anyone know if there is a way to specify a MAC address or channel to associate with in the interfaces script?

Any suggestions would be much appreciated. Thanks!

---

### Post by wieman01 on 2007-01-17
Your script seems ok, however, pay attention to the lines in [COLOR="Blue"]blue[/COLOR]. I suspect the same thing, your PC may try to associate with the A network.

You could add this:
> auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid campusnet
[COLOR="Red"]**wpa-bssid 00:0E:38:FC:09:60**[/COLOR]
wpa-ap-scan 1
[COLOR="Blue"]wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP[/COLOR]
wpa-eap LEAP
wpa-key-mgmt IEEE8021X
wpa-identity username
wpa-password password
Simply add your preferred MAC address and restart the network.

---

### Post by wieman01 on 2007-01-17
Deleted...

---

### Post by usererror on 2007-01-17
> **wieman01 said:**
> Your script seems ok. I suspect the same thing, your PC may try to associate with the A network.

I agree, after all my attempts it was the A Radio that was throwing the whole thing off!  Another tip that helped me, add the gnome network applet to your tray for your wireless interface...that why once the script DOES associate you'll see the signal strength shown, even if you don't get a dhcp offer, if you see signal strength but don't get a dhcp offer just run the 'dhclient wlan0' (your interface may not be wlan0) and it should get you an IP the 2nd time around.

---

### Post by Pollywoggy on 2007-01-17
This is what is working for me on my laptop.  My router is a Linksys WRT54GS but with DD-WRT instead of the OEM firmware and the wifi on my laptop is a Ralink rt2500.

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
gateway 192.168.1.1

iface ra0 inet dhcp
network 192.168.1.0
broadcast 192.168.1.255
dns-nameservers 192.168.1.1
wpa-driver wext
wpa-conf managed
wpa-ssid <myssid> 
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <mykey>


I am not sure what I would do if I were away from home and could not use WPA.  I suppose I would have to get some additional configs for WEP and for no encryption.  The few times I have had to do without encryption in wifi I have used SSH tunnels.

Is it time for me to replace the wifi router with a newer model?

---

### Post by wieman01 on 2007-01-17
> **Pollywoggy said:**
> I am not sure what I would do if I were away from home and could not use WPA.  I suppose I would have to get some additional configs for WEP and for no encryption.  The few times I have had to do without encryption in wifi I have used SSH tunnels.
Basically that's what you would have to do if you use this approach. If you happen to have a mobile computer, you had better install network-manager or wifi-radar.
> **Pollywoggy said:**
> Is it time for me to replace the wifi router with a newer model?
If WPA2 is the problem, no, you don't. The Linux driver for Ralink (Serialmonkey?) is insufficient and does not support WPA2 as far as I know. You either stay with WPA1 or install your card using "ndiswrapper" and the latest Windows driver for your card.

---

### Post by Pollywoggy on 2007-01-17
> **wieman01 said:**
> Basically that's what you would have to do if you use this approach. If you happen to have a mobile computer, you had better install network-manager or wifi-radar.

If WPA2 is the problem, no, you don't. The Linux driver for Ralink (Serialmonkey?) is insufficient and does not support WPA2 as far as I know. You either stay with WPA1 or install your card using "ndiswrapper" and the latest Windows driver for your card.

Thanks for the explanation.  My router does WPA2 though some of the encryption options are not supported, only AES and/or TKIP.  I don't think it will hide the SSID either.

I will stay with WPA1 so I don't have to mess with ndiswrapper.

---

### Post by wieman01 on 2007-01-17
> **Pollywoggy said:**
> Thanks for the explanation.  My router does WPA2 though some of the encryption options are not supported, only AES and/or TKIP.  I don't think it will hide the SSID either.
No problem, my pleasure. AES and TKIP are the only types of encryption supported by WPA. WPA2 uses AEP, WPA1 uses TKIP. WPA is a framework for authentication & encryption whereas AES & TKIP refer to only one aspect of it, namely encryption. 
> **Pollywoggy said:**
> I will stay with WPA1 so I don't have to mess with ndiswrapper.
That's probably a smart idea. :-) It can be quite nasty.

---

### Post by Pollywoggy on 2007-01-17
My router does not seem to know what RCN and CCMP are.  It would seem from what you said in your reply that they have nothing to do with encryption.

BTW I just installed wifi-radar and reinstalled network-manager, which was removed when I installed something else.  I will try to compile those packages myself so that they won't be removed later because of conflicting dependencies; this sometimes works, sometimes not.

Will I need to manually edit /etc/network/interfaces so that I can use WEP or no encryption if that becomes necessary?  If I have to use an unencrypted wifi, I will use an SSH tunnel to my home machine.

---

### Post by wieman01 on 2007-01-17
> **Pollywoggy said:**
> My router does not seem to know what RCN and CCMP are.  It would seem from what you said in your reply that they have nothing to do with encryption.
It's more complicated than that... RSN stands for WPA2 and uses AES as encryption. CCMP refers to AES...  If you want to know more about it, please read this:

[http://en.wikipedia.org/wiki/IEEE_802.11i]("http://en.wikipedia.org/wiki/IEEE_802.11i")

You can use GNOME's networking applet for WEP.

---

### Post by usererror on 2007-01-17
Alrighty, here's my update on EAP-FAST, everything looks good but i get an error here on 'ifup -v wlan0'

```

root@B-096229:/etc/network# ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 2 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "blaSSID" -- OK
wpa_supplicant: wpa-group WEP104 WEP40 -- OK
wpa_supplicant: wpa-key-mgmt IEEE8021X -- OK
wpa_supplicant: wpa-identity "blauser" -- OK
**wpa_supplicant: wpa-eap FAST -- FAIL**
wpa_supplicant: wpa-password "blapassword" -- OK
wpa_supplicant: wpa-phase1 "fast_provisioning=1" -- OK
wpa_supplicant: wpa-pac-file "/etc/network/certnew.cer" -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:de:38:2c:e8
Sending on   LPF/wlan0/00:18:de:38:2c:e8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 10.15.210.124
PING 10.15.210.1 (10.15.210.1) 56(84) bytes of data.

```


/etc/network/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid XXXXXX
wpa-ap-scan 2
wpa-group WEP104 WEP40
wpa-key-mgmt IEEE8021X
wpa-eap FAST
wpa-identity XXXXXX
wpa-password XXXXXX
wpa-phase1 fast_provisioning=1
wpa-pac-file /etc/network/certnew.cer

```

Again, I am using the hidden SSID, since it's the G Radio, the only Radio with broadcast SSID is A Band.

---

### Post by wieman01 on 2007-01-17
> **usererror said:**
> /etc/network/interfaces:
```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid XXXXXX
wpa-ap-scan 2
wpa-group WEP104 WEP40
wpa-key-mgmt IEEE8021X
wpa-eap FAST
wpa-identity XXXXXX
wpa-password XXXXXX
wpa-phase1 fast_provisioning=1
wpa-pac-file /etc/network/certnew.cer

```

Again, I am using the hidden SSID, since it's the G Radio, the only Radio with broadcast SSID is A Band.
Please try this:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 2[/COLOR]
[COLOR="DarkGreen"]wpa-proto RSN WPA
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP[/COLOR]
[COLOR="Red"]wpa-key-mgmt WPA-EAP[/COLOR]
wpa-eap FAST
wpa-identity [COLOR="Red"]<your_user_name>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
wpa-phase1 fast_provisioning=1
wpa-pac-file /etc/network/certnew.cer
Authentication is WPA-EAP (FAST)... What encryption are you using? TKIP, AES?

---

### Post by usererror on 2007-01-17
We are using WEP with open authentication + the EAP-FAST.  I'll take a screenshot tomorrow of the windows config and also try the code above tomorrow too.

---

### Post by r4e on 2007-01-17
> **wieman01 said:**
> Your script seems ok, however, pay attention to the lines in [COLOR="Blue"]blue[/COLOR]. I suspect the same thing, your PC may try to associate with the A network.

Thanks for the suggestion, wieman, but still no luck. I added the network manager applet to my panel as usererror had suggested and it seems that my network card isn't associating with the access point even with the wpa-bssid line. I'm going to try to find a spot on campus where the B/G radio is stronger than the A radio signal to see if that helps, but I might not have time until the weekend.


I'll keep working at this and if I succeed I'll post the script here.

---

### Post by usererror on 2007-01-18
Alrighty,

I get a fail on **wpa-key-mgmt EAP-WPA**

I can't get to my webserver today (probably iced over) so i am attaching a screenshot from windows using the forum utility, which i've never done before...

Hopefully that helps :D

---

### Post by wieman01 on 2007-01-18
> **usererror said:**
> Alrighty,

I get a fail on **wpa-key-mgmt EAP-WPA**

I can't get to my webserver today (probably iced over) so i am attaching a screenshot from windows using the forum utility, which i've never done before...

Hopefully that helps :D
I made a typo... Guess I meant:
> wpa-key-mgmt WPA-EAP
Could you set encryption to TKIP or AES rather than WEP? Otherwise I'll change the script...

---

### Post by usererror on 2007-01-18
Sadly I cannot change the encryption.  it's already deployed to the 120 access points we have in the building. ;)

I'll post my results tomorrow with your minor change you had me make.

---

### Post by wieman01 on 2007-01-19
> **usererror said:**
> Sadly I cannot change the encryption.  it's already deployed to the 120 access points we have in the building. ;)

I'll post my results tomorrow with your minor change you had me make.
Makes sense... :-)

So maybe give this a go:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 2[/COLOR]
[COLOR="DarkGreen"]wpa-proto RSN WPA
wpa-pairwise **CCMP TKIP WEP104 WEP40**
wpa-group **CCMP TKIP WEP104 WEP40**[/COLOR]
[COLOR="Red"]wpa-key-mgmt WPA-EAP[/COLOR]
wpa-eap FAST
wpa-identity [COLOR="Red"]<your_user_name>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
wpa-phase1 fast_provisioning=1
wpa-pac-file /etc/network/certnew.cer

---

### Post by usererror on 2007-01-19
tried it, got an error:

```
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 2 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "XXXXX" -- OK
wpa_supplicant: wpa-pairwise CCMP TKIP WEP104 WEP40 -- FAIL
wpa_supplicant: wpa-group CCMP TKIP WEP104 WEP40 -- OK
wpa_supplicant: wpa-key-mgmt WPA-EAP -- OK
wpa_supplicant: wpa-proto RSN WPA -- OK
wpa_supplicant: wpa-identity "XXXXXX" -- OK
**wpa_supplicant: wpa-eap FAST -- FAIL**
wpa_supplicant: wpa-password "XXXXX" -- OK
wpa_supplicant: wpa-phase1 "fast_provisioning=1" -- OK
wpa_supplicant: wpa-pac-file "/etc/network/certnew.cer" -- OK
wpa_supplicant: enabling network block 0 -- OK

```

we're getting closer!!  I hope :)

---

### Post by wieman01 on 2007-01-19
Mmm... That's a tough one. What happens if you uncomment this line:
> #wpa-eap FAST

---

### Post by usererror on 2007-01-19
> **wieman01 said:**
> Mmm... That's a tough one. What happens if you uncomment this line:

Doh, ok i miss-bolded the previous post.  originally i got this today:

```

wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 2 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "XXXXX" -- OK
**wpa_supplicant: wpa-pairwise CCMP TKIP WEP104 WEP40 -- FAIL**
wpa_supplicant: wpa-group CCMP TKIP WEP104 WEP40 -- OK
wpa_supplicant: wpa-key-mgmt WPA-EAP -- OK
wpa_supplicant: wpa-proto RSN WPA -- OK
wpa_supplicant: wpa-identity "XXXXXX" -- OK
**wpa_supplicant: wpa-eap FAST -- FAIL**
wpa_supplicant: wpa-password "XXXXX" -- OK
wpa_supplicant: wpa-phase1 "fast_provisioning=1" -- OK
wpa_supplicant: wpa-pac-file "/etc/network/certnew.cer" -- OK
wpa_supplicant: enabling network block 0 -- OK

```

now if i comment out the line:

wpa-eap-FAST 

in interfaces i get this:

```

wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 2 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "XXXXX" -- OK
**wpa_supplicant: wpa-pairwise CCMP TKIP WEP104 WEP40 -- FAIL**
wpa_supplicant: wpa-group CCMP TKIP WEP104 WEP40 -- OK
wpa_supplicant: wpa-key-mgmt WPA-EAP -- OK
wpa_supplicant: wpa-proto RSN WPA -- OK
wpa_supplicant: wpa-identity "XXXXXX" -- OK
wpa_supplicant: wpa-password "XXXXX" -- OK
wpa_supplicant: wpa-phase1 "fast_provisioning=1" -- OK
wpa_supplicant: wpa-pac-file "/etc/network/certnew.cer" -- OK
wpa_supplicant: enabling network block 0 -- OK

```

---

### Post by wieman01 on 2007-01-19
That's odd... Would you mind posting your entire "/etc/network/interfaces" once again? It might be that we are missing something.

---

### Post by usererror on 2007-01-19
> **wieman01 said:**
> That's odd... Would you mind posting your entire "/etc/network/interfaces" once again? It might be that we are missing something.

No Problem here it is.

```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid XXXXXX
wpa-ap-scan 2
wpa-proto RSN WPA
wpa-pairwise CCMP TKIP WEP104 WEP40
wpa-group CCMP TKIP WEP104 WEP40
wpa-key-mgmt WPA-EAP
#wpa-eap FAST
wpa-identity XXXXXX
wpa-password XXXXXX
wpa-phase1 fast_provisioning=1
wpa-pac-file /etc/network/certnew.cer

```

don't stress too much...i am hoping to be leaving work by 1pm today for the weekend.  :rolleyes:

---

### Post by wieman01 on 2007-01-19
Oh well... I checked the man-pages a minute ago and I am not entirely sure EAP-FAST is supported after all. Seems we have got to stop here as fast as that protocol is concerned. Running out of ideas here. :-(

---

### Post by usererror on 2007-01-19
> **wieman01 said:**
> Oh well... I checked the man-pages a minute ago and I am not entirely sure EAP-FAST is supported after all. Seems we have got to stop here as fast as that protocol is concerned. Running out of ideas here. :-(

hey, that's not a problem.  We got LEAP working!  And that will work for me! :D

Now, what I'd really like is for Ubuntu to support the A Radio someday. ;)

---

### Post by wieman01 on 2007-01-19
> **usererror said:**
> hey, that's not a problem.  We got LEAP working!  And that will work for me! :D

Now, what I'd really like is for Ubuntu to support the A Radio someday. ;)
True... But I was convinced it was supported... Anyway, let's not cry over spilt milk. Appreciate your effort a lot, man. Nice working with you.

---

### Post by compwiz18 on 2007-01-19
Just a comment - if you go to the wpa_supplicant website:

> Supported EAP methods (IEEE 802.1X Supplicant)

    * EAP-TLS
    * EAP-PEAP/MSCHAPv2 (both PEAPv0 and PEAPv1)
    * EAP-PEAP/TLS (both PEAPv0 and PEAPv1)
    * EAP-PEAP/GTC (both PEAPv0 and PEAPv1)
    * EAP-PEAP/OTP (both PEAPv0 and PEAPv1)
    * EAP-PEAP/MD5-Challenge (both PEAPv0 and PEAPv1)
    * EAP-TTLS/EAP-MD5-Challenge
    * EAP-TTLS/EAP-GTC
    * EAP-TTLS/EAP-OTP
    * EAP-TTLS/EAP-MSCHAPv2
    * EAP-TTLS/EAP-TLS
    * EAP-TTLS/MSCHAPv2
    * EAP-TTLS/MSCHAP
    * EAP-TTLS/PAP
    * EAP-TTLS/CHAP
    * EAP-SIM
    * EAP-AKA
    * EAP-PSK
    * **EAP-FAST**
    * EAP-PAX
    * EAP-SAKE
    * EAP-GPSK (experimental)
    * LEAP (note: requires special support from the driver)

however, the newest version if 0.5.7, and Ubuntu Edgy's is 0.5.4-5, so it may only be supported in the newer vesion.

---

### Post by wieman01 on 2007-01-20
> **compwiz18 said:**
> However, the newest version if 0.5.7, and Ubuntu Edgy's is 0.5.4-5, so it may only be supported in the newer vesion.
Ok, that's where the confusion may come from. Could you post the link where you found this information? "http://hostap.epitest.fi" seems to be a dead link.

---

### Post by compwiz18 on 2007-01-20
Got the link from google, search for wpa_supplicant, although I had to used the cached page - the link was dead for me too.

---

### Post by usererror on 2007-01-24
hmmm, I just read the last few posts, been busy with work.  Wieman, do you want me to try to install this latest version of wpa_supplicant and give it another shot?

And it was a pleasure working with you as well!  Sorry I was delayed at times in posting my updates.

---

### Post by wieman01 on 2007-01-24
> **usererror said:**
> hmmm, I just read the last few posts, been busy with work.  Wieman, do you want me to try to install this latest version of wpa_supplicant and give it another shot?
You could try that, however, the website has been down for quite a number of days now. No idea from where you would get the latest latest version of wpa-supplicant. But I'd give it a go. If you find it please post the link.

---

### Post by compwiz18 on 2007-01-24
> **wieman01 said:**
> You could try that, however, the website has been down for quite a number of days now. No idea from where you would get the latest latest version of wpa-supplicant. But I'd give it a go. If you find it please post the link.
Got it.

A search for wpa_supplicant-0.5.7.tar.gz led to [http://forums.speedguide.net/showthread.php?t=214543](http://forums.speedguide.net/showthread.php?t=214543) which led to [http://downloads.openwrt.org/sources/](http://downloads.openwrt.org/sources/), where I took the liberty of obtaining it.

---

### Post by usererror on 2007-01-24
Awesome!  Thanks for the attachment.  I've downloaded it.  I will try to get it installed on my laptop tomorrow sometime.

---

### Post by compwiz18 on 2007-01-24
No problem.  Good luck with compiling/installing.

---

### Post by wieman01 on 2007-01-25
Still it looks to me as if this version does not support EAP-FAST. Any idea if this is the latest version around?

---

### Post by compwiz18 on 2007-01-25
It _says_ 0.5.7 ,which is supposedly the newest version, however I was unable to find an md5sum to verify this.  The source isn't the most reliable.

---

### Post by newcoventry on 2007-01-25
Do you need any help with results for PEAP with GTC?

This is my current set-up for my /etc/wpa_supplicant.conf
The SSID is hidden.

network={
        ssid="SSID Name"
        proto=RSN
        key_mgmt=WPA-EAP
        pairwise=CCMP
        eap=PEAP
        identity="domain\username"
        password="**********"
}

---

### Post by wieman01 on 2007-01-25
> **newcoventry said:**
> Do you need any help with results for PEAP with GTC?

This is my current set-up for my /etc/wpa_supplicant.conf
The SSID is hidden.

network={
        ssid="SSID Name"
        proto=RSN
        key_mgmt=WPA-EAP
        pairwise=CCMP
        eap=PEAP
        identity="domain\username"
        password="**********"
}
Excellent, buddy. I'll update my thread. Thanks a lot.

---

### Post by compwiz18 on 2007-01-25
> **wieman01 said:**
> Excellent, buddy. I'll update my thread. Thanks a lot.
And I'll update my program.

---

### Post by newcoventry on 2007-01-26
Glad to hear it that the configuration has been added.
Things have been running a bit sketchy with this configuration here.  We think the root of it is the older version of wpasupplicant in the repositories.  We are working on compiling the latest version in the hopes it sorts itself out.
Any tips on compiling wpa_supplicant 0.5.7?

---

### Post by wieman01 on 2007-01-26
> **newcoventry said:**
> Glad to hear it that the configuration has been added.
Things have been running a bit sketchy with this configuration here.  We think the root of it is the older version of wpasupplicant in the repositories.  We are working on compiling the latest version in the hopes it sorts itself out.
Any tips on compiling wpa_supplicant 0.5.7?
That's a likely theory... I have not tried the latest version though since there is nothing I could do with it at this stage. But if you need any kind of help, just post your problems here. 

Does your PEAP script run well then or not?

---

### Post by newcoventry on 2007-01-26
We have no issues with this script once it connects, but there is a considerable lag time in between shutting down the machine and reconnecting.  Based on our research here the bug is referenced on a few pages (all of which are sadly offline at the moment) you can read the cache page here: 
[http://72.14.203.104/search?q=cache:n58bs3FYDJ0J:lists.shmoo.com/pipermail/hostap/2006-August/013868.html+wpasupplicant+disconnect+bug&hl=en&gl=us&ct=clnk&cd=1&client=firefox-a](http://72.14.203.104/search?q=cache:n58bs3FYDJ0J:lists.shmoo.com/pipermail/hostap/2006-August/013868.html+wpasupplicant+disconnect+bug&hl=en&gl=us&ct=clnk&cd=1&client=firefox-a)

Our hope is that 0.5.7 will to fix this issue.  Our errors on compiling occur with linking to OpenSSL because apparently it is installed in a non-standard location.  We are looking for the Libraries and the Includes for OpenSSL before we can compile and install 0.5.7 and test to see if it fixes the error referenced on the above page.
If you know where we can link to the libraries or includes for openssl that would be most helpful.  Then we can ensure that the issue is a wpasupplicant 0.5.4 issue.
Thanks again!

---

### Post by mjbruder on 2007-01-26
You need to install libssl-dev to get 0.5.7 to compile correctly.

sudo apt-get install libssl-dev

---

### Post by mjbruder on 2007-01-26
I just tested the PEAP/GTC configuration mentioned above using wpa_supplicant 0.5.7, and it works flawlessly.  Now the only issue is that I don't have any of the nice startup scripts because it was a manual installation.  

When I ran the installation it put the wpa_supplicant files in /usr/local/sbin.  Any ideas on how I could edit Ubuntu's startup scripts (i.e. /etc/init.d/wpa-ifupdown, and /sbin/wpa_action) to automatically start wpa_supplicant on boot?

---

### Post by wieman01 on 2007-01-26
> **mjbruder said:**
> I just tested the PEAP/GTC configuration mentioned above using wpa_supplicant 0.5.7, and it works flawlessly.  Now the only issue is that I don't have any of the nice startup scripts because it was a manual installation.  

When I ran the installation it put the wpa_supplicant files in /usr/local/sbin.  Any ideas on how I could edit Ubuntu's startup scripts (i.e. /etc/init.d/wpa-ifupdown, and /sbin/wpa_action) to automatically start wpa_supplicant on boot?
If you don't mind, could you use the HOWTO in my signature and use this script:
> auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-eap PEAP
wpa-key-mgmt WPA-EAP
wpa-identity [COLOR="Red"]<your_identity>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
Would be nice to have a valid PEAP script... ESSID is hidden in this case. Change this line if broadcast is enabled:
> wpa-ap-scan 1
Your [COLOR="Blue"]wpa-driver[/COLOR] (wext) and [COLOR="Blue"]network interface[/COLOR] (eth1) may be different though. Check out the HOWTO.

---

### Post by newcoventry on 2007-01-27
I am going to give this a test when I am at work on Monday with the script you have referenced.  The challenge I have is that I move between multiple SSID's
My wpa_supplicant.conf works great with the below settings

```

network={
        ssid="SSIDName"
        key_mgmt=NONE
        wep_key0=KEY
        disabled=1
}

network={
        ssid="HIDDENSSID"
        proto=RSN
        key_mgmt=WPA-EAP
        pairwise=CCMP
        eap=PEAP
        identity="domain\username"
        password="********"
}

```
Is there any way to easily move between these two with your script?

---

### Post by wieman01 on 2007-01-29
My script is not suitable if you plan to switch between networks. Guess your approach is much better with regard to this.

---

### Post by avelala on 2007-01-30
Hey Weiman,

I'm completely new to Ubuntu linux, and i walked through your HowTo and it failed to work, i'm running the same network that mjbruder is running, and in the process of doing your tutorial, i made the interface.conf read-only, so i can no longer edit it.. could you walk me through this again?

---

### Post by usererror on 2007-01-30
> **avelala said:**
> Hey Weiman,

I'm completely new to Ubuntu linux, and i walked through your HowTo and it failed to work, i'm running the same network that mjbruder is running, and in the process of doing your tutorial, i made the interface.conf read-only, so i can no longer edit it.. could you walk me through this again?

to make your interfaces non-read only again try this:

```
sudo chmod 777 /etc/network/interfaces
```

that should make it write-able to everyone, not that you want it but at least for now...you'll be able to edit it.

---

### Post by avelala on 2007-01-30
that worked, and i fixed that conf file, but i'm using network manager to connect to wireless, and somehow during the tutorial, i ended up disabling the wireless option for network manager.... help please... 

if that doesn't work, then i could like to know more about this wpa_supplicant program and how to activate and run it...  everytime i've tried, it doesn't work

---

### Post by wieman01 on 2007-01-31
> **avelala said:**
> that worked, and i fixed that conf file, but i'm using network manager to connect to wireless, and somehow during the tutorial, i ended up disabling the wireless option for network manager.... help please... 

if that doesn't work, then i could like to know more about this wpa_supplicant program and how to activate and run it...  everytime i've tried, it doesn't work
What card have you got? Second, please post the contents of "/etc/network/interfaces", so that we can help.

_**EDIT:**_
And please use the other thread for support... This one refers to another topic.

---

### Post by wieman01 on 2007-01-31
Usererror:

You can download the latest verion [here]("http://hostap.epitest.fi/releases/wpa_supplicant-0.5.7.tar.gz"). The link seems to be working again. The documentation says that EAP-FAST should be supported. Perhaps you can give this one a go & try the script on the first page. It should be ok as far as I can tell.

---

### Post by mjbruder on 2007-01-31
> **wieman01 said:**
> If you don't mind, could you use the HOWTO in my signature and use this script:

Would be nice to have a valid PEAP script... ESSID is hidden in this case. Change this line if broadcast is enabled:

Your [COLOR="Blue"]wpa-driver[/COLOR] (wext) and [COLOR="Blue"]network interface[/COLOR] (eth1) may be different though. Check out the HOWTO.

wieman01,

I tested your above script and it works great for our PEAP network (newcoventry & I work together).  I was also able to use your script to edit my wpa_supplicant.conf (See Below) for successful results.

newcoventry,

If you want to switch between home and work, you can use the following wpa_supplicant.conf and set priorities on your networks.  As far as I can tell, the higher the number the higher the priority.

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
update_config=1

network={
        ssid=[COLOR="Red"]<your ssid>[/COLOR]
        scan_ssid=1
        proto=RSN
        pairwise=CCMP
        group=CCMP
        eap=PEAP
        key_mgmt=WPA-EAP
        identity=[COLOR="Red"]<your username>[/COLOR]
        password=[COLOR="Red"]<your password>[/COLOR]
        priority=2
}

network={
        ssid=[COLOR="Red"]<your ssid>[/COLOR]
        key_mgmt=NONE
        wep_key0=[COLOR="Red"]<your wep key>[/COLOR]
        wep_tx_keyidx=0
        priority=1
}

---

### Post by wieman01 on 2007-01-31
Man, that's good news. Thanks for the feedback. I am pretty sure a lot of people will appreciate it. I'll update my HOWTO soon and include a reference to your post.

---

### Post by usererror on 2007-02-02
> **wieman01 said:**
> Usererror:

You can download the latest verion [here]("http://hostap.epitest.fi/releases/wpa_supplicant-0.5.7.tar.gz"). The link seems to be working again. The documentation says that EAP-FAST should be supported. Perhaps you can give this one a go & try the script on the first page. It should be ok as far as I can tell.

Should I remove the existing wpa_supplicant before I try to compile & install this new one?  nah....... i'm too impatient.  will try it now.

---

### Post by wieman01 on 2007-02-02
> **usererror said:**
> Should I remove the existing wpa_supplicant before I try to compile & install this new one?  nah....... i'm too impatient.  will try it now.
I'd remove the existing version... Simply use Synaptic to remove it, won't do any harm. :-) You'll get there soon enough.

---

### Post by usererror on 2007-02-02
> **wieman01 said:**
> I'd remove the existing version... Simply use Synaptic to remove it, won't do any harm. :-) You'll get there soon enough.

oh god. 

i'm looking at the readme file.  apparently there's no running just ./config you have to make the .config file yourself.  this is where i get shaky...  i tried just putting ALL the options they had in the readme in the .config file and then doing 'make' but i got a bunch of errors at the end.

on a non-related-note my laptop is suddenly REALLY slow today in Ubuntu.  all i did was add some new gnome themes last time i used it.  *sigh.

---

### Post by wieman01 on 2007-02-02
> **usererror said:**
> oh god. 

i'm looking at the readme file.  apparently there's no running just ./config you have to make the .config file yourself.  this is where i get shaky...  i tried just putting ALL the options they had in the readme in the .config file and then doing 'make' but i got a bunch of errors at the end.

on a non-related-note my laptop is suddenly REALLY slow today in Ubuntu.  all i did was add some new gnome themes last time i used it.  *sigh.
Ouch... no guarantee it works with the current version of your kernel. Perhaps it's worthwhile opening another thread to ask other users for help. Not really my area of expertise either...

---

### Post by usererror on 2007-02-02
yup, made a new thread: [http://www.ubuntuforums.org/showthread.php?t=351706](http://www.ubuntuforums.org/showthread.php?t=351706)

---

### Post by acconrad on 2007-03-15
Hey Wieman, you told me to check this thread out, so I have 2 questions for you:

1. Can I create another id such as eth2 so that way I can have a wireless connection for my open network and a wireless connection for my secured network?

2. Which one of these scripts should I run for my situation (see the bottom of page 25 on your helper thread)...WPA1/TKIP/EAP or EAP-TTLS (because the connection is 8021X)?

---

### Post by wieman01 on 2007-03-15
Hello Acconrad, 

1. No, you cannot have two connections at a time. If you want to switch between 2 networks, you had better install NetworkManager.
2. "EAP-TTLS (with WEP)" is the one on page 1. Can you describe the TTLS network in more detail? What phase 2 authentication are you using? And is the encryption reall 802.1X (=WEP)?

Let me know... I try to tailor a script for you.

---

### Post by acconrad on 2007-03-18
[https://wiki.brown.edu/confluence/display/CISDOC/Wireless+-+Connecting+to+the+Brown-Secure+Wireless+Network+with+Windows](https://wiki.brown.edu/confluence/display/CISDOC/Wireless+-+Connecting+to+the+Brown-Secure+Wireless+Network+with+Windows)

[https://wiki.brown.edu/confluence/display/CISDOC/Wireless+-+Connecting+to+the+Brown-Secure+Wireless+Network+with+a+Mac](https://wiki.brown.edu/confluence/display/CISDOC/Wireless+-+Connecting+to+the+Brown-Secure+Wireless+Network+with+a+Mac)

that describes our network...at one point it looks like EAP/TKIP (Windows), and yet other times it also looks like 8021X/TTLS (Mac)...any ideas?

---

### Post by wieman01 on 2007-03-19
> **acconrad said:**
> [https://wiki.brown.edu/confluence/display/CISDOC/Wireless+-+Connecting+to+the+Brown-Secure+Wireless+Network+with+Windows](https://wiki.brown.edu/confluence/display/CISDOC/Wireless+-+Connecting+to+the+Brown-Secure+Wireless+Network+with+Windows)

[https://wiki.brown.edu/confluence/display/CISDOC/Wireless+-+Connecting+to+the+Brown-Secure+Wireless+Network+with+a+Mac](https://wiki.brown.edu/confluence/display/CISDOC/Wireless+-+Connecting+to+the+Brown-Secure+Wireless+Network+with+a+Mac)

that describes our network...at one point it looks like EAP/TKIP (Windows), and yet other times it also looks like 8021X/TTLS (Mac)...any ideas?
SecureW2 seems to be designed for Windows platforms. I don't think wpa-supplicant supports it. Read [this]("http://www.securew2.com/").

As for the other one I believe it is TTLS with PAP and WEP including a server certificate. Please see my next post.

---

### Post by wieman01 on 2007-03-19
Assuming that your ESSID is not hidden and DHCP is enabled, could you try this please:
> auto [COLOR="Red"]eth1[/COLOR]
iface [COLOR="Red"]eth1[/COLOR] inet dhcp
wpa-driver [COLOR="Blue"]wext[/COLOR]
wpa-conf managed
wpa-ssid [COLOR="Purple"]Brown-Secure[/COLOR]
wpa-ap-scan 1
wpa-eap TTLS
wpa-key-mgmt IEEE8021X
wpa-identity [COLOR="Purple"]your_identity[/COLOR]
wpa-password [COLOR="Purple"]your_password[/COLOR]
wpa-ca-cert [COLOR="Purple"]/etc/cert/ca.pem[/COLOR]
wpa-phase2 [COLOR="DarkGreen"]auth=PAP[/COLOR]
You need to get hold of the server certificate for authentication of the server ("/etc/cert/ca.pem"). You either point to it using a URL or you get a copy of it and store it on your PC's harddrive. I believe you could skip this step in the first place and comment the line (#), but that's not safe in the long run.

By the way... what wireless chipset do you have again? The wpa-driver ("wext") may be different in your case.

---

### Post by acconrad on 2007-03-19
I have a Broadcom 5306 Dell wireless card...so I'm quite sure i'm using wext

---

### Post by acconrad on 2007-03-25
> **wieman01 said:**
> Assuming that your ESSID is not hidden and DHCP is enabled, could you try this please:

You need to get hold of the server certificate for authentication of the server ("/etc/cert/ca.pem"). You either point to it using a URL or you get a copy of it and store it on your PC's harddrive. I believe you could skip this step in the first place and comment the line (#), but that's not safe in the long run.

By the way... what wireless chipset do you have again? The wpa-driver ("wext") may be different in your case.

this did not work...could not connect to the secure network...also tried w/ the certificate...any ideas?

---

### Post by wieman01 on 2007-03-26
> **acconrad said:**
> this did not work...could not connect to the secure network...also tried w/ the certificate...any ideas?
You would have to post the output when upping your network:
> sudo ifup -v *[COLOR="Red"]your_interface[/COLOR]*
Without error message it is hard to tell what has gone wrong.

---

### Post by usererror on 2007-05-07
For what it's worth, I'm posting this here.

in Fiesty I am able to connect to our A Radio secure network running dynamic WEP, LEAP/EAP FAST.

I'm connecting with the Network-Manager, and using LEAP since it doesn't have eap-fast supported.  

A Radio wasn't supported before, or I could never get it to work, or our new LWAPP system is making the difference.

---

