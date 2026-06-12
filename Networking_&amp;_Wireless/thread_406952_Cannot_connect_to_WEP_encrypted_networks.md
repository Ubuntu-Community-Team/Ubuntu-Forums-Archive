---
title: "Cannot connect to WEP encrypted networks"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by rustysail on 2007-04-11
Hello,

I have a Netgear WG311T wireless PCI adapter it is listed as one of the cards that works out of the box here.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

On my first log in, Ubuntu 6.10 recognized the card and connected me to my neighbor's wireless network.  When I tried to switch to my network, I found that it would not connect.  It seems that the card does not get WEP out of the box.

I found that it needs a bit of work for that so I followed the link to this site.

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

On the last step, I got the following.
```
root@rusty-desktop:/home/rusty# /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping NetworkManager dispatcher                                    [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping NetworkManager daemon                                        [ ok ] 
 * Stopping DBUS aware dhcp client: dhcdbd                               [ ok ] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                              [ ok ] 
 * Starting DBUS aware dhcp client: dhcdbd                               [ ok ] 
 * Starting NetworkManager daemon                                        [ ok ] 
 * Starting NetworkManager dispatcher                                    [ ok ] 
 * Starting System Tools Backends system-tools-backends                  [ ok ] 

```

After seeing this error, I used apt-get.
```
apt-get install avahi-daemon
```
Then I tried the last step again, making sure to touch the wpasupplicant file again, but I still got the same error message.  It will not let me connect to the network.

I would appreciate it if someone could explain what I'm messing up, or offer an alternate solution.

---

### Post by spd106 on 2007-04-11
You can ignore avahi, you will get that fail message if you haven't turned on service discovery, it's disabled by default.

Have you tried both ascii and hex versions of the WEP password?

---

### Post by rustysail on 2007-04-11
I do not have an ascii version.  Normally, I connect using a 10 digit code made of numbers.  However, there is also a 26 digit code I found somewhere made of numbers and letters.  I don't know what this second code is, but I have never used it in windows or linux.  I think it might be for file sharing though.

---

### Post by panicbyte on 2007-04-11
have you tried using nm-applet to manage your wireless??

for some reason nm-applet makes using WPA/WEP very easy

---

### Post by chili555 on 2007-04-11
I may be a bit confused here. Your post says you cannot connect to WEP encrypted networks, yet you followed a tutorial dealing with WPA and installed wpa_supplicant. WEP and WPA are two very different things. wpa_supplicant is not needed for WEP.

If you are sure you have WEP and you have a 10-digit hex key, connecting should be as easy as:```
sudo iwconfig ath0 essid <your_essid>
sudo iwconfig ath0 key <your_key>
sudo dhclient ath0
```Sometimes, input of WEP keys is helped by adding 'open' or 'restricted' after the key, thus:```
sudo iwconfig ath0 key <your_key> open
```Post back so WEP fans will know the outcome.

---

### Post by rustysail on 2007-04-11
Thanks for the suggestion.  Unfortunetley, I'm currently using nm-applet.  

I have already tried using the method with iwconfig.  I the reason I followed the tutorial is because, the Ubuntu docs suggested it.
[INDENT]"Detected in Network Settings as ath0 and started working once the WAP details were input. Version WG311TGE (sold as WG311T) works out of the box on Dapper 6.06. Same for WGT311TFS in Edgy; [WWW] used for WEP and/or WPA."[/INDENT]

This quote is from this page.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

My wireless card is the second one down.

Here is some more information that might help.

sudo dhclient
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wifi0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:4d:6e:33:28
Sending on   LPF/ath0/00:18:4d:6e:33:28
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Also when I do dmesg right after dhclient I see this at the bottom.
```
[17179992.676000] ath0: no IPv6 routers present

```

My router is not very new.  Is it possible that I should have it look for IPv5 routers and if so how?

---

### Post by chili555 on 2007-04-11
This:> Detected in Network Settings as ath0 and started working once the WAP details were input.Just means someone got the card working as soon as he input his WPA settings, not that *you* have to input your settings, since you have no WPA settings.

This:> ath0: no IPv6 routers presentis trivial. You can safely ignore it.

If you are using nm-applet, also known as NetworkManager, you need to make some changes in System - Administration - Networking. Check here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by rustysail on 2007-04-12
I have already configured my card through iwconfig and system-administration-networking.  On that link you sent me, I saw something mentioned about ndiswrapper requiring you to add a line to /etc/modules.  My card uses madwifi drivers.  Is it possible that I would have to edit this file as well.

---

### Post by chili555 on 2007-04-12
> Is it possible that I would have to edit this file as well.Doubtful.

If your card is recognized and even connects to the neighbor's network, the driver is being loaded on boot. The purpose of editing /etc/modules is to forcably load a module that is a bit lazy. 

I suspect either the WEP key or the ESSID is wrong. Here is a tutorial that may help:  [http://ubuntuforums.org/showthread.php?t=172810&page=2](http://ubuntuforums.org/showthread.php?t=172810&page=2) Please read all the way to the end, tetobear has some good stuff.

---

### Post by rustysail on 2007-04-14
I just did a clean install and I am going to start over with the wifi problem.
Here are the steps I have taken so far.

First I just checked how everything was configured automatically.
```
rusty@rusty-desktop:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"2WIRE971"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Next I put in my settings. It seemed like everything is configured except for the WEP key.
```
root@rusty-desktop:/home/rusty# iwconfig ath0 key 8305477154 restricted

```

I installed network-manager.
```
root@rusty-desktop:/home/rusty# apt-get install network-manager network-manager-gnome

```
After that was installed, I restarted the network and brought up nm-applet.  It didn't show any possible wireless connections.

I decided to try a static IP to see if it would work, so I changed my interfaces file. I have never had trouble with DHCP on windows and the other computers in my house use DHCP, but I have heard on various forums that this can fix some problems.
```
iface ath0 inet static
wireless-essid 2WIRE971
wireless-key 8305477154
wireless-channel 6
address 172.12.1.36
netmask 255.255.0.0
gateway 172.16.0.1
wireless-mode managed

```

When I tried nm-applet again I noticed an error output.
```
root@rusty-desktop:/home/rusty# nm-applet 

(nm-applet:10301): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


```
I searched that error on google, but nothing useful came up.

After reviewing tetobear's post as you suggested, I saw he ran "iwpriv ath0 authmode2."
I wasn't sure if my network was open or shared though and I couldn't tell by looking at the home portal (172.16.0.1).

As near I can tell this didn't do anything.  I am assuming that the "scan" he kept referring to was "iwlist ath0 scan."  If that was the case, my computer was already able to scan.

After all the iwconfig still looks essentially the same.
```
root@rusty-desktop:/home/rusty# iwconfig ath0
ath0      IEEE 802.11g  ESSID:"2WIRE971"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:8305-4771-54   Security mode:restricted
          Power Management:off
          Link Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

I'm not really sure where to go next.  I have a feeling that I misinterpreted some of the instructions.

---

### Post by chili555 on 2007-04-15
For NetworkManager to control your wireless interface, all the interfaces, except lo,  in /etc/network/interfaces need to be removed or commented out:```
#iface ath0 inet static
#wireless-essid 2WIRE971
#wireless-key 8305477154
#wireless-channel 6
#address 172.12.1.36
#netmask 255.255.0.0
#gateway 172.16.0.1
#wireless-mode managed
```Try it and see if NetworkManager allows you to connect.

Also, make sure all interfaces are *un-enabled* in System - Administration -Networking.

Let us know.

---

### Post by rustysail on 2007-04-15
Hey

it turns out that fiesty fawn aoutmatically supports the netgear wg311t, so I'm all set after installing it.

---

### Post by beorn! on 2007-04-15
thank you so much. This discussion was amazing.

---

