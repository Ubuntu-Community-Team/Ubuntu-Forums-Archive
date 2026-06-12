---
title: "Netgear WG111v2 installed but not connecting to network"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by t_anjan on 2007-01-14
What does it take to get a simple Wireless LAN to work on this OS? I'm using Edgy and apparently the Netgear WG111v2 USB adapter works 'out-of-the-box'. It did get detected and was able to scan and detect networks, but could not connect to ANY network. The available wireless network is unencrypted. 
I have been searching around on this forum for two days now and have tried out every single HOW-TO that is related to Wi-FI and WG111v2. I have blacklisted the default RT8187 driver and gotten my adapter to work with ndsiwrapper. Still no luck.

I uninstalled the default Network Manager applet and installed the version from SVN, still no difference.

I tried out another piece of software called 'Connection manager' from [http://www.ubuntuforums.org/showthread.php?t=299462](http://www.ubuntuforums.org/showthread.php?t=299462) using which also I could not establish a connection.

'iwlist scan' shows me the available network.
But 
```
sudo iwconfig wlan0 essid <routerESSID> channel <channel>
```

gives the following output:
```
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.
```

I have literally tried everything. If it is THIS hard to connect to an unencrypted network, I wonder how many weeks I have to spend to get WPA working.
And a relatively inexperienced user could have done all this on Windows in less than 2 minutes.
Could there be a worse experience for a new Linux user?
:rolleyes:

---

### Post by Floppyjoe on 2007-01-14
You may need to enter this configuration manually into /etc/network/interfaces to get your wireless to work.

Type this into the terminal:
```
sudo gedit /etc/network/interfaces
```

You will get something like this:
> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid WarGames
wireless-channel 7
wireless-mode managed


Where you enter your unique interface configuration.
You will need to enter the essid, channel and mode managed.
the following will show you your interface name:
```
iwconfig
```
Then add this for your interface name using the channel number your router is using and your own routers name:

> wireless-essid YourRouterName
wireless-channel 7
wireless-mode managed

Then restart.

---

### Post by t_anjan on 2007-01-15
Thanks for the help. I appreciate it.

I've already added my wireless network config to the interfaces file. The only change I notice after doing that is a huge increase in the boot-up time.  But other than that, no positive outcome.

My wireless-mode is 'master'. 

Does the order of the lines in the interfaces file matter?

I'm using the AMD64 version of Edgy, BTW.

After adding those lines to the interfaces file, my computer should be connected to the network on startup, right? Or are there any additional steps to perform to establish connection?

I'm currently using the net through a wired connection to the router. While trying to establish a wireless connection, is it enough if I disconnect the ethernet cable from the router or do I have to disconnect from both sides?

---

### Post by Floppyjoe on 2007-01-15
I'm not sure if the order of the lines matters but it may. 
About the wireless mode, I can't see any option on my router for choosing either master or managed. Mine is Mode=Access Point which works when i use wireless-mode managed.
If you are using ndiswrapper you need to use the command:
```
sudo ndiswrapper -m
```
to add the ndiswrapper module to /etc/modules so it loads automatically at boot time.

---

### Post by t_anjan on 2007-01-15
Here's more info:

My router is configured using WPA-PSK encryption. 
I've got a Netgear WG111v2 USB dongle that I have installed using NDISWRAPPER. 

'iwlist scan' shows me the available network:

```
anjan@supernal:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:F0:03:06
                    ESSID:"AnjanWireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality:17  Signal level:0  Noise level:2
                    Extra: Last beacon: 0ms ago
```

Output of 'iwconfig'
```
anjan@supernal:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"AnjanWireless"  
          Mode:Managed  Channel=11  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Contents of my 'interfaces' file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid AnjanWireless
wpa-driver wext
wpa-conf master
wpa-ssid AnjanWireless
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <hidden>
```


First, before reading this How-To, I had my 'interfaces' file without all the wpa config commands. Instead I had these two lines:

```
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Contents of my 'wpa_supplicant.conf' file:

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="AnjanWireless"
	scan_ssid=1
       	key_mgmt=WPA-PSK
	proto=WPA
       	#pairwise=CCMP TKIP
       	#group=CCMP TKIP
        #psk="<hidden>"
        psk=<hidden>
}
```

Everything seems OK to me. But I just cannot hook up to my wireless router, even after disabling my wired connection (eth0) and disconnecting my ethernet cable.

Please, I've spent three days on this now and Ubuntu is really starting to frustrate me. Someone help!

---

### Post by t_anjan on 2007-01-15
> **Floppyjoe said:**
> I'm not sure if the order of the lines matters but it may. 
About the wireless mode, I can't see any option on my router for choosing either master or managed. Mine is Mode=Access Point which works when i use wireless-mode managed.
If you are using ndiswrapper you need to use the command:
```
sudo ndiswrapper -m
```
to add the ndiswrapper module to /etc/modules so it loads automatically at boot time.

I've already configured the ndiswrapper module to load at boot time.
```
modprobe config already contains alias directive
```

---

### Post by aberry5555 on 2007-01-15
This may very well be a silly question but are you sure you're using the 64 bit windows drivers? Ndiswrapper works on 64 bit but only if you give it 64 bit drivers.

---

### Post by t_anjan on 2007-01-15
> **aberry5555 said:**
> This may very well be a silly question but are you sure you're using the 64 bit windows drivers? Ndiswrapper works on 64 bit but only if you give it 64 bit drivers.

Actually, that's a very good question because Netgear doesn't provide 64 bit drivers.

So I used the Win 98 drivers, as was mentioned in one of the tutorials.

But, if that driver is not supposed to work, how am I able to scan for available networks?

Edit:
Update:
OK, I thought, why not use 64 bit drivers provided by Realtek, for windows x64, and then use ndiswrapper on them. So, I did that.

The dongle got detected and is able to scan and detect networks. But still no association with Access Point.

---

### Post by aberry5555 on 2007-01-15
When I set up my wifi I had to log in on a wired card to find out the SSID and WEP key seperately, then, in the options for wifi in the network manager, enter both in there without scanning. It seemed to work OK for me but if you need to be able to scan then I'm not sure how that is meant to work :S

---

### Post by t_anjan on 2007-01-15
Ya, I'm saying that I'm able to scan and detect the network, I mean that my USB dongle is working on Ubuntu. It is able to see the network, but even though I'm giving it the correct SSID, channel and everything else it could possibly ask for, still it can't connect to the network.

---

### Post by aberry5555 on 2007-01-15
huh, weird. I dont know what to suggest then :S

---

### Post by Floppyjoe on 2007-01-15
You need to add the line:
> wireless-channel 11
In your /etc/network/interfaces file I think.

Here is how I set up my Wpa on my laptop:This was in my etc/network/interfaces file:
eth1 is my wireless interface:
> auto lo
iface lo inet loopback


#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid WarGames
wireless-channel 7
wireless-mode managed
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


This is how my /etc/wpa_supplicant.conf looks:
> network={
        ssid="WarGames"
        #psk="secretpassword"
        proto=WPA
        key_mgmt=WPA-PSK

        psk=wouldn't you like to know
}

---

### Post by t_anjan on 2007-01-16
To heck with WPA. I've temporarily disabled all security on my router. I want Edgy to connect to my unsecured router. 

My "interfaces" file:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid AnjanWireless
wireless-channel 2
wireless-mode managed
```

Output of **sudo /etc/init.d/networking restart**

```
anjan@supernal:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 8963
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:08:c7:0e
Sending on   LPF/wlan0/00:18:4d:08:c7:0e
Sending on   Socket/fallback
[B][COLOR="Red"]Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.[/COLOR][/B]
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:08:c7:0e
Sending on   LPF/wlan0/00:18:4d:08:c7:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I think these two lines are the most important:
```
[B][COLOR="Red"]Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.[/COLOR][/B]
```

I have no idea why SET is not working. Any ideas? I can't even connect to an unsecured network!!!

---

### Post by cpsalvestrini on 2007-01-16
In my case, I had a similar issue with a similar card from the same manufacturer. I had to install the XP drivers with ndiswrapper instead of using the Windows 98 ones. Using the XP drivers solved all my connectivity problems.

---

### Post by t_anjan on 2007-01-16
> **cpsalvestrini said:**
> In my case, I had a similar issue with a similar card from the same manufacturer. I had to install the XP drivers with ndiswrapper instead of using the Windows 98 ones. Using the XP drivers solved all my connectivity problems.

But, are you using AMD64 version of Ubuntu? Netgear doesn't provide 64 bit drivers.

---

