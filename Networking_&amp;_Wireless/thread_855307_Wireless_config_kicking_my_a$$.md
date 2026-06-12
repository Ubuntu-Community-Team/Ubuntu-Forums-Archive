---
title: "Wireless config kicking my a$$"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by attercop on 2008-07-10
I've been Googling all the how-to's and following as many forum stickies as i can lay my hands on but i'm getting really mixed results. Sometimes my wireless network shows, sometimes not, and when it does show i can't connect.

I'm using a cheap Plexus USB wireless adapter. Fully compliant with IEEE802.11g, IEEE802.11b standard, and support 64/128 bits WEP encryption, WPA-PSK, WPA2 encryption and security protocol etc. Have a Belkin Wireless-G router updated to the latest firmware. ESSID is broadcasting. Using WPA/WPA2, TKIP/AES encryption and a pre-shared key.

```
lshw -C network
```

Shows my wireless adapter fine, with the ndiswrapper driver i installed from the CDs .inf driver file.

```
iwconfig
```

Shows my wireless adapter working on wlan0.

```
iwlist scan
```

Shows my wireless network just fine.

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid MYESSID
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk MYHUGEHEXKEYTHING
```

This is my /etc/network/interfaces file.

I've checked these:
1. Ethernet cable is unplugged.
2. No firewall & configuration tool is running (not that i'm aware of).
3. MAC filtering is disabled.
4. NetworkManager, Wifi-Radar & similar wireless configuration tools are disabled/turned off and not in use (as far as i'm aware yes, i did sudo killall NetworkManager).

Have i missed something? Help!

---

### Post by forger on 2008-07-10
try with ndiswrapper and your windows .inf driver file:
> sudo apt-get install ndisgtk

then head to System > administration > Windows wireless drivers

---

### Post by attercop on 2008-07-10
Yep i've done that and it's not working yet. I rebooted the router and it's finding it ok now but won't connect.

---

### Post by forger on 2008-07-10
try setting it up with rutilt:
sudo apt-get install rutilt
Then head to System > administration > rutilt

---

### Post by attercop on 2008-07-10
That seems good but only supports WEP. I use WPA/WPA2.

---

### Post by kevdog on 2008-07-10
Sorry, but just had to ask -- the wireless config is kicking your money?  Is your livelihood dependent on your wireless being configured correctly??

FYI - do a search for rt73 written by deprius.  I believe its in the networking section in the forum archive!!

---

### Post by attercop on 2008-07-14
> **kevdog said:**
> Sorry, but just had to ask -- the wireless config is kicking your money?  Is your livelihood dependent on your wireless being configured correctly??

FYI - do a search for rt73 written by deprius.  I believe its in the networking section in the forum archive!!
Very funny! I did a search and found that script you recommended, but unfortunately it couldn't do it so i'm still on a network cable. I think i should probably just accept that for the time being this hardware won't work. So, i was recommended this new alternative cheap crap USB wireless receiver!

[http://www.aria.co.uk/Products/Peripherals/Network+Products/Wireless/Adapter+-+USB/Safecom+54Mbps+Wireless+Multimedia+?productId=21422]("http://www.aria.co.uk/Products/Peripherals/Network+Products/Wireless/Adapter+-+USB/Safecom+54Mbps+Wireless+Multimedia+?productId=21422")

---

### Post by kevdog on 2008-07-14
What part wasn't working for you?

---

### Post by nickdbliss on 2008-07-14
Before disabling network manager and others, were u able to see your network with iwlist scan?

---

### Post by attercop on 2008-07-14
> What part wasn't working for you?
I followed the on screen instructions and it still couldn't connect.

> Before disabling network manager and others, were u able to see your network with iwlist scan?
Yes i can see my network no problem. It even used to appear in the Network Manager with the connection strength occasionally. But since i followed the how-to sticky it doesn't do that.

---

### Post by attercop on 2008-07-23
No ideas? I hate admitting defeat on these things.

---

### Post by nickdbliss on 2008-07-24
> **attercop said:**
> No ideas? I hate admitting defeat on these things.

I am sorry it is still not solved. Too many troubleshooting methods and terminal commands sometimes messed up ur system instead of improving it. In my case i wasnt able to use WPA-PSK, network manager was asking password again n again. I searched n found i need to config wpa_supplicant.conf etc. 
I didnt do it, instead i uninstall my network manager ,after system update i did a reinstallation. After that in the interfaces file i commented out everything except auto lo. Then i checked if wpa_supplicant is installed.
Instead of ASCII i entered hex equivalent of my password when network manager once again asked me. Happily using wpa with my wireless connection every since. No problem whatsoever. Maybe i got lucky lol. I try to suggest people to do it before messing with any settings. But they never listen nor care so do i. Cheers

---

