---
title: "Wireless connection (WPA) breaking constantly"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by lodp on 2006-10-23
I'm having trouble keeping my wireless connection up to my Asus WL-500g router.The connection breaks frequently, even when the Laptop stands right next to the router, so I doubt that signal strength is an issue. I'm using WPA-PSK encryption.

Sometimes it takes a couple of minutes to come back up again, sometimes though, it's only like 30 secs or so (is there some daemon involved in establishing connections?)

Sometimes I try entering

/etc/init.d/networking restart

but that doesn't seem to make any difference -- most of the time it just times out, saying it  receive any DHCPOFFERs.

this is my /etc/network/interfaces:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


auto eth1

iface eth1 inet dhcp

   pre-up /sbin/wpa_supplicant -D wext -i eth1 -c /etc/wpa_supplicant.conf -Bw; sleep 8;
   post-down killall -q wpa_supplicant
```

this is my /etc/wpa_supplicant.conf

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=2
network={
      ssid="<here's my ssid>"
      scan_ssid=1
      proto=WPA
      key_mgmt=WPA-PSK
      pairwise=TKIP
      group=TKIP CCMP
      psk=<here's my key>
}
```

are there any wireless tools that can deal with WPA (i.e. show signal strength, make connections)? I tried wifi-radar and knetworkmanager, without much success. wifi-radar shows wireless networks with signal strength, but it can't establish connections or disconnect (nothing happens when I hit a button). knetworkmanager doesn't recognize any interfaces or wireless networks. So I'm stuck to the command line

I would appreciate any comments..

---

### Post by wieman01 on 2006-10-23
Wifi-Radar or NetworkManager are probably the tools that work. I have used both of them before, but I prefer a manual setup. 

Coming back to your problem, this very much sounds like a router issue. I used to have the same problem, timeouts after a few minutes or up to an hour after booting. Then nothing, restarting the network would fail.

The solution was to play around with the router's settings. One setting did the trick for me: **"beacon interval"** (Linksys WRT54G). Not sure if your router has such a setting, but I had to change it from the default value of **100** to **10**. The network has been stable since.

I recommend that you do the same and try different settings. Timeouts usually point to a problem with the network setup rather than Ubuntu itself... This is as far as I can tell.

---

### Post by squibT on 2006-10-23
You really should be looking at interferance from other networks...hidden and broadcasting ssid...try Network Stumbler for starters to see if there are any other ssids on the same channel...switch channels around if you are impatient...beacon can be set at 10 or more realistically 50. You may have to go to dd-wrt or thibor for that capability...not sure your router  is supported by these firmwares but give the forums a try...

---

### Post by wieman01 on 2006-10-24
> **squibT said:**
> You really should be looking at interferance from other networks...hidden and broadcasting ssid...try Network Stumbler for starters to see if there are any other ssids on the same channel...switch channels around if you are impatient...beacon can be set at 10 or more realistically 50. You may have to go to dd-wrt or thibor for that capability...not sure your router  is supported by these firmwares but give the forums a try...
The term "realistic" is relative. I agree with your that a frequency of 10 Milliseconds sounds somewhat odd & a bit of an overkill, but I tried all values closer to 50 but 10 was what eventually resulted in a stable network. Believe or not.

---

### Post by lodp on 2006-10-25
thanks very much for those tips -- i just set beacon interval to 50 and go towards 10 if it doesn't work out.

there IS another network that i receive here, but i couldn't find out which channel it's on. network stumbler is a windows tool, right? maybe i'll just try and switch my own channel randomly.

---

### Post by wieman01 on 2006-10-25
> **lodp said:**
> thanks very much for those tips -- i just set beacon interval to 50 and go towards 10 if it doesn't work out.

there IS another network that i receive here, but i couldn't find out which channel it's on. network stumbler is a windows tool, right? maybe i'll just try and switch my own channel randomly.
I don't think it has to do with interference. There are network all around my place & this did not seem to be much of a problem.

---

### Post by lodp on 2006-10-25
i just booted to windows and tried network stumbler. there are 3 networks additional to mine, and they're all on channel 11. i've got mine set to channel 7 now (network stumbler says: channel 7+), but that seems to have worsened the situation still. connection is breaking like every 15 min now. does it make any difference, what channel i take (apart from other networks possibly interfering)?

i played around with the beacon interval too. i tried 50, 30, and 10, out of which 10 seems to work worst and 50 best (though still not any better than 100, as far as i can tell).

thanks for your support, guys..

---

### Post by squibT on 2006-10-25
Beacon interval is no fix....its a patch....you have issues you need to track down. You need to find out if you have some sort of interferance messing you up....wireless APs on same channel, micorwave, cordless phones...maybe your NIC is messed up. Your country has wireless channels you can use...in Canada it is 1, 6, 11. Check yours and put your AP on 1 if others are on 11. If that does not work look at the other sources of interferance...

When your wirleless goes down, go to your router and patch in your laptop to see if the router is working at all...if it is working when you are hard wired there is something else going on....

---

### Post by lodp on 2006-10-30
many thanks -- switching to channel 1 (from originally 11, and then 7, which i had picked at random) seems to have done the trick. connection has been working fine now for several hours. i hope it'll stay that way...

EDIT: channel 1 didn't work so fine after all -- streaming audio on to the router had very skippy results. old lady upstairs has got a cordless phone (i even helped her install the damn thing! curse you, altruism!). i read up on it on wikipedia -- the wireless channels suggested for europe are 1,7, and 13. 1 sorta worked, 13 didn't work at all, but right now channel 7 seems to work out very well.

thanks everyone!

---

