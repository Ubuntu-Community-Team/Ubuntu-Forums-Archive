---
title: "Wireless card does not obtain IP address from router in Intrepid Ibex"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by Wedge009 on 2008-11-24
I think I have a rather unusual problem, so please bear with me. Of course, if it turns out not to be that unusual, then good! Hopefully, someone will already have a solution, but I won't be surprised if there isn't any.

Not long ago, I could connect to a Linksys WRT54GL Wireless-G router using a Linksys WPC100 notebook adapter with WPA-PSK encryption, and this was on Kubuntu 8.10 (I am quite sure my problem is not Kubuntu-specific). Having moved to a different location, I am now trying to connect to a Netgear WNR854T Wireless-N router with WPA2-PSK encryption.

While wpa_supplicant seems to connect with the router fine, I cannot get any Internet connection. After checking the "Attached Devices" section of the router's interface, the laptop in question is listed with an IP address of 0.0.0.0, whereas all other hosts are listed as 192.168.1.xx. For comparison, I have a Kubuntu 8.10 desktop and a 802.11n-capable laptop (albeit Windows XP Pro based) connecting to the same router using wired and wireless connections respectively.

I have been using Kubuntu for a few years now, although I am still a little unfamiliar with some of the more esoteric and obscure utilities, so please be patient with me. I am hoping - however vainly - that someone has had a similar experience and might be able to help me with this problem. I do hope it's not a Linksys+Linksys vs Linksys+Netgear issue...

---

### Post by gTinker on 2008-11-24
[QUOTE=Wedge009]
Not long ago, I could connect to a Linksys WRT54GL Wireless-G router using a Linksys WPC100 notebook adapter with WPA-PSK encryption, and this was on Kubuntu 8.10 (I am quite sure my problem is not Kubuntu-specific). Having moved to a different location, I am now trying to connect to a Netgear WNR854T Wireless-N router with WPA2-PSK encryption.[/QUOTE]

Sorry I can't give you a definitive answer to your problem but are you confident that the WPC100 is capable of WPA2?

[QUOTE=Wedge009]
While wpa_supplicant seems to connect with the router fine, I cannot get any Internet connection. After checking the "Attached Devices" section of the router's interface, the laptop in question is listed with an IP address of 0.0.0.0, whereas all other hosts are listed as 192.168.1.xx. For comparison, I have a Kubuntu 8.10 desktop and a 802.11n-capable laptop (albeit Windows XP Pro based) connecting to the same router using wired and wireless connections respectively.[/QUOTE]

Is the WPC100 capable of N connections? If it isn't you haven't optioned the router to only use N, have you? That might be an easy mistake to make since your working laptop does have N capabilities.

[QUOTE=Wedge009]
I have been using Kubuntu for a few years now, although I am still a little unfamiliar with some of the more esoteric and obscure utilities, so please be patient with me. I am hoping - however vainly - that someone has had a similar experience and might be able to help me with this problem. I do hope it's not a Linksys+Linksys vs Linksys+Netgear issue...[/QUOTE]

Well, I can't think of a reason you would need any esoteric or obscure utility for any of this.

There is some possibility that it is related to the different brands, N is such a new 'standard' that some earlier equipment wasn't as standard as we might hope. So, there is a possibility, don't jump to this conclusion though.

Is something handling your connection for you or are you attempting it manually? Is the router handing out those IP addressed through DHCP? Is your system set up to request an IP address through DHCP? What happens when you stop then restart the wireless interface from a terminal, does it try to obtain an address? Does it drop any error message?

---

### Post by kevdog on 2008-11-24
A couple of issues you might need to research since I just went through this (a thread under my name will prove this)

#1 You need to make sure the driver you are using for your card supports WPA2

#2 I would change your router settings so it support WPA2 mixed or WPA2/1.  Meaning it prefers 2, but in case a client can not connect it falls back to 1

#3. What driver are your using?

#4. I things are not working, try to troubleshoot using manual connection.  This will tell you the stage things are failing at.  This requires that you simply install the package wpasupplicant (probably already installed), you make a wpa_supplicant.conf file (post back if you need a skeleton).  You need to first pass authentication credentials.  You didn't state if you were using dhcp or a static ip address, but assuming dhcp, you then ask for a dhcp lease -- and thats it!

---

### Post by Wedge009 on 2008-11-24
Thanks for the fast responses.

> **gTinker said:**
> Sorry I can't give you a definitive answer to your problem but are you confident that the WPC100 is capable of WPA2?[I should think so](http://www-au.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=AU%2FLayout&cid=1175240955587&pagename=Linksys%2FCommon%2FVisitorWrapper).

> **gTinker said:**
> Is the WPC100 capable of N connections? If it isn't you haven't optioned the router to only use N, have you?Linksys XXX100 series is interesting. It appears to offer some 802.11n features without actually officially claiming to be Draft 802.11n compliant. The product description seems to imply that it can work with 802.11n networks, at any rate.

I should mention that in trying to get things to work, I set the router to 802.11b/g speeds and options, but they didn't seem to make a difference.

> **gTinker said:**
> Is something handling your connection for you or are you attempting it manually? Is the router handing out those IP addressed through DHCP? Is your system set up to request an IP address through DHCP? What happens when you stop then restart the wireless interface from a terminal, does it try to obtain an address? Does it drop any error message?Since I'm running it in Kubuntu with KDE4, I resorted to manually configuring the wpa_supplicant.conf file and starting wpa_supplicant through Konsole.

The router is set up as a DHCP server, all other hosts (WinXP and Kubuntu) have no problems obtaining IP addresses from it.

> **kevdog said:**
> #1 You need to make sure the driver you are using for your card supports WPA2

#2 I would change your router settings so it support WPA2 mixed or WPA2/1.  Meaning it prefers 2, but in case a client can not connect it falls back to 1

#3. What driver are your using?

#4. I things are not working, try to troubleshoot using manual connection.  This will tell you the stage things are failing at.  This requires that you simply install the package wpasupplicant (probably already installed), you make a wpa_supplicant.conf file (post back if you need a skeleton).  You need to first pass authentication credentials.  You didn't state if you were using dhcp or a static ip address, but assuming dhcp, you then ask for a dhcp lease -- and thats it![LIST=1]
[*]As mentioned above, the Linksys site claims the WPC100 can handle WPA2 encryption.
[*]I should have also mentioned that I tried WPA and even no encryption, with no apparent change.
[*]The Windows XP drivers with ndiswrapper. Vista drivers did not work at all, even back with the Linksys WRT54GL router. So many things I forgot to mention!
[*]Already using wpa_supplicant. :/ Tried with a static IP address and DHCP.
[/LIST]

Thanks for the suggestions, though. It looks like this could be a hardware-related issue and not necessarily Ubuntu's or KDE's fault. As I mentioned before, it's not that I can't get the laptop to communicate with the router at all (as most wireless-problem threads seem to be related to). It's that I can't get an IP address from the router. :confuzzled:

For what it's worth, here is the wpa_supplicant.conf I am using. I went through several configurations before even being able to connect to the router in the first place.

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
	ssid="My Network Name"
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
	group=CCMP
	psk="My Very Secret Pass Key"
}
```Using CCMP because the router expects WPA2-PSK [AES].

---

### Post by kevdog on 2008-11-24
Ok

Here is what I would use:

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
	ssid="My Network Name"
        scan_ssid=1
	proto=RSN WPA
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP
	psk="My Very Secret Pass Key"
}

I would open up 3 terminals

On one terminal type:
tail -f /var/log/syslog

This is going to give run a continuous view of the syslog as messages are added to it.  Any error should present here.

On terminal #2
sudo wpa_supplicant -i <interface> -D wext -c /etc/wpa_supplicant.conf -d

On terminal #3 (After typing on #2 and waiting for some type of confirmation that address has been recognized)
sudo dhclient <interface>

Also if you could provide the following
sudo iwlist <interface> auth
sudo lshw -C network
sudo iwlist <interface> scan

Thanks

---

### Post by Wedge009 on 2008-11-25
> **kevdog said:**
> ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
	ssid="My Network Name"
        scan_ssid=1
	proto=RSN WPA
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP
	psk="My Very Secret Pass Key"
}I tried using those settings for scan_ssid, protocol, pairwise and group before, but for the sake of this testing, I put them back in.

> **kevdog said:**
> On one terminal type:
tail -f /var/log/syslog

This is going to give run a continuous view of the syslog as messages are added to it.  Any error should present here.```
Nov 26 02:55:23 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4                                
Nov 26 02:55:27 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10                               
Nov 26 02:55:37 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20                               
Nov 26 02:55:56 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8                               
Nov 26 02:55:57 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15                               
Nov 26 02:56:04 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15                              
Nov 26 02:56:12 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10                               
Nov 26 02:56:19 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21                              
Nov 26 02:56:22 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2                                
Nov 26 02:56:24 Celsius dhclient: No DHCPOFFERS received.                                                                   
Nov 26 02:56:27 Celsius dhclient: Trying recorded lease 192.168.0.21                                                        
Nov 26 02:56:27 Celsius avahi-daemon[4607]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.21.  
Nov 26 02:56:27 Celsius avahi-daemon[4607]: New relevant interface eth0.IPv4 for mDNS.                                      
Nov 26 02:56:27 Celsius avahi-daemon[4607]: Registering new address record for 192.168.0.21 on eth0.IPv4.                   
Nov 26 02:56:30 Celsius avahi-daemon[4607]: Withdrawing address record for 192.168.0.21 on eth0.                            
Nov 26 02:56:30 Celsius avahi-daemon[4607]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.21.  
Nov 26 02:56:30 Celsius avahi-daemon[4607]: Interface eth0.IPv4 no longer relevant for mDNS.                                
Nov 26 02:56:33 Celsius dhclient: No working leases in persistent database - sleeping.                                      
Nov 26 02:56:40 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17                              
Nov 26 02:56:57 Celsius dhclient: No DHCPOFFERS received.                                                                   
Nov 26 02:56:57 Celsius dhclient: Trying recorded lease 192.168.1.21                                                        
Nov 26 02:56:57 Celsius avahi-daemon[4607]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.21. 
Nov 26 02:56:57 Celsius avahi-daemon[4607]: New relevant interface wlan0.IPv4 for mDNS.                                     
Nov 26 02:56:57 Celsius avahi-daemon[4607]: Registering new address record for 192.168.1.21 on wlan0.IPv4.                  
Nov 26 02:57:00 Celsius avahi-daemon[4607]: Withdrawing address record for 192.168.1.21 on wlan0.                           
Nov 26 02:57:00 Celsius avahi-daemon[4607]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.21. 
Nov 26 02:57:00 Celsius avahi-daemon[4607]: Interface wlan0.IPv4 no longer relevant for mDNS.                               
Nov 26 02:57:03 Celsius dhclient: No working leases in persistent database - sleeping.                                      
Nov 26 03:00:27 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3                                
Nov 26 03:00:30 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4                                
Nov 26 03:00:34 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6                                
Nov 26 03:00:40 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12                               
Nov 26 03:00:52 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18                               
Nov 26 03:01:10 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9                                
Nov 26 03:01:19 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9                                
Nov 26 03:01:28 Celsius dhclient: No DHCPOFFERS received.                                                                   
Nov 26 03:01:31 Celsius dhclient: Trying recorded lease 192.168.0.21                                                        
Nov 26 03:01:31 Celsius avahi-daemon[4607]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.21.  
Nov 26 03:01:31 Celsius avahi-daemon[4607]: New relevant interface eth0.IPv4 for mDNS.                                      
Nov 26 03:01:31 Celsius avahi-daemon[4607]: Registering new address record for 192.168.0.21 on eth0.IPv4.                   
Nov 26 03:01:34 Celsius avahi-daemon[4607]: Withdrawing address record for 192.168.0.21 on eth0.                            
Nov 26 03:01:34 Celsius avahi-daemon[4607]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.21.  
Nov 26 03:01:34 Celsius avahi-daemon[4607]: Interface eth0.IPv4 no longer relevant for mDNS.                                
Nov 26 03:03:51 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3                               
Nov 26 03:03:54 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3                               
Nov 26 03:03:57 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8                               
Nov 26 03:04:05 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15                              
Nov 26 03:04:20 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17                              
Nov 26 03:04:37 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12                              
Nov 26 03:04:49 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3                               
Nov 26 03:04:52 Celsius dhclient: No DHCPOFFERS received.                                                                   
Nov 26 03:04:52 Celsius dhclient: Trying recorded lease 192.168.1.21                                                        
Nov 26 03:04:52 Celsius avahi-daemon[4607]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.21. 
Nov 26 03:04:52 Celsius avahi-daemon[4607]: New relevant interface wlan0.IPv4 for mDNS.                                     
Nov 26 03:04:52 Celsius avahi-daemon[4607]: Registering new address record for 192.168.1.21 on wlan0.IPv4.                  
Nov 26 03:04:55 Celsius avahi-daemon[4607]: Withdrawing address record for 192.168.1.21 on wlan0.                              
Nov 26 03:04:55 Celsius avahi-daemon[4607]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.21.    
Nov 26 03:04:55 Celsius avahi-daemon[4607]: Interface wlan0.IPv4 no longer relevant for mDNS.                                  
Nov 26 03:04:58 Celsius dhclient: No working leases in persistent database - sleeping.                                         
Nov 26 03:06:10 Celsius dhclient: Internet Systems Consortium DHCP Client V3.1.1                                               
Nov 26 03:06:10 Celsius dhclient: Copyright 2004-2008 Internet Systems Consortium.                                             
Nov 26 03:06:10 Celsius dhclient: All rights reserved.                                                                         
Nov 26 03:06:10 Celsius dhclient: For info, please visit http://www.isc.org/sw/dhcp/                                           
Nov 26 03:06:10 Celsius dhclient:                                                                                              
Nov 26 03:06:11 Celsius dhclient: Listening on LPF/wlan0/00:1d:7e:9d:e6:9d                                                     
Nov 26 03:06:11 Celsius dhclient: Sending on   LPF/wlan0/00:1d:7e:9d:e6:9d                                                     
Nov 26 03:06:11 Celsius dhclient: Sending on   Socket/fallback                                                                 
Nov 26 03:06:14 Celsius dhclient: DHCPREQUEST of 192.168.1.21 on wlan0 to 255.255.255.255 port 67                              
Nov 26 03:06:22 Celsius dhclient: DHCPREQUEST of 192.168.1.21 on wlan0 to 255.255.255.255 port 67                              
Nov 26 03:06:29 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3                                  
Nov 26 03:06:30 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3                                   
Nov 26 03:06:32 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7                                  
Nov 26 03:06:33 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4                                   
Nov 26 03:06:37 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6                                   
Nov 26 03:06:39 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12                                 
Nov 26 03:06:43 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8                                   
Nov 26 03:06:51 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10                                  
Nov 26 03:06:51 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9                                  
Nov 26 03:07:00 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10                                 
Nov 26 03:07:01 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 26 03:07:10 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Nov 26 03:07:12 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov 26 03:07:22 Celsius dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov 26 03:07:24 Celsius dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 26 03:07:30 Celsius dhclient: No DHCPOFFERS received.
Nov 26 03:07:30 Celsius dhclient: Trying recorded lease 192.168.1.21
Nov 26 03:07:30 Celsius avahi-daemon[4607]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.21.
Nov 26 03:07:30 Celsius avahi-daemon[4607]: New relevant interface wlan0.IPv4 for mDNS.
Nov 26 03:07:30 Celsius avahi-daemon[4607]: Registering new address record for 192.168.1.21 on wlan0.IPv4.
Nov 26 03:07:31 Celsius dhclient: No DHCPOFFERS received.
Nov 26 03:07:33 Celsius avahi-daemon[4607]: Withdrawing address record for 192.168.1.21 on wlan0.
Nov 26 03:07:33 Celsius avahi-daemon[4607]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.21.
Nov 26 03:07:33 Celsius avahi-daemon[4607]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 26 03:07:33 Celsius dhclient: Trying recorded lease 192.168.0.21
Nov 26 03:07:33 Celsius avahi-daemon[4607]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.21.
Nov 26 03:07:33 Celsius avahi-daemon[4607]: New relevant interface eth0.IPv4 for mDNS.
Nov 26 03:07:33 Celsius avahi-daemon[4607]: Registering new address record for 192.168.0.21 on eth0.IPv4.
Nov 26 03:07:33 Celsius dhclient: No working leases in persistent database - sleeping.
Nov 26 03:07:36 Celsius avahi-daemon[4607]: Withdrawing address record for 192.168.0.21 on eth0.
Nov 26 03:07:36 Celsius avahi-daemon[4607]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.21.
Nov 26 03:07:36 Celsius avahi-daemon[4607]: Interface eth0.IPv4 no longer relevant for mDNS.
```Yes, that is local time. I'm losing a lot of sleep trying to deal with this frustrating problem.

> **kevdog said:**
> On terminal #2
sudo wpa_supplicant -i <interface> -D wext -c /etc/wpa_supplicant.conf -d```
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:18:4d:24:ba:e4
IEEE 802.1X RX: version=1 type=3 length=151
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=56
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 98
  key_nonce - hexdump(len=32): d3 38 31 16 67 fc e5 6a 2b f0 c9 0e 3f 34 fd e2 83 a8 61 06 17 6c 15 5a db 60 f9 fe ef a4 2d d2
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): cf 21 a9 6f e7 e3 9c 33 a2 2c 5d 21 f7 3a a1 3e
RSN: encrypted key data - hexdump(len=56): 87 7f c3 6b 29 33 c7 42 42 84 40 d8 33 61 a4 f9 06 71 50 7b 8a 46 00 38 3c 5a d5 db f7 28 f2 c0 72 39 3a 11 fb 01 38 5b 69 c7 24 d5 6f 5a f6 99 aa b0 a4 73 85 9d 45 4b
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
State: COMPLETED -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 b7 84 2e 46 0c 78 d8 2e 9e dd 46 da bc fd 88 7e dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=16).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with 00:18:4d:24:ba:e4 [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
RX EAPOL from 00:18:4d:24:ba:e4
IEEE 802.1X RX: version=1 type=3 length=151
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=56
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 99
  key_nonce - hexdump(len=32): d3 38 31 16 67 fc e5 6a 2b f0 c9 0e 3f 34 fd e2 83 a8 61 06 17 6c 15 5a db 60 f9 fe ef a4 2d d2
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 15 4e b4 bd dc 5b 8d 13 58 ad c4 fe f2 c4 21 95
RSN: encrypted key data - hexdump(len=56): 87 7f c3 6b 29 33 c7 42 42 84 40 d8 33 61 a4 f9 06 71 50 7b 8a 46 00 38 3c 5a d5 db f7 28 f2 c0 72 39 3a 11 fb 01 38 5b 69 c7 24 d5 6f 5a f6 99 aa b0 a4 73 85 9d 45 4b
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
State: COMPLETED -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 b7 84 2e 46 0c 78 d8 2e 9e dd 46 da bc fd 88 7e dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=16).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with 00:18:4d:24:ba:e4 [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c07 len=122
AssocReq IE wireless event - hexdump(len=114): 00 05 53 70 69 72 61 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 1e 00 90 4c 33 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 2d 1a 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 dd 07 00 50 f2 02 00 01 00
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=102
AssocResp IE wireless event - hexdump(len=94): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 2d 1a 6c 18 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:18:4d:24:ba:e4
Association info event
req_ies - hexdump(len=114): 00 05 53 70 69 72 61 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 1e 00 90 4c 33 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 2d 1a 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 dd 07 00 50 f2 02 00 01 00
resp_ies - hexdump(len=94): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 2d 1a 6c 18 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
State: COMPLETED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:18:4d:24:ba:e4
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:18:4d:24:ba:e4
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=2
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9c
  key_nonce - hexdump(len=32): 48 23 2a 0d fc 67 7e f1 30 6b 52 15 24 2f 66 79 98 b3 fa 1d 0c f7 0e c1 40 fb 62 65 74 bf 36 49
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
RSN: msg 1/4 key data - hexdump(len=0):
WPA: Renewed SNonce - hexdump(len=32): b9 84 d8 98 d4 c2 85 c9 c7 16 73 a9 77 6a e1 4e d1 3f 29 39 97 a4 9a fd de 0a e2 63 91 15 ae b6
WPA: PTK derivation - A1=00:1d:7e:9d:e6:9d A2=00:18:4d:24:ba:e4
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:18:4d:24:ba:e4
IEEE 802.1X RX: version=1 type=3 length=151
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=56
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9d
  key_nonce - hexdump(len=32): 48 23 2a 0d fc 67 7e f1 30 6b 52 15 24 2f 66 79 98 b3 fa 1d 0c f7 0e c1 40 fb 62 65 74 bf 36 49
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): fb 97 46 65 9a 5e 6d e7 81 f1 0b 69 dc 71 50 31
RSN: encrypted key data - hexdump(len=56): a1 ba c7 35 3c d6 ea 98 29 b7 24 11 1f 68 70 3b 6a ad 41 72 5a d8 4f 4b 6c c4 70 6f 37 fd 7b 4f c4 6a d7 82 52 7a 22 e0 da b5 4a 88 3e 83 9b 11 bb 78 18 95 4b 05 c3 e2
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 b7 84 2e 46 0c 78 d8 2e 9e dd 46 da bc fd 88 7e dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=16).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with 00:18:4d:24:ba:e4 [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:18:4d:24:ba:e4 completed (reauth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:18:4d:24:ba:e4
IEEE 802.1X RX: version=1 type=3 length=151
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=56
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9e
  key_nonce - hexdump(len=32): 48 23 2a 0d fc 67 7e f1 30 6b 52 15 24 2f 66 79 98 b3 fa 1d 0c f7 0e c1 40 fb 62 65 74 bf 36 49
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): cd 8d 4d 11 8e 42 d8 80 f2 75 21 eb 48 8d b4 75
RSN: encrypted key data - hexdump(len=56): a1 ba c7 35 3c d6 ea 98 29 b7 24 11 1f 68 70 3b 6a ad 41 72 5a d8 4f 4b 6c c4 70 6f 37 fd 7b 4f c4 6a d7 82 52 7a 22 e0 da b5 4a 88 3e 83 9b 11 bb 78 18 95 4b 05 c3 e2
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
State: COMPLETED -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 b7 84 2e 46 0c 78 d8 2e 9e dd 46 da bc fd 88 7e dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=16).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with 00:18:4d:24:ba:e4 [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
RX EAPOL from 00:18:4d:24:ba:e4
IEEE 802.1X RX: version=1 type=3 length=151
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=56
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9f
  key_nonce - hexdump(len=32): 48 23 2a 0d fc 67 7e f1 30 6b 52 15 24 2f 66 79 98 b3 fa 1d 0c f7 0e c1 40 fb 62 65 74 bf 36 49
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 1a 27 30 13 cd 1b 73 88 58 78 98 58 20 22 4a e1
RSN: encrypted key data - hexdump(len=56): a1 ba c7 35 3c d6 ea 98 29 b7 24 11 1f 68 70 3b 6a ad 41 72 5a d8 4f 4b 6c c4 70 6f 37 fd 7b 4f c4 6a d7 82 52 7a 22 e0 da b5 4a 88 3e 83 9b 11 bb 78 18 95 4b 05 c3 e2
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
State: COMPLETED -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 b7 84 2e 46 0c 78 d8 2e 9e dd 46 da bc fd 88 7e dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=16).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with 00:18:4d:24:ba:e4 [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c07 len=122
AssocReq IE wireless event - hexdump(len=114): 00 05 53 70 69 72 61 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 1e 00 90 4c 33 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 2d 1a 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 dd 07 00 50 f2 02 00 01 00
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=102
AssocResp IE wireless event - hexdump(len=94): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 2d 1a 6c 18 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:18:4d:24:ba:e4
Association info event
req_ies - hexdump(len=114): 00 05 53 70 69 72 61 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 1e 00 90 4c 33 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 2d 1a 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 dd 07 00 50 f2 02 00 01 00
resp_ies - hexdump(len=94): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 2d 1a 6c 18 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
State: COMPLETED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:18:4d:24:ba:e4
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:18:4d:24:ba:e4
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=2
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 a0
  key_nonce - hexdump(len=32): 0d 26 af c8 f9 e2 7b 74 b5 ee 17 d0 a1 2a 63 fc dd b6 ff d8 49 72 4b 04 05 7e 67 e0 71 ba b3 8c
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
RSN: msg 1/4 key data - hexdump(len=0):
WPA: Renewed SNonce - hexdump(len=32): f4 f6 e4 89 0e a4 fa c2 4e 80 5d f9 f5 d8 f0 5a ce 70 53 ca a5 7f 6e 98 e7 2b ad cf 62 49 96 42
WPA: PTK derivation - A1=00:1d:7e:9d:e6:9d A2=00:18:4d:24:ba:e4
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:18:4d:24:ba:e4
IEEE 802.1X RX: version=1 type=3 length=151
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=56
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 a1
  key_nonce - hexdump(len=32): 0d 26 af c8 f9 e2 7b 74 b5 ee 17 d0 a1 2a 63 fc dd b6 ff d8 49 72 4b 04 05 7e 67 e0 71 ba b3 8c
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 5b 8b 01 64 e1 d0 43 ee 81 37 14 9a 3c 3c f5
RSN: encrypted key data - hexdump(len=56): 2f 92 07 28 91 ca d3 99 e8 e0 b4 94 36 f7 09 98 cc 5a 7b 82 60 c5 36 5b ab 21 c6 76 d5 7b 71 23 22 7c 73 5d ed ca 14 f7 44 d5 9d 00 c3 bc 28 d2 2a 40 b1 b3 69 0b 36 51
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 b7 84 2e 46 0c 78 d8 2e 9e dd 46 da bc fd 88 7e dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=16).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with 00:18:4d:24:ba:e4 [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:18:4d:24:ba:e4 completed (reauth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:18:4d:24:ba:e4
IEEE 802.1X RX: version=1 type=3 length=151
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=56
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 a2
  key_nonce - hexdump(len=32): 0d 26 af c8 f9 e2 7b 74 b5 ee 17 d0 a1 2a 63 fc dd b6 ff d8 49 72 4b 04 05 7e 67 e0 71 ba b3 8c
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 8a 7d 5e 72 37 a6 35 7e 2b c0 c0 21 35 16 b9 03
RSN: encrypted key data - hexdump(len=56): 2f 92 07 28 91 ca d3 99 e8 e0 b4 94 36 f7 09 98 cc 5a 7b 82 60 c5 36 5b ab 21 c6 76 d5 7b 71 23 22 7c 73 5d ed ca 14 f7 44 d5 9d 00 c3 bc 28 d2 2a 40 b1 b3 69 0b 36 51
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
State: COMPLETED -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 b7 84 2e 46 0c 78 d8 2e 9e dd 46 da bc fd 88 7e dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=16).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with 00:18:4d:24:ba:e4 [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAP: EAP entering state DISABLED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:18:4d:24:ba:e4 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 1039 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:24:ba:e4 ssid='<ssid>'
Try to find non-WPA AP
Trying to associate with 00:18:4d:24:ba:e4 (SSID='<ssid>' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
Authentication with 00:18:4d:24:ba:e4 timed out.
BSSID 00:18:4d:24:ba:e4 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     53 70 69 72 61                                    <ssid>
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 1039 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - blacklisted
1: 00:15:e9:28:6d:4e ssid='MyHome' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:b5:37:0e:83 ssid='hornerhome' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
3: 00:60:64:15:63:bb ssid='wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - blacklisted
1: 00:15:e9:28:6d:4e ssid='MyHome' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:b5:37:0e:83 ssid='hornerhome' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
3: 00:60:64:15:63:bb ssid='wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:18:4d:24:ba:e4 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:24:ba:e4 ssid='<ssid>'
Try to find non-WPA AP
Trying to associate with 00:18:4d:24:ba:e4 (SSID='<ssid>' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
Authentication with 00:18:4d:24:ba:e4 timed out.
Added BSSID 00:18:4d:24:ba:e4 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 1039 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:24:ba:e4 ssid='<ssid>'
Try to find non-WPA AP
Trying to associate with 00:18:4d:24:ba:e4 (SSID='<ssid>' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
Authentication with 00:18:4d:24:ba:e4 timed out.
BSSID 00:18:4d:24:ba:e4 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     53 70 69 72 61                                    <ssid>
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 1039 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - blacklisted
1: 00:15:e9:28:6d:4e ssid='MyHome' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:b5:37:0e:83 ssid='hornerhome' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
3: 00:60:64:15:63:bb ssid='wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - blacklisted
1: 00:15:e9:28:6d:4e ssid='MyHome' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:b5:37:0e:83 ssid='hornerhome' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
3: 00:60:64:15:63:bb ssid='wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:18:4d:24:ba:e4 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:24:ba:e4 ssid='<ssid>'
Try to find non-WPA AP
Trying to associate with 00:18:4d:24:ba:e4 (SSID='<ssid>' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c07 len=122
AssocReq IE wireless event - hexdump(len=114): 00 05 53 70 69 72 61 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 1e 00 90 4c 33 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 2d 1a 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 dd 07 00 50 f2 02 00 01 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=102
AssocResp IE wireless event - hexdump(len=94): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 2d 1a 6c 18 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:18:4d:24:ba:e4
Association info event
req_ies - hexdump(len=114): 00 05 53 70 69 72 61 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 1e 00 90 4c 33 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 2d 1a 0c 00 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 06 00 00 00 00 00 00 dd 07 00 50 f2 02 00 01 00
resp_ies - hexdump(len=94): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c dd 18 00 50 f2 02 01 01 80 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 2d 1a 6c 18 03 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:18:4d:24:ba:e4
No keys have been configured - skip key clearing
Associated with 00:18:4d:24:ba:e4
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:18:4d:24:ba:e4
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=2
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 a3
  key_nonce - hexdump(len=32): 95 7e 77 50 21 ba a3 2c 6d b6 8f 48 79 72 bb a4 c5 ee 27 40 51 2a 53 1c 9d 26 bf b8 a9 e2 6b 94
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
RSN: msg 1/4 key data - hexdump(len=0):
WPA: Renewed SNonce - hexdump(len=32): 82 ad 2f 31 09 64 e6 d4 c1 55 93 a0 6b 86 9c f9 dc b8 dc 89 2d 68 db 4d f6 66 1f db c0 ee bc 54
WPA: PTK derivation - A1=00:1d:7e:9d:e6:9d A2=00:18:4d:24:ba:e4
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:18:4d:24:ba:e4
IEEE 802.1X RX: version=1 type=3 length=151
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=56
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 a4
  key_nonce - hexdump(len=32): 95 7e 77 50 21 ba a3 2c 6d b6 8f 48 79 72 bb a4 c5 ee 27 40 51 2a 53 1c 9d 26 bf b8 a9 e2 6b 94
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): fe b1 84 0c 36 1e 93 6e 75 8b 4f f8 dc e0 ce 96
RSN: encrypted key data - hexdump(len=56): b7 a9 10 02 48 ab ed 38 21 43 72 35 bd 7f 75 99 65 7d ad 5b 24 f1 61 e9 8c 70 70 05 fb a9 9d a1 24 30 bd 84 34 fd 2a f9 04 92 f1 e5 c0 7e 88 fd 47 e4 1b e4 c8 75 f5 e2
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:4d:24:ba:e4 (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 b7 84 2e 46 0c 78 d8 2e 9e dd 46 da bc fd 88 7e dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=16).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with 00:18:4d:24:ba:e4 [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:18:4d:24:ba:e4 completed (reauth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c09 len=32
PMKID candidate wireless event: flags=0x0 index=0 bssid=00:18:4d:24:ba:e4
RSN: PMKID candidate event - bssid=00:18:4d:24:ba:e4 index=0 preauth=0
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:18:4d:24:ba:e4 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 1039 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:24:ba:e4 ssid='<ssid>'
Try to find non-WPA AP
Trying to associate with 00:18:4d:24:ba:e4 (SSID='<ssid>' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
Authentication with 00:18:4d:24:ba:e4 timed out.
BSSID 00:18:4d:24:ba:e4 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     53 70 69 72 61                                    <ssid>
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 1039 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - blacklisted
1: 00:15:e9:28:6d:4e ssid='MyHome' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:b5:37:0e:83 ssid='hornerhome' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
3: 00:60:64:15:63:bb ssid='wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   skip - blacklisted
1: 00:15:e9:28:6d:4e ssid='MyHome' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:b5:37:0e:83 ssid='hornerhome' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
3: 00:60:64:15:63:bb ssid='wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:18:4d:24:ba:e4 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:24:ba:e4 ssid='<ssid>'
Try to find non-WPA AP
Trying to associate with 00:18:4d:24:ba:e4 (SSID='<ssid>' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
Authentication with 00:18:4d:24:ba:e4 timed out.
Added BSSID 00:18:4d:24:ba:e4 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 1039 bytes of scan results (4 BSSes)
CTRL-EVENT-SCAN-RESULTS
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:18:4d:24:ba:e4 ssid='<ssid>' wpa_ie_len=0 rsn_ie_len=20 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:18:4d:24:ba:e4 ssid='<ssid>'
Try to find non-WPA AP
Trying to associate with 00:18:4d:24:ba:e4 (SSID='<ssid>' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
```

> **kevdog said:**
> On terminal #3 (After typing on #2 and waiting for some type of confirmation that address has been recognized)
sudo dhclient <interface>```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1d:7e:9d:e6:9d
Sending on   LPF/wlan0/00:1d:7e:9d:e6:9d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.21 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.21 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.1.21
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```Interestingly enough, I actually get an IP address now. Unfortunately, Internet still doesn't work and on top of that, dhclient seems to kill the wireless connection on my working WinXP laptop at the same time.

> **kevdog said:**
> Also if you could provide the following
sudo iwlist <interface> auth
sudo lshw -C network
sudo iwlist <interface> scan```
wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		WPA2
          Current Key management :
		PSK
          Current Pairwise cipher :
		CCMP
          Current Pairwise cipher :
		CCMP
          Current Authentication algorithm :
		open
``````
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:d6:79:f7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:1d:7e:9d:e6:9d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.53+Linksys, A Division of Cisc latency=128 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
``````
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:24:BA:E4
                    ESSID:"<Wedge009 Network Name>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:85/100  Signal level:-38 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:60:64:15:63:BB
                    ESSID:"wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:15:E9:28:6D:4E
                    ESSID:"MyHome"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by gTinker on 2008-11-26
Wedge009,
Do you have the ethernet cable from the wired ethernet card plugged into the router at the same time you are trying to get a wireless IP address?

---

### Post by Wedge009 on 2008-11-26
No. I disconnect the ethernet cable before attempting to access through the wireless card. Otherwise, how would I know if it was the wireless card and not the ethernet connection that was working?

---

### Post by Wedge009 on 2008-12-01
A quick test of the card on a Windows XP system yielded no problems, connection was quick and easy. So it seems to be a problem with the software setup rather than a hardware mismatch...

---

### Post by kevdog on 2008-12-01
Why are you using ndiswrapper?? Can you not use the madwifi driver for this chipset?  I can't seem to get my current ndiswrapper version to work with wpa2 either (but it does with wpa).  Both madwifi and b43 (depending on the card) do connect with wpa2 for me at least, making me believe at least that it is a driver problem.

---

### Post by Wedge009 on 2008-12-01
I used ndiswrapper because it was the first thing I tried and it worked fine with the router I first accessed. I am not familiar with either madwifi or b43, but I will have a look around and see what I can find out about them.

Edit: Okay, so I installed madwifi-tools, but everything seems to refer to "athX" devices, and the card only shows up as "wlan0". Here is where I show my lack of experience and ask for a walk-through of how to use madwifi if, as you suggest, it would be better to work with the card than ndiswrapper.

---

### Post by Wedge009 on 2009-03-12
Finally got wireless access. Yay.

Things were starting to break down, I finally decided to do a fresh install of Kubuntu Intrepid Ibex (the laptop had been continually upgraded ever since Kubuntu Dapper Drake) just over a month ago. Since then I also updated to KDE 4.2 (which, for me personally, is finally on the same level as KDE 3.5 in terms of functionality).

Today, purely on a whim, I decided to have another go at getting my wireless adapter to work... and it did! I simply connected using KDE's graphical front-end to the Network Manager in the tray bar. No mucking around with wpa_supplicant.conf, no installation of Windows XP drivers using ndiswrapper, no fuss at all.

This is how it should be for the user. I don't know whether it was the fresh installation that did the trick or whether any improvements showed through with KDE 4.2, but I am finally relieved that my wireless adapter isn't going to waste any more.

---

