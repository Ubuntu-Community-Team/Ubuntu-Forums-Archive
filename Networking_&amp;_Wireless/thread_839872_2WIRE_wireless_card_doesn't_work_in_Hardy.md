---
title: "2WIRE wireless card doesn't work in Hardy"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by Forcestar on 2008-06-24
I just picked up a Thinkpad R40 off Ebay. Due to the fact that it does not contain a wireless card, I pulled my trusty 2WIRE card off the shelf and stuck it in. After spending over 2 hours wrangling with it, I've been unable to get the darn thing to work. Iwconfig is as follows:

> nathan@Wyvern:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"2WIRE977"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by chili555 on 2008-06-25
Is your 2WIRE router still set up with the default settings, 64-bit WEP with the key being the 10-digit number on the bottom of the router? You should be able to click the Network Manager icon, select your network, 2WIRE977, drop down 64-bit WEP, put in those 10 digits, leave the authentication method as 'Open,' and connect.

I think a lot of people try to select 'WEP Passphrase' and fail. Passphrase, whatever it's supposed to be, never has worked for me.

---

### Post by Forcestar on 2008-06-25
> **chili555 said:**
> Is your 2WIRE router still set up with the default settings, 64-bit WEP with the key being the 10-digit number on the bottom of the router? You should be able to click the Network Manager icon, select your network, 2WIRE977, drop down 64-bit WEP, put in those 10 digits, leave the authentication method as 'Open,' and connect.

I think a lot of people try to select 'WEP Passphrase' and fail. Passphrase, whatever it's supposed to be, never has worked for me.

The problem is that it doesn't come up with the network at all. I entered it manually (System>Administration>Network>wlan0properties). I've got the correct network name, and the correct key (tested that with my father's laptop), it just doesn't seem to pick up the network despite the fact that the router is sitting 10 feet away :P

---

### Post by Forcestar on 2008-06-25
Anyone around to help?

---

### Post by chili555 on 2008-06-25
Let's have a look at ```
sudo iwlist wlan0 scan
sudo lshw -C network
```Thanks.

---

### Post by Forcestar on 2008-06-25
Scan:

> 
nathan@Wyvern:~$ sudo iwlist wlan0 scan
[sudo] password for nathan: 
wlan0     Scan completed :
          Cell 01 - Address: 00:0D:72:B9:75:51
                    ESSID:"2WIRE977"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level=-118 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002b8fd35ec9



Lshw: 

> 
nathan@Wyvern:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:06:1b:e3:b1:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.79 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:60:b3:1b:8a:91
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=prism54pci latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11g
nathan@Wyvern:~$ 



---

### Post by Forcestar on 2008-06-25
Bump.

---

### Post by chili555 on 2008-06-25
Are you trying to get it to work with your wired ethernet connected? Network Manager doesn't like that.> ip=192.168.1.79 latency=66 link=yes [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager) Especially see this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managedYour scan and lshw look very healthy. Please detach the wire and see if wireless springs to life.

---

### Post by Forcestar on 2008-06-26
After some kicking around with the network manager, I *finally* got it working with some restarts. Thank you, Chili!

---

