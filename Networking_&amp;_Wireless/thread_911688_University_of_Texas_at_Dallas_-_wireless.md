---
title: "University of Texas at Dallas - wireless"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by ArlexBee on 2008-09-05
Hello,

I've been trying to get my wireless connection to work at the University of Texas at Dallas.  School can't help me because they don't offer Linux support, and I've been working on this for days now.  I've tried both xsupplicant and wpa_supplicant.  [HERE ]("http://www.utdallas.edu/ir/cats/network/wlan/8021x/linux.html")is the official UTD instruction on how to get it to work with xsupplicant.  

I'm running Kubuntu 8.04 and I have a Lenovo Thinkpad T61 with an Intel 4965.  I post my wpa_supplicant attempt here.


My **/etc/wpa_supplicant/wpa_supplicant.conf **file looks like this:

```
network={
    ssid="UTDALLAS"
    scan_ssid=1
    key_mgmt=IEEE8021X
    eap=PEAP
    ca_cert="/etc/wpa_supplicant/verisign.pem"
    phase2="auth=MSCHAPV2"
    identity="axa081100"
    password="my school password"
}
```


My **/etc/network/interfaces** looks like this:

```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
```

The '**iwl4965**' kernel module loads up and I'm sure the drivers work since I'm able to connect to my home wireless system.

Running **sudo /etc/init.d/networking restart **I get:
```
* Reconfiguring network interfaces...                                                                                                                    RTNETLINK answers: No such process                                                                                                                        
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072                                                                                
Internet Systems Consortium DHCP Client V3.0.6                                                                                                            
Copyright 2004-2007 Internet Systems Consortium.                                                                                                          
All rights reserved.                                                                                                                                      
For info, please visit http://www.isc.org/sw/dhcp/                                                                                                        

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:26:b9:4d   
Sending on   LPF/wlan0/00:13:e8:26:b9:4d
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:26:b9:4d
Sending on   LPF/wlan0/00:13:e8:26:b9:4d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
Trying recorded lease 192.168.1.4
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

I've tried commenting out **ca_cert="/etc/wpa_supplicant/verisign.pem"** from the **wpa_supplicant.conf **file because I'm not sure if I need it, but it makes no difference.

Running **sudo wpa_supplicant -w -iwlan0 -Dwext -c/etc/wpa_supplicant/wpa_supplicant.conf** I get:
```
Trying to associate with 00:0c:e6:9e:12:9c (SSID='UTDALLAS' freq=2462 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:0c:e6:9e:12:9c (SSID='UTDALLAS' freq=2462 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:0c:e6:9e:12:9c (SSID='UTDALLAS' freq=2462 MHz)
Authentication with 00:00:00:00:00:00 timed out.
...
```
I don't know what else try.  Can anyone help?

Thanks

---

### Post by ArlexBee on 2008-09-06
wow, these pages are moving quickly.

Anyone have any idea what I could try next?

ArlexBee

---

### Post by ChiaGod on 2008-09-08
Hello!

I am also feeling your pain.  I do have good news... At one time I did have my laptop working via wireless at UTD.  Since I have switched from Kubuntu to regular Ubuntu and I have not got it working since.

I do know that the instructions at the UTD site have not been updated in a while, and since then there have been updates to Ubuntu's networking (now gives additional options for Wireless Security).

Thing is, when you click on the networking icon and select "Other Networks" there are 4 WPA options.  The correct one should be either WPA Enterprise or WPA2 Enterprise.

The correct settings (to my knowledge) should be:
Network name:UTDALLAS
Wireless Security: (WPA or WPA2 Enterprise)
EAP Method: PEAP
Key Type:  ???
Phase2 Type: MSCHAPV2
Identity: UTD Login
Password: Your UTD Password
Anonymous Identity:
Client Certificate File: ???
CA Certificate File: (Select the verisign.pem you downloaded)
Private Key File:
Private Key Password:

I'm still testing to see if I can get it working via this method, but I'll post what I find out.

Oh and welcome to UTD!

Edited to add:  Ensure your wireless drivers are working with a simpler wireless connection.  If you or somebody you know has a router, make sure you can connect to it.  Also it may be worth testing connectivity using a different driver (OSS or ndiswrapper)

---

### Post by ChiaGod on 2008-09-08
Ok I did some digging and found the old files that worked with Kubuntu 7.04 or 7.10.

The last file is my wpa_supplicant.conf (just remove the extra stuff and fill in the blanks to use it).  Also replace eth1 with the correct name of your wireless adaptor.

The other three files are shell scripts I wrote to connect to the UTD network, reconnect (in case it drops), and finally turn off wpa_supplicant so I can use a home network.

Note you can add a ping command at the end of these scripts to get confirmation that the connection was successful.

I haven't re-tried getting this to work in Ubuntu 8.10, but when I have a chance I'll go through the whole procedure and post an update.

---

### Post by ChiaGod on 2008-10-16
I wanted to add, even though I have not gotten the UTDALLAS WPA network to work with Ubuntu (After moving from 7.10 to 8.04), I am happy to note that a new network is up called CometNet2.  

Ubuntu 8.04 can connect to CometNet2 with no modifications:  
1.  Select CometNet2 from the available networks
2.  Select WPA or WPA2 (forget which one worked) for the network, 
3.  User ID and password fields will appear.
4.  Enter your UTD ID and password
5.  Internet!

I know this newer network is available at the Engineering building and at Johnson, I'm not sure of the apartments and other buildings, but if you see it, know you can connect to it.

There is no certificate requirement for this newer network.

---

