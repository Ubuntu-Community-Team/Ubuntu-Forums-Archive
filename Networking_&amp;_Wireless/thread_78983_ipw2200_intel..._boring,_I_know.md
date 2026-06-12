---
title: "ipw2200 intel... boring, I know"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by pau on 2005-10-19
Hi,

I only managed once to bring the intel card to work when I installed the 2.6.13 kernel on hoary.... still, the communication was breaking every 20 minutes or so. Nevertheless I could not resist the temptation of installing breezy and so I did. The ipw2200 thing is there, right, and is updated... But I cannot connect to my network. I installed this gui utility, wifi-radar and it can see about four networks to which I could connect, including mine, but when I try to do so, both from command line with ifdown eth0 + ifup eth1 and form these gui thingies like the ubuntu one, it just takes ages to finish the connection and when it says it's finished and I am connected, I plug out the LAN and try to ping something, like ping [www.yahoo.com](www.yahoo.com) and nothing happens. There's not connection.
I have only a "mac address filter" on the router and am employing DHCP to make things easy... and no wap/wep/wip/wop :rolleyes:  But it doesn't work.

Any help will be appreciated

Here you are some output:

```
andromina| iwconfig                                                                                                      
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:"lameua"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
andromina| ifconfig                                                                                                      

eth0      Link encap:Ethernet  HWaddr 00:03:0D:1B:80:17
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe1b:8017/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:122899252 (117.2 MiB)  TX bytes:18760052 (17.8 MiB)
          Interrupt:9 Base address:0xc800

eth1      Link encap:Ethernet  HWaddr 00:0E:35:6A:43:3C
          inet6 addr: fe80::20e:35ff:fe6a:433c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:ffdfd000-ffdfdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9001860 (8.5 MiB)  TX bytes:9001860 (8.5 MiB)
```

```
andromina| iwlist  scanning                                                                                              

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:03:C9:7D:91:85
                    ESSID:"lameua"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=42/100  Signal level=-75 dBm
                    Extra: Last beacon: 219ms ago
          Cell 02 - Address: 00:09:5B:CC:59:B4
                    ESSID:"Funkverkehr"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=46/100  Signal level=-73 dBm
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra: Last beacon: 106ms ago
          Cell 03 - Address: 00:01:E3:41:E7:59
                    ESSID:"ConnectionPoint"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=44/100  Signal level=-74 dBm
                    Extra: Last beacon: 66ms ago
          Cell 04 - Address: 00:90:96:F7:EE:05
                    ESSID:"ALICE-WLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=16/100  Signal level=-88 dBm
                    Extra: Last beacon: 1172ms ago
```
```

andromina| sudo cat /proc/net/wireless                                                                                   

Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 17
  eth1: 0000    0.    0.    0.       0      0      0      0      0        0
```

HEEEEEEEEEEEELP!

---

### Post by Stealth on 2005-10-19
try "dhclient eth1" ?

---

### Post by pau on 2005-10-19
No working leases?? :confused: 

```
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:6a:43:3c
Sending on   LPF/eth1/00:0e:35:6a:43:3c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by pau on 2005-10-23
Bump...

Nobody can help me?

I was told I could also set my wlan card up with madwifi, and I went through the full process of installation and it IS set up... but the result is the same

Either with

[LIST=1]
[*]command lines
[*]or with nice gui applets
[*]with ipw2200 (version 1.0.0 to 1.0.6 checked out)
[*]with madwifi
[/LIST]

the result is THE SAME always for me:

I can see all networks flying in the air but I cannot log in to any of them, including mine!

I disabled the encription key and still cannot do it...

A lot of lads have told me they have the same wlan card and are surfing from the lavatory! I want too!!!

I'M FED UP!

HEEEEEEEEEELP!

---

### Post by Psquared on 2005-10-23
I was about to give up too .... until I tried this:


sudo gedit /etc/modprobe.d/ipw2200

(you probably will have an empty file)

regardless, add this line:

options ipw2200 hwcrypto=0

save

then run: modprobe -r ipw2200

and then: modprobe ipw2200 hwcrypto=0

this worked like a champ for me.

the one additional thing I did was I uninstalled a lot of software related to powersaving and other unneeded stuff first. my thought was i might have a software conflict too.

Anyway, my Intel Pro Wireless BG is now working like a charm. No problems at all for the last 48 hours. (and I've left it on for hours and rebooted several times.)

---

### Post by pau on 2005-10-23
P^2

thanks for the answer... But still I don't get any connection. I see all four networks (see above, 1st post) but cannot connect to them...

Can you connect through the gnome thing and/or radar-wifi or via command line? 

Another thing is that I have installed both, the ipw2200 thing and the madwifi one... do you think there is some overlap that's creating now this difficulty? 

It sound promising, what you say... I hope.. I bought this box in january and since then I'm struggling with the wlan...

---

### Post by pau on 2005-10-25
bump...

---

### Post by Psquared on 2005-10-25
[QUOTE=pau]P^2

thanks for the answer... But still I don't get any connection. I see all four networks (see above, 1st post) but cannot connect to them...

Can you connect through the gnome thing and/or radar-wifi or via command line? 

Another thing is that I have installed both, the ipw2200 thing and the madwifi one... do you think there is some overlap that's creating now this difficulty? 

It sound promising, what you say... I hope.. I bought this box in january and since then I'm struggling with the wlan...[/QUOTE]

I connect using the Networking Tools.

What do you see in System>Administration>Networking? Is the wireless card there? Are you able to activate it?

I had wifi-radar installed but as part of my problem solving I uninstalled it.

---

### Post by pau on 2005-10-26
```

What do you see in System>Administration>Networking? Is the wireless card there? Are you able to activate it?
```

Yes, I can see it and usually I stop the eth0 (LAN) one and also eth1 (WLAN) and then try to activate again eth1.... It takes ages until I get an answer, which is "activated" always... But as usual, I cannot employ any of the networks. To be sure I plug out the LAN cable and try to ping something... But nothing happens during some minutes until I get "not reachable", or something like that... and nothing else...

The command line doesn't help, either... I get the same thing

```
sudo ifconfig eth1 down
sudo ifconfig eth0 down
sudo iwconfig eth1 essid "XXXXXXXX"
sudo iwconfig eth1 open
sudo ifconfig eth1 up
sudo dhclient eth1

```

Everything is smooth and fine and then I try

```
ping www.yahoo.com
```

And... no connection...

---

### Post by emperor on 2005-10-26
Did you install the firmware for the ipw2200? It is not included with Ubuntu 5.10! 

The ipw2200 was working on my machine when activated via the system network with a fixed IP,  WITHOUT the firmware installed!

Download and installing the firmware (for ipw2200 v1.06) makes a noticable improvement!  Now Wifi-Radar works normally, no more lock-ups!

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

The firmware directory is "/usr/lib/hotplug/firmware" on Ubuntu.

---

### Post by hackyou on 2005-10-29
Emperor we have to extract the firmware archive in /usr/lib/hotplug/firmware and stop or something else?

---

### Post by tidemann on 2005-10-29
This is a HUGE problem for me as well... I have searched this board and read almost every possible solution, but nothing makes the ipw2200 card stable... I love Ubuntu, but I find myself searching for another distribution because of this..

---

### Post by emperor on 2005-10-29
[quote=hackyou]Emperor we have to extract the firmware archive in /usr/lib/hotplug/firmware and stop or something else?[/quote]

Just extract to: /usr/lib/hotplug/firmware and the then l the firmware will be automaticly loaded via hotplug during the boot process.

---

### Post by tekmerc on 2005-10-29
This might sound stupid, but..

Does your laptop have a wireless disable button (either by itself or a Fn+KEY combination)?. My laptop has an ipw2200 too and it took me a while to figure out that if that key is off, even though you can see access points, you cannot connect to any of them.

---

### Post by javaguru on 2005-11-09
i have the same problems. tried the ipw2200 hwcrypto=0 option, with no success. i can connect to the ap wihout wpa tho. this is why i still use windoze. May people complain but it works out of the box :/
i'M$orry ..

PS: i notice the led indicating a wireless connection is off even when i'm polling the ap

---

### Post by javaguru on 2005-11-10
OK, problem solved, i'll try to describe the sollution for 
Debian unstable kernel 2.6.13 (custom) WPA2 Personal with TKIP and AES:

1: edit /etc/modules.conf and add options ipw2200 hwcrypto=0
2: make sure your wpa_supplicant.conf looks something like this:
```

jlap:~# cat /etc/wpa_supplicant.conf
network={
        ssid="h4xx0r"
        #scan_ssid=1
        #bssid=00:12:17:d4:a3:94
        proto=WPA RSN
        #auth_alg=OPEN
        #mode=0
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk=5e128e4f1903815e7ad784b5e0d3b4ad7ed28085d4622f424dea5b5
        psk="imsofuckingfedupwiththis"
        priority=0
}
```
3: prepare a startup script for wpa_supplicant that looks like this (or better)
```
#! /bin/sh
# wifi / WPA init script
# -B for background

echo " [WLAN]: Enabling WPA supplicant ..."
        if [ -x /usr/sbin/wpa_supplicant ];
                then
                        killall wpa_supplicant;
                        modprobe -r ipw2200 ;
                        modprobe ipw2200 ;
                        /usr/sbin/wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D wext  -w -W;
                        echo " done!"
        fi

exit 0
# add support for restart
# the first 3 lines are a workaround for some strange stuff: AP is found,
# handshake done, and connection is up, and then the connection dies and AP is
# blacklisted. This means that the driver has to be unloaded and then reloaded
# add -dd and remove -B to debug

```
4: your /etc/network/interfaces looks something like this```

jlap:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
# The WLAN network interface
auto eth0
iface eth0 inet dhcp

# The other interface

iface eth1 inet dhcp

#wireless-mode          managed
#wireless-channel       0
#wireless-encryption    on
#wireless-pairwise      CCMP TKIP
#wireless-key_mgmt       WPA-PSK
wireless-nick           JLap
#wireless-set_power     3
#wireless-essid Haxxor
#wireless-key s:imfuckingfedup

```

iwconfig output : ```

jlap:~# iwconfig eth0
eth0      IEEE 802.11g  ESSID:"Haxxor"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:D4:A3:94
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:849E-9AEA-F9AAE-188-57D-BB12-F760   Security mode:open
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
iwlist output:
```
jlap:~# iwlist eth0 scanning
eth0      Scan completed :
          Cell 01 - Address: 00:12:17:D4:A3:94
                    ESSID:"Haxxor"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=89/100  Signal level=-40 dBm
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020000
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    Extra: Last beacon: 206ms ago

```
I'm not sure if this will help in your case, but i'll do my best to help out. maybe i'll update this post later today when i'll be rested .. good luck

---

### Post by iNerdSure on 2005-11-10
[QUOTE=Psquared]I connect using the Networking Tools.

What do you see in System>Administration>Networking? Is the wireless card there? Are you able to activate it?

I had wifi-radar installed but as part of my problem solving I uninstalled it.[/QUOTE].

---

### Post by iNerdSure on 2005-11-10
[QUOTE=Psquared]I was about to give up too .... until I tried this:


sudo gedit /etc/modprobe.d/ipw2200

(you probably will have an empty file)

regardless, add this line:

options ipw2200 hwcrypto=0

save

then run: modprobe -r ipw2200

and then: modprobe ipw2200 hwcrypto=0

this worked like a champ for me.

the one additional thing I did was I uninstalled a lot of software related to powersaving and other unneeded stuff first. my thought was i might have a software conflict too.

Anyway, my Intel Pro Wireless BG is now working like a charm. No problems at all for the last 48 hours. (and I've left it on for hours and rebooted several times.)[/QUOTE]

Hi, had similar problem. So tried your solution, and encountered:
> ins@inerdsure:~$ modprobe -r ipw2200
FATAL: Error removing ipw2200 (/lib/modules/2.6.12-9-386/kernel/drivers/net/wire less/ipw2200/ipw2200.ko): Operation not permitted
ptc@sgc9711:~$ cat /etc/wpa_supplicant.conf
cat: /etc/wpa_supplicant.conf: No such file or directory
ins@inerdsure:~$
Am I missing some other steps?
Please help. Thanks.

---

### Post by javaguru on 2005-11-11
iNerdSure READ my post which is the one above yours. It should get you started

---

### Post by iNerdSure on 2005-11-11
[QUOTE=javaguru]iNerdSure READ my post which is the one above yours. It should get you started[/QUOTE]
Thank you, Javaguru. I'll try. Being a newbie Linux convert, the steps look rather  intimidating. Will let you what kind of results I get. :confused:

---

### Post by iNerdSure on 2005-11-13
> **javaguru]OK, problem solved, i'll try to describe the sollution for 
Debian unstable kernel 2.6.13 (custom) WPA2 Personal with TKIP and AES:

1: edit /etc/modules.conf and add options ipw2200 hwcrypto=0
2: make sure your wpa_supplicant.conf looks something like this:
```

jlap:~# cat /etc/wpa_supplicant.conf
network={
        ssid="h4xx0r"
        #scan_ssid=1
        #bssid=00:12:17:d4:a3:94
        proto=WPA RSN
        #auth_alg=OPEN
        #mode=0
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk=5e128e4f1903815e7ad784b5e0d3b4ad7ed28085d4622f424dea5b5
        psk="imsofuckingfedupwiththis"
        priority=0
}
```
3: prepare a startup script for wpa_supplicant that looks like this (or better)
```
#! /bin/sh
# wifi / WPA init script
# -B for background

echo " [WLAN]: Enabling WPA supplicant ..."
        if [ -x /usr/sbin/wpa_supplicant ] said:**
> 
Hi Javaguru,
Got only as far as:
> 
edit /etc/modules.conf and add options ipw2200 hwcrypto=0
2: make sure your wpa_supplicant.conf looks something like this:


[QUOTE]
11:~$ cat /etc/wpa_supplicant.conf
cat: /etc/wpa_supplicant.conf: No such file or directory
11:~$

Am I missing some steps? Thanks.

---

### Post by javaguru on 2005-11-22
yupp .. you're missing the config file for wpa_supplicant, it should look something like this:
```

#for WPA2 (better security)
network={
        ssid="Haxxor"
        #scan_ssid=1
        #bssid=00:12:17:d4:a3:94
        proto=WPA RSN
        #auth_alg=OPEN
        #mode=0
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk=5e128e4f19038f315e7ad784b5e0d3b4ad7ed28085d123676d4622f424dea5b5
        psk="bing00++"
        priority=0
}

```

the only problem is that my last solution didn't work after upgrading to kernel 2.6.14, i still have some IOCTL errors .. Gimme a day or two

---

