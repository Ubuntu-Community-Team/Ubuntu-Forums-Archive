---
title: "essid and wep key won't stay on reboot. why?"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by akajonesy on 2007-01-11
ok, have a ZyDAS 802.11b/g USB2 WiFi adapter installed, using Ubuntu Edgy, and everything works absolutely great. Except I can't get the essid ID and wep key to stick.

I've entered the information in the networking interface, and it didn't work, so I tried what I did in a xubuntu install on an old laptop and manually entered the info using iwconfig eth1 essid "name" key xxxxxxxxxxxx
That works fine and I have full connectivity while I'm on.
However, I have to do that every time I boot up as it seems to loose the info on shutdown.
How do I fix this?

iwconfig reads this:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11g zd1211  ESSID:"Neptune"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:08:A9:AC   
          Bit Rate=11 Mb/s   
          Link Quality=93/100  Signal level=93/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

any help?

---

### Post by englert.james on 2007-01-12
I believe you have to edit some parameters so that ifup and ifdown work.   The file you will need to edit is /etc/network/interfaces. You may need to search for the ifup and ifdown tools for this to work. Google it because I'm not expert.

---

### Post by akajonesy on 2007-01-12
from what I can understand ifup ifdown are in case your signal gets dropped. Mine is fine. Its just not activating on boot up. 
Is there something not loading on boot?

---

### Post by akajonesy on 2007-01-13
anyone? This one is giving me kittens. I just don't know where to look for the info, since I just can't tell what it's doing.:(

---

### Post by Floppyjoe on 2007-01-13
You need to edit your /etc/network/interfaces file.

```
sudo gedit /etc/network/interfaces
```

make sure it has the correct parameters there.

for example this is in my interfaces file:
> iface eth0 inet dhcp

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
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf


I have Wpa encryption activated here but you may not so delete those lines.
Also make sure your essid is in there and the channel is set to your router channel.
Make sure you edit the interface that your computer is using for wireless here. In your case 
it would be eth1.

I hope this helps.

---

### Post by akajonesy on 2007-01-14
floppyjoe, 

that file seems to have the right info (here's the paste):

> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






iface eth1 inet dhcp
wireless-essid Neptune
wireless-key ************

auto eth1

I notice that my card is written in as "eth1" as opposed to "wlan" could this be the issue? Also, Ive not installed the drivers that came with the card, since it worked otherwise, felt it was unnecessary.

---

### Post by Floppyjoe on 2007-01-14
I think you need the "wireless-mode managed" line in there too.
And also the channel of the router you are connecting to.

ie. wireless-channel 7

It should look something like this:

> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





auto eth1
iface eth1 inet dhcp
wireless-essid Neptune
wireless-channel 8
wireless-mode managed
wireless-key ************


---

### Post by akajonesy on 2007-01-14
tried it. Same problem. 
When I shutdown and reboot, the settings go away.

---

### Post by akajonesy on 2007-01-16
anyone?

---

### Post by sgornick on 2007-01-22
What are you trying to say when you write: "settings go away"?

If you are trying to say that it appears that the settings from the /etc/network/interfaces config file are not getting read during boot, then perhaps there is still a problem with the settings in the config file.

I got burned once when using ASCII WEP key but not prefixing it with "s:" in the config file.  
e.g., for the WEP key "WORKWEPKEY", I had to use:
  wireless-key s:WORKWEPKEY 

I am including a link to a bug report that I filed (which has not yet been confirmed), which may provide additional information:
  [https://launchpad.net/ubuntu/+source/netbase/+bug/80499](https://launchpad.net/ubuntu/+source/netbase/+bug/80499)

---

### Post by akajonesy on 2007-01-24
I installed network-manager through synaptic (no idea what the difference between it and what comes preinstalled) but it seems to have done the trick. Things all work now. 
(Mind you I also installed the latest drivers for the adapter through synaptic at the same time, so couldve been that or a combination). 

Either way. All works very nice now.:)

---

