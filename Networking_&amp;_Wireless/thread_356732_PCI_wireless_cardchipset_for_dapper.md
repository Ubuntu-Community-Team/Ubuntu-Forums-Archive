---
title: "PCI wireless card/chipset for dapper"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by tomane on 2007-02-08
Hello everyone,

I couldn't find this info anywhere so I hope that I can get some hints here.
I'm looking for a PCI wireless adapter for one PC running dapper.
Here are a few candidates that I found, can someone point which is most likely to *just* run on a PC with dapper?
 * Gigabyte GN-WP01GS
 * Sitecom WL-171
 * Asus WL-138G V2
 * Edimax EW-7128G
**<update> * NETGEAR WPN311 <-- went with this one and it was really easy to set up with wpa2 </update>**
Thanks in advance :)
cheers,
--to

---

### Post by Floppyjoe on 2007-02-08
I could not find any of those you listed on this page of supported interfaces:

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

I did find this info about ndiswrapper for ASUS card mentioned:
> 
Card: Asus WL-138G, 54mbps

    * Chipset: Marvell W8300
    * pciid: 11ab:1fa6 (rev 07)>
    * Driver: CDROM, ASUS [33]
    * Works with amd64 and 64 bits driver taken here: [ftp://dlsvr01.asus.com/pub/ASUS/lan/wifi-g/WIFI_V2712_64bit.zip](ftp://dlsvr01.asus.com/pub/ASUS/lan/wifi-g/WIFI_V2712_64bit.zip)
    * Other: Works well with Ndiswrapper 1.0 and CDROM WinXP driver on Gentoo with Kernel 2.6.11. ASUS Downloaded driver fails.; Problems with new driver versions and ndiswrapper 1.x (System Freeze), but the driver on CD mrv8k51 (ASUS,12/24/2003,2.2.0.20) works fine with ndiswrapper 1.5 (1.6rc2 is more stable) on linux 2.6.14.2 and 16kstacks (I will test if it works without the 16k patch). Works better with win98 driver for the card D-Link DWL-G510 [ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip](ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip) (manual directory).
    * Other: Ubuntu Dapper comes with a native, but not working Marvell driver [34]. To use ndiswrapper, you must prevent it from loading at boot, e.g. by removing the mrv8k.ko file from /lib/modules/...kernel.... The DLink Win98 driver works, but I see a few system freezes. Using the newer, downloaded Asus Win98 driver (after renaming mrv8ka50.sys to mrv8ka51.sys) the system often hangs at boot, but is more stable afterwards. With both drivers, booting is slow.
    * Other: The above versions causes kernel freeze/panic on Ubuntu Edgy (Ndiswrapper module version 1.22, Kernel: 2.6.17-10-generic). A workaround is yet to be found...
    * Other: The 64-bit driver mentioned above - which doesn't work with winxp sp2 on my box :) - works well on my 32-bit athlon and seems to be the only driver allowing WPA2 connection. (kernel: 2.6.19-gentoo-r4, ndiswrapper-1.34, wpa_supplicant-0.5.7) 
From the following URL:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A)

Also from the same source for Ndiswrapper compatibility:
> 
Card: Edimax EW-7128g

    * Chipset: RaLink? RT2500
    * pciid: 1814:0201 (rev 1)
    * Driver: Ndiswrapper 0.11; .inf and .sys for Win2K from [ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip)
    * Other: Slackware 10.0. Hint: modify /etc/rc.d/rc.inet1 and replace instances of "eth" with "wlan"; also modify /etc/rc.d/rc.modules to load ndiswrapper. Running flawlessly for one day so far. Using WEP.

---

### Post by tomane on 2007-02-10
I found a NETGEAR WPN311 card on a store and it happens that the card is natively supported using the madwifi driver. I have already installed it and it is running like a charm :)
From what I've read, the card handles WPA well so I'll give it a shot and see how it goes.

cheers,
--to

---

### Post by ubuntu_demon on 2007-02-22
> **tomane said:**
> I found a NETGEAR WPN311 card on a store and it happens that the card is natively supported using the madwifi driver. I have already installed it and it is running like a charm :)


Congrats :)

> **tomane said:**
> 
From what I've read, the card handles WPA well so I'll give it a shot and see how it goes.

cheers,
--to

WPA is a bit hard to setup. If you decide to do this then here's a guide :
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

I'm very interested in your experiences. I hope you get WPA2 personal running with CCMP/AES. I'm searching for a wireless card myself see :
[http://www.ubuntuforums.org/showthread.php?t=363633](http://www.ubuntuforums.org/showthread.php?t=363633)

The netgear WPN311 is one of the candidates

---

### Post by tomane on 2007-02-22
> **ubuntu_demon said:**
> Congrats :)
WPA is a bit hard to setup. If you decide to do this then here's a guide :
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

Well, I actually found it quite easy thanks to that guide :). Just after my previous post, I found that guide and I managed to set up WPA quite easily, so I definatelly recomend this card.

There's one thing, though, I'm using *edgy* instead of dapper because I had read that the madwifi drivers included in dapper were a bit old and IIRC I had to download a couple of stuff and build from source, which I wasn't very into at the time... With edgy it *plain just* works, which is as it should be for everyone, and now my server boots in a couple of seconds (wow! :-) ).

As for the kind of encryption used, I really can't tell *exactly* which one, but I believe it's WPA2, at least that's what network manager on my laptop shows when I connect to the wlan.
If I remember correctly, I had the router (SMC barricade) configured with <edit>TKIP+AES ***ahem... WPA/WPA2 mixed mode, I mean***</edit>, but from your thread it seems that plain AES is even better. This is my wpa_supplicant.conf:
```
network={
        ssid="this-is-not-my-ssid"
        #psk="thisisnotmypskaswell"
        psk=yadayadayadainhexadecimal
}

```this is my section related to ath0 in /etc/network/interfaces:
```
auto ath0
iface ath0 inet static
address 231.132.231.132
netmask 255.255.255.0
gateway 123.123.123.123
wireless-essid "this-is-not-my-ssid-duh:-)"
wpa-driver madwifi
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```Your thread mentions the model WG311, but note that my card is the WPN311. I believe that it doesn't to much difference at all so the NETGEAR card has my vote. It costed around €35-€39 in Portugal.

I'll take another look at that guide and make sure that I'm using the best encryption scheme, and make the necessary changes in the network configuration. I'll keep you posted regarding how it goes.


cheers,
--to

---

### Post by ubuntu_demon on 2007-02-22
> **tomane said:**
> Well, I actually found it quite easy thanks to that guide :). Just after my previous post, I found that guide and I managed to set up WPA quite easily, so I definatelly recomend this card.

There's one thing, though, I'm using *edgy* instead of dapper because I had read that the madwifi drivers included in dapper were a bit old and IIRC I had to download a couple of stuff and build from source, which I wasn't very into at the time... With edgy it *plain just* works, which is as it should be for everyone, and now my server boots in a couple of seconds (wow! :-) ).

As for the kind of encryption used, I really can't tell *exactly* which one, but I believe it's WPA2, at least that's what network manager on my laptop shows when I connect to the wlan.
If I remember correctly, I had the router (SMC barricade) configured with TKIP+AES, but from your thread it seems that plain AES is even better. This is my wpa_supplicant.conf:
```
network={
        ssid="this-is-not-my-ssid"
        #psk="thisisnotmypskaswell"
        psk=yadayadayadainhexadecimal
}

```this is my section related to ath0 in /etc/network/interfaces:
```
auto ath0
iface ath0 inet static
address 231.132.231.132
netmask 255.255.255.0
gateway 123.123.123.123
wireless-essid "this-is-not-my-ssid-duh:-)"
wpa-driver madwifi
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```Your thread mentions the model WG311, but note that my card is the WPN311. I believe that it doesn't to much difference at all so the NETGEAR card has my vote. It costed around €35-€39 in Portugal.


Thank you very much !

I'm interested in both the netgear WPN311 and the WG311T (see my last post in that thread).

> **tomane said:**
> 
I'll take another look at that guide and make sure that I'm using the best encryption scheme, and make the necessary changes in the network configuration. I'll keep you posted regarding how it goes.


cheers,
--to

You could try my wpasupplicant and see if that works (it will probably work) :

network={
ssid="********"
proto=WPA2
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk=******
}

My /etc/network/interfaces (replace eth1 and wext for your stuff) :

```

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

---

### Post by tomane on 2007-02-22
demon: Just a heads up to confirm that your wpa_supplicant worked on the first try.
My router is an SMC BarricadeG 7904WBRA2, running fw 0.15a
I had it configured with wpa/wpa2 mixed mode (I was mistaken; it doesn't even show TKIP), changed it to WPA2 only, and in this mode AES is the only option that it shows for the cypher suite.
Then I adapted my wpa_supplicant.conf to match yours, and after rebooting the router, just needed `sudo /etc/init.d/networking restart´ to get on the air again.
My post is being done through a WPA2+AES encryped wlan as I type :lolflag:

So I figure you might be on your way to be another happy owner of a netgear W*311 card :D

cheers,
--to

---

### Post by ubuntu_demon on 2007-03-01
Great! Thanks for the heads-up.

I will probably go for one of those netgears indeed. (WG311T probably because I've found one of those)

---

### Post by khughitt on 2007-12-21
> I found a NETGEAR WPN311 card on a store and it happens that the card is natively supported using the madwifi driver. I have already installed it and it is running like a charm
From what I've read, the card handles WPA well so I'll give it a shot and see how it goes.

I just bought a WPN311 myself, but have not had any luck setting it up. Do you remember what steps you took to get it working? I would like to connect to a home network with WPA1 encryption.

Thanks :)

---

### Post by tomane on 2007-12-21
> **pwnedd said:**
> I just bought a WPN311 myself, but have not had any luck setting it up. Do you remember what steps you took to get it working? I would like to connect to a home network with WPA1 encryption.

Thanks :)
Hi,
I ended up installing ubuntu server 6.10 / edgy because it shipped with the new madwifi-ng drivers IIRC and making it work was a snap ( see the previous posts showing the config files ). I think 6.06 works too but might require a little bit more work because the included drivers might not be in good shape.

But, if you're looking for an LTS version, why not install gutsy now and upgrade it when hardy comes out? It has better support for the card, I suppose, and upgrading it should be painless.

Best wishes, :-)
--to

---

### Post by khughitt on 2007-12-21
Thanks, I'm actually running Gusty now, but the wireless card doesn't appear to be supported yet. I'm going to try install madwifi though and see if I have any luck with that.

---

