---
title: "searching for wireless pci / usb with wpa2 support without ndiswrapper"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by ubuntu_demon on 2007-02-17
**updated**

I need to buy a wireless pci or usb card with wpa2 support (it's for a desktop pc).  I don't want to use ndiswrapper. I want it to work out-of-the-box with Ubuntu Dapper.

**I'm searching for a good pci/usb card which supports wpa2 (through wpasupplicant) without ndiswrapper.**

I will use wpasupplicant with the following settings :

network={
ssid="********"
proto=WPA2
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk=******
}

(I'm using these settings on my laptop as well)

I will roughly prioritize my wishlist to be able to easier find a suitable card :

1  pci or usb (pci is preferred)
2 works without problems in Ubuntu Dapper
3 opensource driver available with proper wpa support through wpasupplicant
4 I prefer chipsets from companies which collaborate with the open source community on drivers
5 proper wpa2 support using some driver through wpasupplicant
6 40 euros max
7 proper wpa2 support through open source driver + wpasupplicant. would be very cool
8 802.11g support preferred

A list of wireless cards available in the netherlands :
[http://tweakers.net/pricewatch/cat/315](http://tweakers.net/pricewatch/cat/315)

some links :

    * [http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)
    * [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
    * [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)
    * [http://ralink.rapla.net/](http://ralink.rapla.net/)
    * [http://rt2×00.serialmonkey.com](http://rt2×00.serialmonkey.com)
    * [http://atheros.rapla.net/](http://atheros.rapla.net/)
    * [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
    * [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
    * [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
    * [http://tweakers.net/pricewatch/cat/315](http://tweakers.net/pricewatch/cat/315)
    * [http://ubuntuforums.org/showthread.php?t=363633](http://ubuntuforums.org/showthread.php?t=363633)
    * [http://forum.ubuntu-nl.org/topic/7419](http://forum.ubuntu-nl.org/topic/7419)

**I think I will be going for atheros (madwifi driver). Now I still have to find the best PCI card :**

These models look best currently :

Netgear WG311T (108Mbps, PCI)  	
Netgear WPN311 (108Mbps, PCI)  	
D-Link DWL-G520 (108Mbps, PCI) 

see [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility) for details on these cards

List of wireless cards available in the netherlands :
[http://tweakers.net/pricewatch/cat/315](http://tweakers.net/pricewatch/cat/315)

**Tips and suggestions are very much welcome!**

---

### Post by wieman01 on 2007-02-18
Not sure if the Linux driver for Ralink (Serialmonkey) really supports WPA2, it supports WPA only as far as I know... Sorry that I cannot advise more.

One thing: TKIP is part of the WPA(1) framework, not WPA2. Use "AES" instead which is the most secure algorithm available right now.

---

### Post by ubuntu_demon on 2007-02-18
> **wieman01 said:**
> Not sure if the Linux driver for Ralink (Serialmonkey) really supports WPA2, it supports WPA only as far as I know... Sorry that I cannot advise more.

One thing: TKIP is part of the WPA(1) framework, not WPA2. Use "AES" instead which is the most secure algorithm available right now.
Thanks.

my wireless router has the following two options for wpa2 :
TKIP + AES
AES

I had set it to TKIP+AES. This wpasupplicant I showed you works perfectly with these settings.

Do you think AES is more safe than TKIP+AES ?

---

### Post by wieman01 on 2007-02-18
> **ubuntu_demon said:**
> Do you think AES is more safe than TKIP+AES ?
Don't want to get off-topic but yes, AES is more secure. TKIP is part of the old and outdated WPA standard which is WEP based basically. WPA2 replaces WPA as you know and with it comes AES as new encryption standard. I would simply disable TKIP and make it WPA2/AES only. Never really understood why the offer WPA2 with TKIP in the first place... :-)

_**EDIT:**_
Just for the record... You would have to replace these two lines:
> pairwise=**CCMP**
group=**CCMP**

---

### Post by ubuntu_demon on 2007-02-18
> **wieman01 said:**
> Don't want to get off-topic but yes, AES is more secure. TKIP is part of the old and outdated WPA standard which is WEP based basically. WPA2 replaces WPA as you know and with it comes AES as new encryption standard. I would simply disable TKIP and make it WPA2/AES only. Never really understood why the offer WPA2 with TKIP in the first place... :-)

_**EDIT:**_
Just for the record... You would have to replace these two lines:
Thanks. I changed to AES.

---

### Post by ubuntu_demon on 2007-02-18
> **wieman01 said:**
> Not sure if the Linux driver for Ralink (Serialmonkey) really supports WPA2, it supports WPA only as far as I know... Sorry that I cannot advise more.


Thanks. Maybe I'll ask whether I can try the linksys WMP54G (Ver.4)
or the e-tech WGPI03 out and return it if it doesn't work with WPA2.

Do you have any idea which ralink/intel/realtek chipset has the best native linux driver with wpa2 support ?

---

### Post by wieman01 on 2007-02-18
> **ubuntu_demon said:**
> Thanks. Maybe I'll ask whether I can try the linksys WMP54G (Ver.4)
or the e-tech WGPI03 out and return it if it doesn't work with WPA2.

Do you have any idea which ralink/intel/realtek chipset has the best native linux driver with wpa2 support ?
Not exactly one that I have tried myself, but check this out: [http://www.linux-wlan.org/docs/wlan_adapters.html.gz]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz")

There are 3 listed with AES support (see "COMMENTS"). Don't know about the others.

---

### Post by ubuntu_demon on 2007-02-18
> **wieman01 said:**
> Not exactly one that I have tried myself, but check this out: [http://www.linux-wlan.org/docs/wlan_adapters.html.gz]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz")

There are 3 listed with AES support (see "COMMENTS"). Don't know about the others.
Sadly those three aren't pci or usb.

---

### Post by wieman01 on 2007-02-18
> **ubuntu_demon said:**
> Sadly those three aren't pci or usb.
Perhaps it helps picking the USB/PCI ones and checking in the forums if somebody else has had luck with them. Just an idea...

---

### Post by wieman01 on 2007-02-18
Hello again, 

These are the adapters that work using WPA... not sure if this refers to version 1 or 2 but users have confirmed that these work just fine (see bracket for driver used):
> 1. Linksys WUSB54G V4 (ndiswrapper; wpa-driver = wext)
2. Intel IPW2200 (Linux driver; wpa-driver = wext)
3. Linksys WPC54G (ndiswrapper; wpa-driver = wext)
4. D-Link WNA-2330 (Linux driver; wpa-driver = madwifi)
5. Linksys WMP54G V2 (ndiswrapper; wpa-driver = wext)
6. D-Link WDA-2320 (Linux driver; wpa-driver = madwifi)
Guess D-Link will be a good choice?

---

### Post by ubuntu_demon on 2007-02-18
handy links :
[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
[http://www.passys.nl/tips/tip40_en.htm](http://www.passys.nl/tips/tip40_en.htm)

---

### Post by ubuntu_demon on 2007-02-18
I get the impression that intel has the best supported chipsets. Sadly the only intel pci card I've found is not of a well known brand and a bit expensive (70 euros) :
[http://www.passys.nl/tips/tip40_en.htm](http://www.passys.nl/tips/tip40_en.htm)

70 euros is too much for a wireless card. Especially since wireless cards start at about 15 euros.

---

### Post by ubuntu_demon on 2007-02-19
I will prioritize my wishlist to be able to easier find a suitable card.

1  pci or usb (pci is preferred)
2 works without problems in Ubuntu Dapper
3 opensource driver available with proper wpa support through wpasupplicant
4 I prefer chipsets from companies which collaborate with the open source community on drivers
5 proper wpa2 support using some driver through wpasupplicant
6 40 euros max
7 proper wpa2 support through open source driver + wpasupplicant. would be very cool
8 802.11g support preferred

I blogged about this :
[http://ubuntudemon.wordpress.com/2007/02/19/searching-for-wireless-pciusb-card-which-supports-wpa2/](http://ubuntudemon.wordpress.com/2007/02/19/searching-for-wireless-pciusb-card-which-supports-wpa2/)

---

### Post by ubuntu_demon on 2007-02-19
Does anyone have an opinion about the netgear WG311T with atheros chipset ?

I suspect that this card will work without problems under Dapper. I also think it will work with WPA2. The madwifi driver is open source needs a binary blob that's why restricted modules need to be installed for the card to work.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)
[http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx](http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx)
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

---

### Post by ubuntu_demon on 2007-02-19
I think I will be going for atheros (madwifi driver). Now I still have to find the best PCI card :

List of wireless cards available in the netherlands :
[http://tweakers.net/pricewatch/cat/315](http://tweakers.net/pricewatch/cat/315)

Compatibility information :
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

**Tips and suggestions are very much welcome!**

---

### Post by wieman01 on 2007-02-19
> **ubuntu_demon said:**
> I think I will be going for atheros (madwifi driver). Now I still have to find the best PCI card :

List of wireless cards available in the netherlands :
[http://tweakers.net/pricewatch/cat/315](http://tweakers.net/pricewatch/cat/315)

Compatibility information :
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

**Tips and suggestions are very much welcome!**
There is one user who is trying out a D-link DWL-G520 PCI adapter (see signature post #207). It's an Atheros chipset indeed. We are working on WPA1 right now but perhaps I can convince him/her to give WPA2 a go... What do you think?

---

### Post by ubuntu_demon on 2007-02-19
> **wieman01 said:**
> There is one user who is trying out a D-link DWL-G520 PCI adapter (see signature post #207). It's an Atheros chipset indeed. We are working on WPA1 right now but perhaps I can convince him/her to give WPA2 a go... What do you think?

I would be very interested whether WPA2 works on that one.

**edited**

These models look best currently :

Topcom Skyracer Pro PCI 154 (108Mbps PCI)
Edimax EW-7325Ig (108Mbps, PCI) 
Netgear WG311T (108Mbps, PCI)  	
D-Link DWL-G520 (108Mbps, PCI) 

see [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility) for details on these cards

I'm very much interested in opinions and experiences.

---

### Post by ubuntu_demon on 2007-02-20
I went looking for atheros based cards in my local town but couldn't find any. I ended up borrowing the e-tech wgpi03 to try whether I could get it to work with WPA(2).

The e-tech wgpi03 worked out of the box for unsecured WIFI (I only had to modprobe st61 and put the ra0 interface in my interfaces).

But I couldn't get it to work with WPA or WPA2. I also compiled the newest st61 driver from ralink which worked but not for WPA or WPA2. (I couldn't get  wpasupplicant 0.4.7 compiled so I tried it using the .dat file approach)

Conclusion : the e-tech wgpi03 isn't suitable for my needs and I brought it back.

I will try another town and see whether I can buy a D-Link DWL-G520 (108Mbps, PCI) or Netgear WG311T (108Mbps, PCI) somewhere. I do want to return it if it doesn't work so ordering online is not a option.

---

### Post by ubuntu_demon on 2007-02-20
These models look best currently :

Topcom Skyracer Pro PCI 154 (108Mbps PCI) (also written as skyr@cer)
Edimax EW-7325Ig (108Mbps, PCI)
Netgear WG311T (108Mbps, PCI)
D-Link DWL-G520 (108Mbps, PCI)

see [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility) for details on these cards

I'm very much interested in opinions and experiences.

---

### Post by ubuntu_demon on 2007-02-20
**updated**

I&#8217;m searching for an atheros based PCI card which works (almost) out-of-the-box in Ubuntu Dapper. 
The card has to support WPA2 personal (ccmp/aes). I have made selection of a few possible cards.

Would you prefer netgear and d-link above edimax,topcom,smc ?

If someone has any experience with one of these cards on Ubuntu Dapper with WPA2 personal (ccmp/aes). 
I would be very interested.

Does someone from the Netherlands know a shop in alkmaar,amsterdam or maastricht where I can buy a card in person ? 
So that I can return it if I can't get it to work.

More information on these cards :
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

Edimax EW-7325Ig (108Mbps, PCI) 25-35 euro
* works for someone on ubuntuforums
* madwifi wiki : AR2414A (a/b/g/turbo) or user comment: AR5212

SMC WPCIT-G (108Mbps, PCI) 25-35 euro
* madwifi wiki : works in debian
* madwifi wiki : AR5212 (Atheros 802.11b/g)

Topcom Skyracer Pro PCI 154 (108Mbps PCI) 30-40 euro
* madwifi wiki : works in Ubuntu
* madwifi wiki : AR5212 (802.11a/b/g)

Netgear WG311T (108Mbps, PCI) 35-50 euro
* uwiki : version WG311TGE (sold as WG311T) works out of the box on Dapper 6.06. Same for WGT311TFS in Edgy;
* popular on ubuntuforums (112 threads)
* popular on madwifi user mailinglist (172 threads)
* madwifi wiki : AR5002G (b/g) (AR5212)

D-Link DWL-G520 (108Mbps, PCI) 40-60 euro
* popular on ubuntuforums (160 threads)
* uwiki : DAPPER: Nearly works out-of-the-box,
* popular on madwifi user mailinglist (344 threads)
* madwifi wiki : has one old or 520+ version (A3) which has TI chipset and doesn&#8217;t work
* madwifi wiki : AR5212 (b/g) or AR 2414A-00 (b/g)

Netgear WPN311 (108Mbps, PCI) 45-55 euro
* uwiki : works
* forums : works
* AR5004G (11b/11g/turboG) or user comment : AR5212

---

### Post by tomane on 2007-02-22
Hi, I believe that the netgear WG311 is a good choice. My [b]WPN[b]311 has been working for a couple of weeks with WPA and it is very reliable too (my server uses it to connect to the broadband router).

I'm not sure if I am using CCMP/AES (all these acronyms are more cryptic than the encryption itself ;o] ) but it works like a champ.

I followed [this guide]("http://madwifi.org/wiki/UserDocs/802.11i") from madwifi.org on my first attempt. Only then I found [this fabulous thread]("http://www.ubuntuforums.org/showthread.php?t=202834") in the fora, and it was a matter of glueing what I had from madwifi.org with the network configuration file, so I figure that my configuration may be sub-optimal...

I'll try to set up CCMP/AES solely based on the forum thread and keep you posted with the results.

cheers,
--to.

---

### Post by ubuntu_demon on 2007-02-22
> **tomane said:**
> Hi, I believe that the netgear WG311 is a good choice. My [b]WPN[b]311 has been working for a couple of weeks with WPA and it is very reliable too (my server uses it to connect to the broadband router).

I'm not sure if I am using CCMP/AES (all these acronyms are more cryptic than the encryption itself ;o] ) but it works like a champ.

I followed [this guide]("http://madwifi.org/wiki/UserDocs/802.11i") from madwifi.org on my first attempt. Only then I found [this fabulous thread]("http://www.ubuntuforums.org/showthread.php?t=202834") in the fora, and it was a matter of glueing what I had from madwifi.org with the network configuration file, so I figure that my configuration may be sub-optimal...

I'll try to set up CCMP/AES solely based on the forum thread and keep you posted with the results.

cheers,
--to.
thanks !

---

### Post by tomane on 2007-02-22
Hi, I got home a while ago and had a chance to check my router and its encryption scheme. I set it up in order to use *only* **WPA2** with AES (it was using mixed mode previously). Then I took your demon's wpa_supplicant.conf from [this thread]("http://ubuntuforums.org/showthread.php?p=2194028"), adapted it, did a network restart and everything is still working, no funny explosions comming from the router or the server at all :)

So, yeah, the WPN311 handles WPA2 quite well and I'm really happy with it.

cheers,
--to

P.S.  Please note, I meant WPA2 up there, just in case you read WPA in your email notification. There's always some bloody typo to spoil it, no matter how much I check them... :rolleyes:

---

### Post by richieeee on 2007-02-28
Hi

I just got the WPN311. At first I thought I must be doing something wrong with the WPA2 instructions, but in the end I realised the WPN311 just had a very poor signal -90dBm and was not picking up the AP. The only way I could get a reliable connection was to put the wifi router within a metre of the PCI card. I read on the madwifi that others have similiar signal problems, but none with the same card in Windows. 

Has anyone else with the WPN311 experience this?

My setup

Edgy
AP Linksys version 2 running latest Hyper-WRT
AP is 7 metres away thro one wall. I works fine under the same distance with a laptop and Nokia N800
netgear WPN311 PCI

I may return it for a different type of card, any recommendations? Or is there a tweak to get the signal improved on the WPN311?

Cheers
Rich

---

### Post by tomane on 2007-02-28
those -90dBm are for signal or noise? what's the output of iwconfig ath0?

I also had some quirks with reception, but the card was in a separate room, with one wall between and the pc was placed in the grond, in the oposite corner. The distance to the AP is about 6~7 m. I didn't have much trouble connecting to the AP, although sometimes network response was laggy. My typical signal / noise levels shown by iwconfig were -74dBm / -94dBm, sometimes worse. Then I got an external antena with a 2m cable (6 dBi gain, typical for omnidirectional antenas), replaced the original one with it, and placed the antena about 1m above the ground. Signal level bumped to a comfortable -40dBm typical and I could notice a real improvement in network responsiveness.

In my case there were too many obstacles in the way, so I can't really blame much on the card.
Check the placement of your PC and the AP as well, try to keep then away from walls and metalic parts, as well as sources of EM inferference, it can affect the signal quality severely, but playing around with it, you might even find the optimal placement for the AP and PC.

cheers,
--to

---

### Post by ubuntu_demon on 2007-03-01
> **richieeee said:**
> 
........
I may return it for a different type of card, any recommendations? Or is there a tweak to get the signal improved on the WPN311?

Cheers
Rich

You could try a netgear WG311T

---

### Post by ubuntu_demon on 2007-03-26
I recently bought a wg311T and it works perfectly.

some configuration details :
[http://www.ubuntuforums.org/showpost.php?p=2356363&postcount=281](http://www.ubuntuforums.org/showpost.php?p=2356363&postcount=281)

---

