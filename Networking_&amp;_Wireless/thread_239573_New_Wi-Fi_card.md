---
title: "New Wi-Fi card"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by tgunner on 2006-08-19
Hi all,

I have my Newer Compaq V2000z Lappy here, and it's been great for me. But the one thing that has always kept me from switching to ubuntu on it is the infamous Broadcom AirForceOne 54g mini-PCI wireless card. Now, I will be going back to school, and want to use ubuntu, so, I need a new mini-PCI wi-fi card. My school uses WPA encryption, is there any difficulty using WPA in linux? I'm looking at either an intel card, or an atheros based one. Any specific recommendations, comments, or tips?

---

### Post by compwiz18 on 2006-08-20
Howdy

Before you go out and buy a new card, it may be worth trying to get your current card to work.  Take a look here: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
and here: [http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+wireless+card](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+wireless+card)
This should help if you've got a Broadcom wifi card.

And yes, I've got a Compaq v2000 (without the Z)that works fabulously.

---

### Post by tgunner on 2006-08-20
Thanks for the response. I've tried the tutorials you listed, and did get the card to work. It's just nowhere near reliable enough for me. The reason your V2000 works so well is that it's an intel model, featuring an intel wireless card. The big thing I need is WPA, and thats why I need to know how well ubuntu can handle WPA on an entirely Windows Network, with Microsoft-minded admins. I can't go ask them for assistance with WPA, they will probably shun me for using linux, and try to make me buy Windows on the spot! ;)

---

### Post by compwiz18 on 2006-08-20
Mine is an AMD model, actually.  I believe that you can use WPA, although I don't.  Good luck.  You can duel boot too, if you need Windows for WPA...

---

### Post by tgunner on 2006-08-21
Yes, it is says V2000, but if it is an AMD model, it is technically the V2000z. The individual model numbers are different also, mine is the V2450US. I read most of the ubuntu wireless-docs, and came close to kind of card I want. It is an MSI MP54G4 based on the Ralink RT2500 chipset. I found this nice guide here about how to get WPA mostly working: 

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

My other choice is an Intel Pro 2200BG, but I have heard of WPA issues with this card. If anyone has any more input on this discussion, please post. I need to order this soon for school.

---

### Post by lupine_nickt on 2006-08-21
I'm using one of [these](http://cgi.ebay.co.uk/Atheros-GIGABYTE-GN-WIAG02-Mini-Pci-802-11g-108-Mbit_W0QQitemZ9728962738QQihZ008QQcategoryZ45000QQssPageNameZWD1VQQrdZ1QQcmdZViewItem) in my router at the moment; it's rock solid, and trivial to set up.


And no, that's not my auction ;). I *think* you can get them cheaper from eBuyer, but YMMV...

Edit: [here](http://linitx.com/index.php?cPath=34) also has a number of (presumably) working miniPCI cards, as well as the antennae! They're a nightmare to get hold of... so bookmark that page. You won't regret it ;)

xF,

...Nick

---

### Post by tgunner on 2006-08-21
I looked up the Gigabyte model you posted, and I can get it here for $28 (~15 pounds) including shipping. I see that it is based on an Atheros chipset, I was looking for these originally, but the two I saw above came up too. What OS do you use this card with? ubuntu? Have you tried WPA yet? I guess I have 3 choices now:

MSI MP54G4 based on the Ralink RT2500 chipset

Intel Pro 2200BG

GigaByte GN-WIAG02 based on the Atheros AR5005GS chipset

---

### Post by mjziegle on 2006-08-21
> **tgunner said:**
> I looked up the Gigabyte model you posted, and I can get it here for $28 (~15 pounds) including shipping. I see that it is based on an Atheros chipset, I was looking for these originally, but the two I saw above came up too. What OS do you use this card with? ubuntu? Have you tried WPA yet? I guess I have 3 choices now:

MSI MP54G4 based on the Ralink RT2500 chipset

Intel Pro 2200BG

GigaByte GN-WIAG02 based on the Atheros AR5005GS chipset

Anything Atheros works great with everything.  WPA, master, monitor the works.  And it's supported in the kernel.  I wouldn't try anything else.

I have a Toshiba L25

---

### Post by lupine_nickt on 2006-08-21
I'm using AspisOS (linux-based, uses exactly the same madwifi source as you'd use for Ubuntu) for my router; but any install of Ubuntu would also work. Just get the madwifi drivers and build... if you're lucky, the madwifi in linux-restricted-modules will work fine for you. If not... well, building your own driver isn't  difficult, as such. Just finicky.

xF,

...Nick

---

