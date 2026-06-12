---
title: "DHCP fails in wireless network with WPA,wpa_supplicant and ndiswrapper, Netgear WG121"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Grizzlitiger on 2007-07-10
Hi there,

I know there a lots of similar posts but there didn't quite have the same problem as I do and after trying all day yesterday and all morning today I figured that now would be the time to seek help.

Firstly some infos: I have re-installed **Feisty Fawn** on my computer and want to set up a wireless network connection using **wpa_supplicant** and **wpa1 encryption** to my home network with **no SSID broadcast**. I have succeeded to do so using the following wpa_supplicant.conf file on my laptop and the following /etc/network/interfaces:

```
 ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
# 0: Der Treiber des Interfaces kümmert sich um das Scannen von Netzen und die AP Auswahl. 
#    Dieser Mode sollte benutzt werden, wenn man eine Verschlüsselung auf ein Kabelnetzwerk legt.
# 1: wpa_supplicant kümmert sich um das Scannen von Netzen und die AP Auswahl.
# 2: Fast wie 0, es wird aber mit Hilfe von Sicherheitsrichtlinien und der SSID zu APs verbunden (BSSID wird nicht unterstützt)
# 
# Normalerweise funktioniert entweder Mode 1 oder Mode 2.
**ap_scan=2** *It even worked without option 2 on my laptop*

network={
        ssid="My Network SSID"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="My PSK Passphrase (no HEX since in "" !!)"
}
 
```

```
 [...] 
#The primary network interface

iface eth0 inet dhcp
	wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto eth0

[...] 
```

This was very nice and I was hoping to get a working connection on my PC too. However unfortunately I have a wlan usb adaptor **Netgear WG121** for which I have to use **ndiswrapper** to use the windows driver. I have installed ndiswrapper using the text console and got ```

ndiswrapper -l
netwg121: driver installed
device (0046:4210) present (alternate driver: prism54usb)
```

I expected "driver present hardware present" but seemed close enough?! I read on some forums that **prism54usb** often messes it up so I **blacklisted** it and prism54common.

I now start the connection in debug mode using 
```
sudo wpa_supplicant -i wlan0 -D wext -c/etc/wpa_supplicant/wpa_supplicant.conf -d  
```
And -obviously after debugging it a little - I get no more errors! When I now enter **iwconfig** I even get 
```
lo        no wireless extensions.

irda0     no wireless extensions.

wlan0      IEEE 802.11g  ESSID:"My SSID!"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: My AP!!!   
          Bit Rate:18 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/100  Signal level=-77 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3439   Missed beacon:0

```
Which is great...I thought. However, entering **sudo dhclient wlan0** I am **not able to get an IP from my AP**!!!

**Can anyone help me please?**

[RIGHT]Thanks for any help in advance!
Johannes[/RIGHT]

**Additional info:**
Also, I have tried to connect avoiding the use of the wpa_supplicant.conf file as described in [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) - which is btw a pretty good HOWTO - using  this /etc/network/interfaces
```

[...]
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa ssid MySSID *Notice: No "" !*
**wpa-scan 2**
wpa-proto WPA 
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk MyPSK(HEX!!) *Notice: No "" !*
[...]

```
But then I** don't get my SSID** on entering **iwconfig** so I figured this doesn't work as well as the prior "solution".

---

### Post by kevdog on 2007-07-10
I read through your post and noticed the following:

> eth0      IEEE 802.11g  ESSID:"My SSID!"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: My AP!!!   
          Bit Rate:18 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/100  Signal level=-77 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3439   Missed beacon:0

sudo dhclient wlan0

Shouldnt it be:
sudo dhclient eth0 rather than wlan0??

---

### Post by Grizzlitiger on 2007-07-10
Hi,

thanks for your reply and for reading through my post! 
No I was a bit sloppy there and pasted the output of my laptop since it is the same - on my laptop it's eth0 on my PC it's wlan0 just to make it even more confusing.

Cheers
Johannes

---

### Post by kevdog on 2007-07-10
Does your card connect without WPA -- meaning on an unencrypted network??

If so what is result of:
iwlist scan

I also take it you have installed the wpasupplicant package??

Also just to make sure everything is consistent, wlan0 also needs to be eth0 here:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa ssid MySSID Notice: No "" !
wpa-scan 2
wpa-proto WPA 
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk MyPSK(HEX!!) Notice: No "" !

If everything is OK up to this point please post
lshw -C network

Does anything show an error in
/var/log/boot
/var/log/syslog
dmesg

That would help explain your error??

That would suggest a possiblity for the error?

---

### Post by Grizzlitiger on 2007-07-10
Hello,

I will check whether it connects to an open network later today I didn't have enough time any more - I tried with **WEP** and it didn't work either and funnily it **didn't even show the network** on entering **iwconfig.**
Yes **wpa_supplicant is installed ** (otherwise I wouldn't have been able to run ```
sudo wpa_supplicant -i wlan0 -D wext -c/etc/wpa_supplicant/wpa_supplicant.conf -d
```). Output of **dmesg, /var/log/syslog and /var/log/boot normal** - boot is empty. I could only attach the output of **lshw -C network** unfortunately because the other files are too large - I could put them on my webspace if required. The only thing in these files is **dhcp failing loads of times** and an **odd output of network manager** which I installed again but which should be inactive (and has no wireless setting except for roaming mode) - see below. The output of **iwlist scan** is OK showing my network.
The wireless interface on my PC is wlan0 so that's OK in the post.

**Thanks very much for your help and time again!**
Johannes

```

Jul 10 18:26:43 johannes-desktop NetworkManager: <debug info>^I[1184084803.094602] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_66f_8000_0002F68C31688A03_if0_scsi_host_scsi_device_lun0'). 
Jul 10 18:26:43 johannes-desktop NetworkManager: <debug info>^I[1184084803.161740] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_66f_8000_0002F68C31688A03_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul 10 18:26:43 johannes-desktop NetworkManager: <debug info>^I[1184084803.181796] nm_hal_device_added (): New device added
(hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4868_B62B'). 
Jul 10 18:26:43 johannes-desktop hald: mounted /dev/sde1 on behalf of uid 1000
Jul 10 18:26:44 johannes-desktop avahi-autoipd(eth0)[6956]: Successfully claimed IP address 169.254.5.187
Jul 10 18:26:44 johannes-desktop avahi-autoipd(eth0)[6956]: fopen() failed: Permission denied
Jul 10 18:26:54 johannes-desktop kernel: [ 2005.144000] eth1: link down
Jul 10 18:26:54 johannes-desktop kernel: [ 2005.144000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul 10 18:26:54 johannes-desktop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Jul 10 18:26:54 johannes-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jul 10 18:26:54 johannes-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jul 10 18:26:54 johannes-desktop dhclient: All rights reserved.
Jul 10 18:26:54 johannes-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul 10 18:26:54 johannes-desktop dhclient: 
Jul 10 18:26:55 johannes-desktop dhclient: Listening on LPF/eth1/00:15:e9:ef:ce:de
Jul 10 18:26:55 johannes-desktop dhclient: Sending on   LPF/eth1/00:15:e9:ef:ce:de
Jul 10 18:26:55 johannes-desktop dhclient: Sending on   Socket/fallback
Jul 10 18:26:59 johannes-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jul 10 18:27:05 johannes-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jul 10 18:27:11 johannes-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jul 10 18:27:14 johannes-desktop ntpdate[7087]: can't find host ntp.ubuntu.com 
Jul 10 18:27:14 johannes-desktop ntpdate[7087]: no servers can be used, exiting
Jul 10 18:27:23 johannes-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jul 10 18:27:30 johannes-desktop dhclient: No DHCPOFFERS received.
Jul 10 18:27:30 johannes-desktop dhclient: No working leases in persistent database - sleeping.
Jul 10 18:27:30 johannes-desktop avahi-autoipd(eth1)[7134]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jul 10 18:27:30 johannes-desktop avahi-autoipd(eth1)[7134]: Successfully called chroot().
Jul 10 18:27:30 johannes-desktop avahi-autoipd(eth1)[7134]: Successfully dropped root privileges.
Jul 10 18:27:30 johannes-desktop avahi-autoipd(eth1)[7134]: fopen() failed: Permission denied
Jul 10 18:27:30 johannes-desktop avahi-autoipd(eth1)[7134]: Starting with address 169.254.12.67
Jul 10 18:27:36 johannes-desktop avahi-autoipd(eth1)[7134]: Callout BIND, address 169.254.12.67 on interface eth1
Jul 10 18:27:36 johannes-desktop avahi-daemon[5189]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.12.67.
Jul 10 18:27:36 johannes-desktop avahi-daemon[5189]: New relevant interface eth1.IPv4 for mDNS.
Jul 10 18:27:36 johannes-desktop avahi-daemon[5189]: Registering new address record for 169.254.12.67 on eth1.IPv4.
Jul 10 18:27:36 johannes-desktop avahi-autoipd(eth1)[7135]: client: RTNETLINK answers: File exists
Jul 10 18:27:40 johannes-desktop avahi-autoipd(eth1)[7134]: Successfully claimed IP address 169.254.12.67
Jul 10 18:27:40 johannes-desktop avahi-autoipd(eth1)[7134]: fopen() failed: Permission denied
Jul 10 18:27:50 johannes-desktop dhclient: There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Jul 10 18:27:50 johannes-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jul 10 18:27:50 johannes-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jul 10 18:27:50 johannes-desktop dhclient: All rights reserved.
Jul 10 18:27:50 johannes-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul 10 18:27:50 johannes-desktop dhclient: 
Jul 10 18:27:51 johannes-desktop dhclient: Bind socket to interface: No such device
Jul 10 18:27:51 johannes-desktop dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Jul 10 18:27:51 johannes-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jul 10 18:27:51 johannes-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jul 10 18:27:51 johannes-desktop dhclient: All rights reserved.
Jul 10 18:27:51 johannes-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul 10 18:27:51 johannes-desktop dhclient: 
Jul 10 18:27:52 johannes-desktop dhclient: Bind socket to interface: No such device
Jul 10 18:27:52 johannes-desktop kernel: [ 2063.464000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 10 18:27:53 johannes-desktop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Jul 10 18:27:53 johannes-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jul 10 18:27:53 johannes-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jul 10 18:27:53 johannes-desktop dhclient: All rights reserved.
Jul 10 18:27:53 johannes-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul 10 18:27:53 johannes-desktop dhclient: 
Jul 10 18:27:54 johannes-desktop dhclient: Listening on LPF/wlan0/00:09:5b:d1:9b:4c
Jul 10 18:27:54 johannes-desktop dhclient: Sending on   LPF/wlan0/00:09:5b:d1:9b:4c
Jul 10 18:27:54 johannes-desktop dhclient: Sending on   Socket/fallback
Jul 10 18:27:54 johannes-desktop kernel: [ 2064.972000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 10 18:27:55 johannes-desktop avahi-daemon[5189]: Registering new address record for fe80::209:5bff:fed1:9b4c on wlan0.*.
Jul 10 18:27:56 johannes-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jul 10 18:28:02 johannes-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jul 10 18:28:04 johannes-desktop kernel: [ 2075.180000] wlan0: no IPv6 routers present
Jul 10 18:28:09 johannes-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jul 10 18:28:10 johannes-desktop ntpdate[7170]: can't find host ntp.ubuntu.com 
Jul 10 18:28:10 johannes-desktop ntpdate[7170]: no servers can be used, exiting
Jul 10 18:28:24 johannes-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 10 18:28:27 johannes-desktop dhclient: No DHCPOFFERS received.

```

---

### Post by kevdog on 2007-07-10
If you issue command 
iwlist scan

And your network doesnt even show up -- then there is definitely a problem -- and its not related to WPA. Likely a driver related problem.

Did you just try with the native prism drivers??
To quickly check, all you need to do is blacklist ndiswrapper and then either comment out (#) the prism blacklist statements or remove them.

The first thing you want to check after a reboot is if your network can even be detected.

---

### Post by Grizzlitiger on 2007-07-11
Hi there,

sorry for the late reply and thanks for your post.

**The output of iwlist scan is OK - even using wpa encryption:**
```
 johannes@johannes-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: MYMAC
                    ESSID:"MYSSID!"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
 
```

**I don't think it's a driver-related problem** since this would most likely not allow me to scan for the network then but instead not even give me my interface wlan0 as output - **although the GUI for ndiswrapper gives me Hardware present: No**. I tried with the **native drivers but they don't work** yielding exactly this problem of not being able to do anything with the interface. I am very sure you **have to use ndiswrapper** here since this is the info I got here: [https://help.ubuntu.com/community/WifiDocs/Device/WG121/](https://help.ubuntu.com/community/WifiDocs/Device/WG121/) - **this all seems to work for me until I issue sudo dhclient wlan0**. Also with SUSE I used ndiswrapper and it worked after a long long time of trying...

I have tried to connect to an unencrypted network. **Everything works except for dhcp! (so same as here!)** 

As info here is the output of **iwevent**:
```
  johannes@johannes-desktop:~$ iwevent
Waiting for Wireless Events from interfaces...
13:04:56.227228   wlan0    New Access Point/Cell address:Not-Associated
13:04:56.227601   wlan0    Set Mode:Managed
13:04:56.227921   wlan0    Set ESSID:"MYSSID"
13:04:57.530636   wlan0    Association Request IEs:00164A6F68616E6E65732E7365696E2E4E65747A7765726B010402040B1632080C1218243048606CDD160050F20101000050F20201000050F20201000050F20
13:04:57.530698   wlan0    Association Response IEs:010482848B9632080C1218243048606C
13:04:57.530709   wlan0    New Access Point/Cell address:MYMAC
13:05:10.551321   wlan0    New Access Point/Cell address:Not-Associated
13:05:10.567054   wlan0    Set Mode:Managed
13:05:10.567081   wlan0    Set ESSID:"MYSSIDD"
13:05:11.860733   wlan0    Association Request IEs:00164A6F68616E6E65732E7365696E2E4E65747A7765726B010402040B1632080C1218243048606CDD160050F20101000050F20201000050F20201000050F20
13:05:11.860810   wlan0    Association Response IEs:010482848B9632080C1218243048606C
13:05:11.860831   wlan0    New Access Point/Cell address:MYMAC

```

I really don't know what else I could do and I hate spending so much time on such a fundamental thing as connecting to the internet....:(

**UPDATE**
I have moved my computer to another room which is directly above the router. I get connection quality of about 50/100-70/100 most of times. I** even got an IP once but only once **- tried about 15 times or so...so this is quite nice info since it means that **drivers and config should be OK** but now I don't know why it only worked once. I have got related problems with my **laptop which I have to move around every single time when I want to connect to the network until after some time I finally find I spot where I'm able to connect** - however, **after the connection has been established I usually don't have any problems** any more. Anyway I think the signal in the room above the AP (about 3-5 ft above the AP maybe) should really be strong enough to allow a connection with network manager giving some 90% +signal strength...

any ideas?

---

