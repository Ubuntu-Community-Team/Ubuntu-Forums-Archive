---
title: "Unable to associate with OPEN/WEP networks after first connecting to a WPA network"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by kingweee on 2008-04-03
First of all, I uninstalled NetworkManager a few months ago because I was unsatisfied with its ability to simultaneously handle two wireless connections. 

To manage my wireless, I created various interfaces files and employed scripts that would copy them and restart networking when I wanted to switch connections. Unfortunately, whenever I activated a WPA connection I would be unable to go back to WEP or OPEN without first clearing my interfaces file and rebooting.

EG:

auto ath0
iface ath0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
wpa-psk keyhere
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Jamnet

If I restarted networking with the above in my 'interfaces' configuration file I would be forced to reboot with a blank file before I could associate with any OPEN or WEP APs.

EG:

auto ath0
iface ath0 inet static
address 192.168.1.225
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key keyhere
wireless-essid btw

or 

auto ath0
iface ath0 inet dhcp
wireless-essid opennet
wireless-key off

I would not be able to associate with the 'btw' or 'opennet' APs without a full reboot. I am aware that this problem is likely caused by WPA supplicant and whatever residual effect it leaves behind after I try to switch to an open or a WEP network. I have tried killing the wpa_supplicant process, but it does not solve the problem.

Basically what I am searching for is a command that will revert wpa_supplicant to a passive state; a state where it will not interfere with OPEN or WEP association. 

Recently I tried employing Wicd as my wireless manager to see if the problem would persist, and it does. If I use Wicd to connect to a WPA network, I must then reboot before I can associate with OPEN or WEP APs. I have since also tried to re-install NetworkManager, but for whatever reason it is now broken (roaming mode will not associate with any of the listed APs, although manual configuration works fine).

I couldn't care less about the problems with NetworkManager, using my own scripts is far more efficient and resource friendly. However, it is extremely annoying to have to reboot every time I want to connect to a WEP or OPEN AP after first connecting (or booting with WPA info in my interfaces file)  to a WPA network.

Thanks for your time,

kingweee

---

### Post by randomhuman on 2008-04-18
Have you tried just killing wpa_supplicant after switching the interface files, but before restarting networking?

wpa_supplicant can also manage open and wep networks. Your interfaces file would need to look something like:

auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -B -Dmadwifi -iath0 -P/var/run/wpa_supplicant.ath0.pid
post-down kill `cat /var/run/wpa_supplicant.ath0.pid`

...and you'd then need to create a wpa_supplicant.conf that specifies the details of all your networks. I'm not sure if you can specify static ips. man wpa_supplicant.conf doesn't say.

---

