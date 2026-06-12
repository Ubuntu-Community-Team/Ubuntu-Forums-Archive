---
title: "Nintendo DS wifi without WEP"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by feap on 2006-09-20
I can't get Nintendo DS handheld to recognize a wifi network from my laptop. It doesn't even show up on the available wifi networks list while other nets do. My laptop is connected to the internet via LAN and I want to use the laptop's wireless router as an access point for the DS.

I've gotten as far as learning that WEP should be turned off (iwconfig ath0 key off) but that doesn't help. My iwconfig output doesn't show the status of WEP:

ath0      IEEE 802.11  ESSID:"xxxx"
          Mode:Managed  Frequency:5.745 GHz  Access Point: Not-Associated
          Bit Rate:6 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Does anyone have any experience with getting a DS to recognize the wifi network?

[moving this from absolute beginners]

---

### Post by Echo35 on 2006-09-20
The problem may not be with your network, but with the actual router you are using. The DS support for WiFi brands is quite spotty, so it may be that. Also, do you need to do anything special to connect on your laptop? Is there some sort of web page you have to visit first or some sort of cookie authentication? If so, that won't work either since the DS doesn't accept cookies. However, if this were the case, you would usually be able to see it, just not connect. The most likely case here is that the brand is one that's not supported by the DS. Can you tell me what brand/model router you have?

---

### Post by feap on 2006-09-20
No cookies needed. My laptop is connected to the internet via LAN and I need the wifi only to connect the DS to the laptop.

My wireless router on the laptop is 3COM, which after a quick googling seems to work well with DS in general. I don't know how to get the exact model number under ubuntu.

---

### Post by Echo35 on 2006-09-20
I assume the laptop is broadcasting it's WiFi signal? Is the router hooked to the laptop or to the actual network?

---

### Post by feap on 2006-09-20
I don't know how to enable broadcasting in ubuntu, iwconfig doesn't appear to have such an option.

---

### Post by Echo35 on 2006-09-20
Ah. Can other things connect to the wireless? Just because it's a router or wireless card doesn't mean it's actively broadcasting. To clarify, is it a router or a card in your laptop?

---

### Post by feap on 2006-09-20
I don't know if other things can connect to it as I have no other wireless devices. It's a pcmcia card in my laptop with an extensible antenna.

---

### Post by Echo35 on 2006-09-20
Oh, so it connects to a network? See, cards like that don't broadcast a signal. You need a router for that. You know, those big box things with all the antennae on them? If that's the case, you might want to check out the Nintendo DS USB adapter on their website.

---

### Post by feap on 2006-09-20
kk, I was under the impression it does broadcast... I guess I'll stop by the local computer store and see if they have a wireless router, as a cheap one costs as much as the DS USB adapter (which apparently doesn't work with linux).

---

