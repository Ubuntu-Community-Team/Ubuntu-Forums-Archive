---
title: "Setting up a wireless connection using WPA2"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by pieter5 on 2014-09-07
Hi,

To start off with, I'm really new to using linux so, if possible, be descriptive in your responses. I really want to learn but don't have a big knowledge-base on the subject. I'm sorry if I missed to provide some information that I should have to be able to get decent feedback, I'm really trying ^_^

I'm trying to setup a home server for git/atlassian/DLNA streaming/torrenting/... usage and want to use the Ubuntu 14.04 server.
I've installed the server and am currently trying to connect it to my wireless network, this is the first thing I'm trying and I'm already failing horribly..

The first thing I tried was checking if I could actually find my wireless network:

sudo iwlist wlan0 scan 
```
wlan0 No scan results
```

I then tried to configure my networking file and based it on the information I got from my windows laptop wireless configuration (only necessary stuff inclided) :
```
  Standaardgateway. . . . . . . . . : fe80::5e35:3bff:fe20:930a%11
                                      192.168.0.1
  DHCP-server . . . . . . . . . . . : 192.168.0.1


  DNS-servers . . . . . . . . . . . : 2a02:1800:100::42:2
                                      2a02:1800:100::42:1
                                      195.130.131.130
                                      195.130.130.2
  Zoeklijst voor verbindingsspec. DNS-achtervoegsels :
                                      telenet.be

```
So I used 

sudo nano /etc/network/interfaces to setup the file as:
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.0.1 (also tried 192.168.1.1)
wpa-ssid myssid
wpa-psk mypassword
dns-nameservers 195.130.131.130 195.130.130.2 (from the windows config)
```

Then making the machine use the new settings:
sudo ifdown wlan0 && sudo ifup -v wlan0
I get:
```

... 
wpa_supplicant: configuring network blaock -- 0
wpa_supplicant:  wpa-ssid "myssid" -- OK
wpa_supplicant: wpa-pask *** -- OK
wpa_supplicant: enabling network block 0 -- OK
ip addr add 192.168.1.150/255.255.255.0 broadcast 192.168.1.255  dev wlan0 label wlan0

RTNETLINK answers: File exists
Failed to bring up wlan0

```

hope you guys can help me!

---

### Post by varunendra on 2014-09-11
First of all, Welcome to the forums pieter5 ! :)

I am not really a server guy, nor do I have in-depth knowledge about the ways of IPv6 (which seems to be in use on your network), but I may be able to verify if there is some trouble on the driver part.

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Since you are already aware of how to use nano, I hope you also already know how to deal with a script if you needed to run it manually (hint: don't use "sh wireless_script" as it is incompatible with 'sh'. Instead, run it with "./wireless_script" or "bash wireless_script"). Let me know if you need detailed help with running the script or posting its report back here.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

