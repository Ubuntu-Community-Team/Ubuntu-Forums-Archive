---
title: "Opinions on a new router to boost device access - to prevent router crashing"
date: 2017-12-05
forum: Networking &amp; Wireless
---

### Post by stewbuntu2 on 2017-12-05
I tried to think about where to ask some people about routers and I thought of Ubuntu forums first. I hope this is the right place to post this and it's okay. Here are my questions and thoughts and I'm wondering what insights you might have, what to avoid beside spending extra money, and firmware on other brands other than Asus which I like bc of how easy it i to change them into a Repeater or AP, add port forwarding, etc. I don't know how the other brands are these days.

1.) Do the new AC routers which have MU-MIMO work with N devices? Mu came after AC 2nd Gen, but I'm hoping that its backwards compatible as in the router can handle the traffic that way for N devices also

2.) I read the Archer C7 by tp link is 3x3 for 802.11**N** is this correct and how do I find what other routers can convert their channels down?  Will a tri band router downgrade to 2.4G on all bands so I could then set eah band to channels 1,6,& 11 (if I set the three bands manually to those channels)?

**My environment:**
I ask these questions because my devices are all N currently but I have read that the AC routers can handle more traffic which is my problem. Add Grandparents streaming/Facetime, kids downloading junk, siblings over, and 2 TVs (that have no "cable" just intenet streaming access) = my router crashes and I have to reboot or just change the wifi password. The router is fine when just my wife and I. This article has results of 50% to 200% more through ut vs an N router. [https://www.smallnetbuilder.com/wireless/wireless-features/32512-does-an-ac-router-improve-n-device-performance](https://www.smallnetbuilder.com/wireless/wireless-features/32512-does-an-ac-router-improve-n-device-performance)

**So my goal** is to get MU, at least 3x3 "lanes" if possible which I think is AC2000+, while 4x4 is AC3000+ maybe dual core would help (but I seem to have read it really only helps when using VPN and other intensive services). I have the TVs on cat6 now. I was thinking also take my Asus N600 and turn it into an AP for wifi users in the basement apartment on channel 1, and my Asus N300 upstairs on the 3rd floor on channel 11. Maybe those APs would decrease the connections to the main router on channel 6 so it won't crash. I know they will eat up the bandwith available, but that was never an issue if the router didn't crash, streams never lagged, the N600 would just crash when a goup of 4+ comes over. I can also set up a guest network and decrease their speed if it's possible, but I think whatever router I have them log into will then crash as well and I will be dealing with that during the middle of a weekend. I'm trying to build up and distribute out, but I'm not sure if I should go as far as tri band/AC3000 and up for N devices. I'm on the fence on how reliable switches are vs having a router with 8 ports (can run Vera Edge, 2 TVs, IP cameras, computer, and have 2 ports still open for those APs.) I once has a netgear switch keep crashing my ASUS N300 router which is why I bought the N600 and then found out it was the switch. Maybe 8 ports would be a good idea, or 3 cheap N routers to make more APs. I ran Cat6 to all rooms when I remodeled.

Archer c7 with 3x3 mentioned at the bottom of this review:
[https://www.amazon.com/review/R1INMPZDIVVEIB/ref=ask_dp_lswr_rp_hza](https://www.amazon.com/review/R1INMPZDIVVEIB/ref=ask_dp_lswr_rp_hza)

I really like how easily Asus routers do AP or Repeater mode, but wonder how it will work with another brand. Linksys is the only triband down near $100 unless I buy Amazon warehouse deals where they are all about $50 less.

I'm thinking: 

TP Link Brand:
$80 -AC1750 (archer c7) Archer C7 v.2 - [https://www.pcmag.com/review/352074/tp-link-archer-c7-ac1750-wireless-dual-band-gigabit-routergreat](https://www.pcmag.com/review/352074/tp-link-archer-c7-ac1750-wireless-dual-band-gigabit-routergreat) price if the HTTPS issues have been fixed with newer firmware (need to look into it further)
$109 -AC1900 (c9) for around $100 has great reviews vs the https issue

Asus Brand:
$67 - AC1700
$73 RT-N66w N900 good in tests
$115 - AC1750
$250 **8 ports** = AC3100 W 4X4 


Netgear Brand
$89 AC1750 (R6700) **good review** [https://thewirecutter.com/reviews/best-wi-fi-router/](https://thewirecutter.com/reviews/best-wi-fi-router/)
$150 AC1900 has first in Netgear group to have QoS to limit visitors bandwith
$230 R8500 6 Lan Ports

Linksys Brand
$49  - AC1750 - could get 3 at this price and create 2 new APs
$105 - AC3200 **Tri band for around $100 **if bands convert down to 2.4 GHz
$89 AC1900

Trend Net Brand:
$110 - Trend Net good review AC2600 [https://www.pcmag.com/review/349107/trendnet-ac2600-streamboost-mu-mimo-wifi-router-tew-827dru](https://www.pcmag.com/review/349107/trendnet-ac2600-streamboost-mu-mimo-wifi-router-tew-827dru)

---

### Post by gordintoronto on 2017-12-06
What speed is your Internet access? Or are you mostly concerned with bandwidth within your network?

I recently upgraded to 25 Mbps, and my ISP sold me a Technicolor (!!!) modem/router as part of the upgrade. It has worked flawlessly. My household is only four people, but we have 15 devices, and we all like to stream videos. I have an amusing picture of my wife streaming Chinese video on her iPad while doing email on her desktop computer.

---

### Post by SeijiSensei on 2017-12-07
I have an Archer C7.  I don't know about all the stuff that seems to concern you.  I do know it works fine with all my N devices as well as with my desktop machine that has a TP-Link AC1200 USB adapter.  The AC connection has to run in the 5 GHz band.  My N connections generally use the 2.4 GHz band.  I let the router handle all of this and never think about it.  I've occasionally chosen specific channels to use in an effort to reduce interference from neighbors' devices, but again, this usually hasn't been necessary.

I don't know what those "HTTPS issues" are.  I have no problem with HTTPS connections at all.

---

### Post by chili555 on 2017-12-07
I also have an Archer C7, although mine is a V.1.

I separate the 2.4 and 5 gHz segments by giving each its own SSID. I use and recommend fixed channels. I recommend a site survey:```
nmcli dev wifi list
```There are at least eleven devices connected to it at all times. 

I have no crashes or other problems. I am unaware of any https issue.

---

### Post by SeijiSensei on 2017-12-07
> **chili555 said:**
> I separate the 2.4 and 5 gHz segments by giving each its own SSID.
I do this, too. N devices like this LG phone can use both; the AC protocol only runs over the 5 GHz channel.

---

### Post by chili555 on 2017-12-07
> **SeijiSensei said:**
> I do this, too. N devices like this LG phone can use both; the AC protocol only runs over the 5 GHz channel.I think a number of wireless drivers in Linux struggle to stay connected and then drop when the router decides to upshift from 2.4 to 5 gHz. Then I get a new case here on this forum: "My wireless drops all the time. What can I do?"

---

### Post by SeijiSensei on 2017-12-07
> **chili555 said:**
> I think a number of wireless drivers in Linux struggle to stay connected and then drop when the router decides to upshift from 2.4 to 5 gHz. Then I get a new case here on this forum: "My wireless drops all the time. What can I do?"
Perhaps.  Before buying an AC1200, I used this device which worked flawlessly:
[https://www.newegg.com/Product/Product.aspx?Item=N82E16833704045](https://www.newegg.com/Product/Product.aspx?Item=N82E16833704045)

For 802.11n devices I always chose the Atheros chipset.

For the 802.11ac device I have now, which appears to use an RTL8821au, I had to compile the driver myself for Kubuntu 14.04 some months ago.  Apparently there is now a driver available from the [repositories]("https://launchpad.net/ubuntu/xenial/+package/rtl8812au-dkms") for 16.04+.

---

