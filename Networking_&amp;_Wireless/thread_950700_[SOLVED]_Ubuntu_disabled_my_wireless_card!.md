---
title: "[SOLVED] Ubuntu disabled my wireless card!?"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by computer_freak_8 on 2008-10-17
Okay, here's what has happened. When I first installed the operating system, I left my ppp, eth0 and ath0 on roaming (after making sure the wireless worked). I didn't need to use them; I connect (to the Internet) via a Sprint card. 

Yesterday, I decided to setup my box as a Wi-Fi hotspot. Well, now, the network manager does not show device "ath0" (my wireless). 

I tried setting it in /etc/network/interfaces: failed.

I tried seeing the status via System, Administration, Hardware Drivers: No devices listed (failed).

However, when I run "lspci", I get an entry that looks promising:
[FONT="Courier New"]05:0a.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
[/FONT]
I tried modprobe commands, but I'm too much of a newbie. I don't know what syntax and/or module I want.

The programs iwconfig/ifconfig do not show it at all.


Any ideas for me to try?

Thanks in advance,
computer_freak_8

---

### Post by computer_freak_8 on 2008-10-18
Okay, I played around with MadWifi and "sudo modprobe ath_pci" and got it working - in a way.

Now, whenever I issue the command "sudo /etc/init.d/networking restart", my whole system locks up about five seconds after executing with three or four errors. Then I have to do a hard reset.

Here is the latest version of my "/etc/network/interfaces" file that caused a lockup:```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual




auto ppp0
iface ppp0 inet manual


auto ath0

iface ath0 inet manual
#	pre-up modprobe ath_pci
	pre-up wlanconfig ath0 destroy
        pre-up wlanconfig ath0 create wlandev wifi0 wlanmode master
#       post-down wlanconfig ath0 destroy
        wireless-mode master
        wireless-channel 7
        wireless-essid UnsecuredByJBatWH
        address 221.112.5.150
        gateway 192.168.0.1
        netmask 255.255.255.0

#iface br0 inet manual
#        bridge_ports ppp0 ath0

iface br0 inet manual
	bridge_ports ppp0 ath0
#	pre-up ifconfig ppp0 0.0.0.0 up
#	pre-up ifconfig ath0 0.0.0.0 up
#	pre-up iwconfig ath0 mode master
	pre-up brctl addbr br0
	pre-up brctl addif ppp0
	pre-up brctl addif ath0
#	post-down ifconfig ppp0 0.0.0.0 down
#	post-down ifconfig ath0 0.0.0.0 down
#	post-down brctl delif br0 ppp0
#	post-down brctl delif br0 ath0
#	post-down brctl delbr br0

```

Note: All of the errors are about the "ath0" device.

Now I'm going to try:```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual




auto ppp0
iface ppp0 inet manual


auto ath0

iface ath0 inet manual
        wireless-mode master
        wireless-channel 7
        wireless-essid UnsecuredByJBatWH
        address 221.112.5.150
        gateway 192.168.0.1
        netmask 255.255.255.0

#iface br0 inet manual
#        bridge_ports ppp0 ath0

iface br0 inet manual
	bridge_ports ppp0 ath0
#	pre-up ifconfig ppp0 0.0.0.0 up
#	pre-up ifconfig ath0 0.0.0.0 up
#	pre-up iwconfig ath0 mode master
	pre-up brctl addbr br0
	pre-up brctl addif ppp0
	pre-up brctl addif ath0
#	post-down ifconfig ppp0 0.0.0.0 down
#	post-down ifconfig ath0 0.0.0.0 down
#	post-down brctl delif br0 ppp0
#	post-down brctl delif br0 ath0
#	post-down brctl delbr br0

```

---

### Post by iponeverything on 2008-10-18
> **computer_freak_8 said:**
> Okay, I played around with MadWifi and "sudo modprobe ath_pci" and got it working - in a way.

Now, whenever I issue the command "sudo /etc/init.d/networking restart", my whole system locks up about five seconds after executing with three or four errors. Then I have to do a hard reset.

Here is the latest version of my "/etc/network/interfaces" file that caused a lockup:```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual




auto ppp0
iface ppp0 inet manual


auto ath0

iface ath0 inet manual
#	pre-up modprobe ath_pci
	pre-up wlanconfig ath0 destroy
        pre-up wlanconfig ath0 create wlandev wifi0 wlanmode master
#       post-down wlanconfig ath0 destroy
        wireless-mode master
        wireless-channel 7
        wireless-essid UnsecuredByJBatWH
        address 221.112.5.150
        gateway 192.168.0.1
        netmask 255.255.255.0

#iface br0 inet manual
#        bridge_ports ppp0 ath0

iface br0 inet manual
	bridge_ports ppp0 ath0
#	pre-up ifconfig ppp0 0.0.0.0 up
#	pre-up ifconfig ath0 0.0.0.0 up
#	pre-up iwconfig ath0 mode master
	pre-up brctl addbr br0
	pre-up brctl addif ppp0
	pre-up brctl addif ath0
#	post-down ifconfig ppp0 0.0.0.0 down
#	post-down ifconfig ath0 0.0.0.0 down
#	post-down brctl delif br0 ppp0
#	post-down brctl delif br0 ath0
#	post-down brctl delbr br0

```

Note: All of the errors are about the "ath0" device.

Now I'm going to try:```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual




auto ppp0
iface ppp0 inet manual


auto ath0

iface ath0 inet manual
        wireless-mode master
        wireless-channel 7
        wireless-essid UnsecuredByJBatWH
        address 221.112.5.150
        gateway 192.168.0.1
        netmask 255.255.255.0

#iface br0 inet manual
#        bridge_ports ppp0 ath0

iface br0 inet manual
	bridge_ports ppp0 ath0
#	pre-up ifconfig ppp0 0.0.0.0 up
#	pre-up ifconfig ath0 0.0.0.0 up
#	pre-up iwconfig ath0 mode master
	pre-up brctl addbr br0
	pre-up brctl addif ppp0
	pre-up brctl addif ath0
#	post-down ifconfig ppp0 0.0.0.0 down
#	post-down ifconfig ath0 0.0.0.0 down
#	post-down brctl delif br0 ppp0
#	post-down brctl delif br0 ath0
#	post-down brctl delbr br0

```

I assume that the 192.168.0.0 segment is available on another one of your interfaces. 

/etc/modprobe.d/options -- add this:

```
options ath_pci autocreate=ap

```
/etc/network/interfaces :

```
iface ath0 inet static
        wireless-essid UnsecuredByJBatWH
        address 221.112.5.150
        gateway 192.168.0.1
        netmask 255.255.255.0
        post-up /etc/tkip

auto ath0

```

/etc/tkip :

```
#!/bin/sh
iwconfig ath0 essid UnsecuredByJBatWH
iwpriv ath0 mode 3
ifconfig ath0 221.112.5.150 up
hostapd -B /etc/hostapd.conf

```

/etc/hostapd.conf :

```
interface=ath0
driver=madwifi
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
debug=0
dump_file=/tmp/hostapd.dump
ssid=UnsecuredByJBatWH
eapol_key_index_workaround=0
wpa=1
wpa_passphrase=just a passphrase for anyone to have a crack at 
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP

```

---

### Post by iponeverything on 2008-10-18
Its easy enough for you to modify the the above to be open. Unless you like to have people parked outside your house surfing on your network, I would not recommend it.

> 
Yesterday, I decided to setup my box as a Wi-Fi hotspot. Well, now, the network manager does not show device "ath0" (my wireless).


network manager will ignore any interfaces configured via the /etc/network/interfaces file.

I am curious about the IP that you chose for ath0 interface. You are aware that that in order to surf via your hotspot, clients will need to be configured with 221.112.5.0/24 addresses. And unless you're doing masq for them (using an IP address range that is assigned to someone else and masq'ing will cause some rather subtle issues), your upstream is going to have a route for you in order for them to work. If this is not your intention, modify the above to use an RFC-1918 complaint private address and spend about 15 minutes setting up a dhcp server to hand them out.  Setup a simple iptables rule to mask you private segment and turn on IP forward. 

If the 221.112.5 address is that of your sprint card and your machine already has that default route don't have it in the iface section of ath0.

Make your ath0 192.168.0.1/24 and hand out addresses in that range.

---

### Post by computer_freak_8 on 2008-10-18
Okay, since the last time I was here, I got two responses. (Thanks, iponeverything!) During that same time, I installed madwifi from source, and with some fiddling, got a working wifi hotspot... for a while.

About this:
> **iponeverything said:**
> I am curious about the IP that you chose for ath0 interface. You are aware that that in order to surf via your hotspot, clients will need to be configured with 221.112.5.0/24 addresses.
Yes, I have (had?) a DHCP server that worked just fine, my other client and I were both able to successfully connect to the Internet on our laptops. I had somehow gotten the ath0 device into "Master" mode, then installed Firestarter and did the routing. 

Now, here's what I've discovered: After I destroy the VAP (sudo wlanconfig ath0 destroy), the computer locks up completely upon issuing "sudo wlanconfig ath0 create wlandev wifi0 wlanmode ap". Note that it re-creates fine if I leave off the "wlanmode ap" part. (Well, "fine" except for the fact that it is not in master mode...) Also, when I say "locks up completely", I mean there is a pause of 5-10 seconds, then the screen freezes (mouse/terminal cursor in stop moving/blinking, respectively), and no matter what I try, it won't respond. I have to do a hard reset. I tried all of the following: [Ctrl]+[Alt]+[Delete], [Ctrl]+[Alt]+[F#] (one of the f-keys on the top row of the keyboard), [Caps Lock], [Num Lock], [Esc]; none of them do anything - the caps/num lock keys don't even toggle the corresponding lights on the keyboard.

So I figured that maybe I had to change what my commands were before that deadly command. But I can't figure it out. Whether "sudo ifconfig ath0 up" or "sudo ifconfig ath0 down", whether "sudo modprobe ath_pci" or not, I can't get the result to change. 

I'm now going to try what you have recommended.

---

### Post by computer_freak_8 on 2008-10-18
Actually, after looking at what you gave me, I was able to come up with what I needed. Also, this way, I can turn off the Access Point when I want to by issuing "sudo killall hostapd" and bring it back with "sudo hostapd -B /etc/hostap.conf"

Here is my new (working... I think) "/etc/network/interfaces" file:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual




auto ppp0
iface ppp0 inet manual
	pre-up iptables-restore < /etc/iptables


auto ath0

iface ath0 inet manual

	pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
        wireless-mode master
        wireless-channel 7
        wireless-essid UnsecuredByJBatWH
        address 221.112.5.150
        gateway 127.0.0.1
        netmask 255.255.255.0

#iface br0 inet manual
#        bridge_ports ppp0 ath0

iface br0 inet manual
	bridge_ports ppp0 ath0
	pre-up ifconfig ppp0 0.0.0.0 up
	pre-up ifconfig ath0 0.0.0.0 up
	pre-up iwconfig ath0 mode master
	pre-up brctl addbr br0
	pre-up brctl addif ppp0
	pre-up brctl addif ath0
	post-down ifconfig ppp0 0.0.0.0 down
	post-down ifconfig ath0 0.0.0.0 down
	post-down brctl delif br0 ppp0
	post-down brctl delif br0 ath0
	post-down brctl delbr br0

```


I ran "sudo /etc/init.d/networking restart" and then "iwconfig", which shows: ```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ppp0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"UnsecuredByJBatWH"  Nickname:""
          **Mode:Master**  Frequency:2.412 GHz  Access Point: 00:14:A5:CB:45:44   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-91 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Note the bold part.

But now, Firestarter will not start. It hangs for about 5 minutes, then gives a window with the title of something like (can't remember for sure; I just closed it) "Firestarter: firewall failed to start".

---

### Post by iponeverything on 2008-10-19
```
iface ath0 inet manual

	pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
        wireless-mode master
        wireless-channel 7
        wireless-essid UnsecuredByJBatWH
        address 221.112.5.150
        gateway 127.0.0.1
        netmask 255.255.255.0

```

Goodness.. gateway 127.0.0.1 ? -- Maybe I missing something here -- why do you have the gateway set to use loopback? The gateway is not mandatory in all the stanza's, just remove it altogether from your ath0 stanza. This could be the reason why firestarter hangs on you.

---

### Post by computer_freak_8 on 2008-10-19
> **iponeverything said:**
> Goodness.. gateway 127.0.0.1 ? -- Maybe I missing something here -- why do you have the gateway set to use loopback? The gateway is not mandatory in all the stanza's, just remove it altogether from your ath0 stanza. This could be the reason why firestarter hangs on you.


No, you didn't miss anything - I just remembered you pointing out that the 182.168.x.x address would need to be another one of my interfaces, which it is not, so I figured loopback would work, since the one that it *would* be is dynamic. I will do as you have suggested and remove it; I thought it had to be there for some reason. 


Thanks for the tip,
computer_freak_8

---

### Post by iponeverything on 2008-10-20
> **computer_freak_8 said:**
> No, you didn't miss anything - I just remembered you pointing out that the 182.168.x.x address would need to be another one of my interfaces, which it is not, so I figured loopback would work, since the one that it *would* be is dynamic. I will do as you have suggested and remove it; I thought it had to be there for some reason. 


Thanks for the tip,
computer_freak_8

Dynamic is fine. I would make your AP (ath0) have an address 192.168.0.1/24 and have
your dhcp server hand out something 192.168.0.20 - 192.168.0.50 -- with a default gw of 192.168.0.1 (itself) to the clients.

All of the IP routes on your box are available to traffic from any of your interfaces as long you are not prohibiting it.

---

### Post by computer_freak_8 on 2008-10-22
> **iponeverything said:**
> Dynamic is fine. I would make your AP (ath0) have an address 192.168.0.1/24 and have
your dhcp server hand out something 192.168.0.20 - 192.168.0.50 -- with a default gw of 192.168.0.1 (itself) to the clients.

All of the IP routes on your box are available to traffic from any of your interfaces as long you are not prohibiting it.

Okay. I got it working, and actually just used IPTABLES directly after uninstalling Firestarter. I want to have the IP addresses in the 221.112.5.x, 150<x<200 range, mainly just to be unique. It is working fine. I'm surprised, actually, because my Sprint card does not provide much bandwidth, but none of the users (myself plus two clients) have noticed much lag with the Internet. 

I plan to remember that thing about the IP routes being available on any/all interfaces, provided I don't prohibit it.


Thanks again for all your help,
computer_freak_8

---

### Post by kennedy7 on 2008-11-01
you could have done it like this. First to get it working again you need to go to "applications; accessories, Terminal. Once you get to the terminal type "modprobe ath_pci"
no quotes. Then your card should work. Then in the terminal type "sudo nano /etc/rc.local" again no quotes. then right before the line "exit o" type
"modprobe ath_pci". That make your wireless card drivers autoload at startup. If you have any trouble just tell me.

---

