---
title: "WLAN: unencrypted &amp; WEP work, WPA1+2 don't"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by d.avid on 2008-07-28
Hello.

I installed ndiswrapper with the WinXP BCM4312 drivers yesterday (following this guide: [http://ohioloco.ubuntuforums.org/showthread.php?t=760568](http://ohioloco.ubuntuforums.org/showthread.php?t=760568)) because of extremely slow internet connections (if any) with my notebook. Funnily enough, iwconfig reports roughly the same link quality (~70%) as Windows Vista, where the wlan is much much faster. The router web interface produced a quality of only ~20% in the first case, though.

The driver works, I can connect to my wlan using WEP or no encryption. The quality issues mentioned above don't seem to occur.
-->
When I use WPA1/2 the wlan is found aswell and iwconfig & Wicd even report that i'm connected and the link quality. BUT internet doesn't work, I can't even ping my router!

In the router log it says that the authorization fails due to an invalid key (which is correct of course).

I use the same WPA settings as I did with the old driver (where the connection at least worked). I use Wicd by the way. I tried the HOWTOs concerning wlan security and connecting manually without success.
I don't know which data is relevant here, please tell me if you want to see any outputs or files.

iwconfig
```
wlan0     IEEE 802.11g  ESSID:"Sub-Etha-Net"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1C:4A:A3:1F:AD   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
```


ifconfig
```
wlan0     Link encap:Ethernet  Hardware Adresse 00:1e:4c:14:b9:2e  
          inet Adresse:192.168.178.22  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21e:4cff:fe14:b92e/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:8291 (8.0 KB)  TX bytes:14329 (13.9 KB)
          Interrupt:16 Speicher:c0200000-c0204000
```

Thanks in advance. 
david

---

### Post by caljohnsmith on 2008-07-28
> **d.avid said:**
> I use the same WPA settings as I did with the old driver (where the connection at least worked). I use Wicd by the way.
What old driver are you referring to? BTW, make sure you have the wpasupplicant package installed, but it sounds like you do.

---

### Post by d.avid on 2008-07-28
> **caljohnsmith said:**
> What old driver are you referring to? BTW, make sure you have the wpasupplicant package installed, but it sounds like you do.

Thanks for your reply.
I *think* it "worked" more or less out of the box after I installed Hardy: wext. 
wpasupplicant is installed.

Bye

---

### Post by d.avid on 2008-07-29
I tried kevdog's tutorial on command line connection, same issues.
Doing so I've gathered some more details like the wpa_supplicant debugging messages, the .conf file and my exact proceeding (posted here [http://ubuntuforums.org/showthread.php?p=5481462#post5481462](http://ubuntuforums.org/showthread.php?p=5481462#post5481462)) although I don't know how to interprete the results.

--> WPA connection (failed attempt)
```

sudo su
ifconfig wlan0 down
dhclient -r wlan0
route add default gw 192.168.178.1
ifconfig wlan0 192.168.178.22 netmask 255.255.255.0
iwconfig wlan0 essid "Sub-Etha-Net"
iwconfig wlan0 mode Managed
wpa_supplicant -Bw -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf 

```

**wpa_supplicant.conf**
```

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

network={
	ssid="Sub-Etha-Net"
	psk="mykey"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
}

```

Bye

---

### Post by d.avid on 2008-07-31
Oh my god, it worked!
Once.

I changed the WPA key and got a connection to the internet:
```

root@Oiskipoiski:~# **rm -rf /var/run/wpa_supplicant/wlan0**
root@Oiskipoiski:~# **ifconfig wlan0 down**
root@Oiskipoiski:~# **dhclient -r wlan0**
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1e:4c:14:b9:2e
Sending on   LPF/wlan0/00:1e:4c:14:b9:2e
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.178.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
root@Oiskipoiski:~# **ifconfig wlan0 192.168.178.22 netmask 255.255.255.0**
root@Oiskipoiski:~# **route add default gw 192.168.178.1**
root@Oiskipoiski:~# **iwconfig wlan0 essid "Sub-Etha-Net"**
root@Oiskipoiski:~# **iwconfig wlan0 mode Managed**
root@Oiskipoiski:~# **wpa_supplicant -w -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf**
Trying to associate with 00:1c:4a:a3:1f:ad (SSID='Sub-Etha-Net' freq=2427 MHz)
Associated with 00:1c:4a:a3:1f:ad
[b]WPA: Key negotiation completed with 00:1c:4a:a3:1f:ad [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1c:4a:a3:1f:ad completed (auth) [/b][id=0 id_str=]
```


I terminated the connection with CTRL+C and without changing anything at all I entered the very same lines:
```

root@Oiskipoiski:~# **ifconfig wlan0 down**
root@Oiskipoiski:~# **dhclient -r wlan0**
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1e:4c:14:b9:2e
Sending on   LPF/wlan0/00:1e:4c:14:b9:2e
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.178.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
root@Oiskipoiski:~# **ifconfig wlan0 192.168.178.22 netmask 255.255.255.0**
root@Oiskipoiski:~# **route add default gw 192.168.178.1**
root@Oiskipoiski:~# **iwconfig wlan0 essid "Sub-Etha-Net"**
root@Oiskipoiski:~# **wpa_supplicant -w -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf**
Trying to associate with 00:1c:4a:a3:1f:ad (SSID='Sub-Etha-Net' freq=2427 MHz)
Associated with 00:1c:4a:a3:1f:ad
Associated with 00:1c:4a:a3:1f:ad
Associated with 00:1c:4a:a3:1f:ad
Associated with 00:1c:4a:a3:1f:ad
...
```

The router reports "authorization failed" everytime. Something with the keys...!? 
Though "iwlist scan" always finds the wlan, wpa_supplicant often doesn't. I get scan timeouts and messages like 
"ioctl[SIOCGIWSCAN]: Resource temporarily unavailable" then.


Okay, I was going to post the wpa_supplicant debugging output and the .conf file the wlan worked with, but I'm experiencing new problems now (and I don't know what I did to provoke them).

My wlan0 device is not found anymore. ifconfig just doesn't list it. When I try "sudo ifconfig wlan0 up" I get: (I assume; it's German)
**wlan0: ERROR while getting interface flags: No such device**

'sudo ifup wlan0' and '/etc/init.d/networking restart' produce:
```

wlan0: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
Failed to disable WPA in the driver.
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.

```

Yeah... suggestions? :(

---

### Post by caljohnsmith on 2008-07-31
That's great you got it to work at least once, but the results you are experiencing while troubleshooting seem rather erratic and inconsistent; I would file a bug report at this point if I were you: bugs.launchpad.net. Sorry I can't be of more help, but it seems like you are experiencing some genuine bugs and it would be good to let the bug team know about them.

---

