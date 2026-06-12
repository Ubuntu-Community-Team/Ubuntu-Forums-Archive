---
title: "Trendnet 501pc Atheros wireless card won't connect to WPA"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by voltage223 on 2008-02-08
Working with an IBM Thinkpad T30 with Kubuntu 7.04 Feisty Fawn.

I tried originally to connect to our WPA2-enabled wireless network with the built-in Cisco Aironet card.  It successfully connects when the network is unsecured, but when it is WPA-enabled it just hangs on "configuring device."  I then read on ([http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)) that this was not supported.  I had another wireless card laying around so I put in a Trendnet 501pc atheros wireless card.  I tried connecting to the WPA2 network with that and got the same effect, hangs on "configuring device" and eventually gives up.  However this card also successfully joins networks that are unsecured.

What else can I do to get this to work?

---

### Post by voltage223 on 2008-02-09
Has anyone had a similar problem and resolved it??

---

### Post by ModelM on 2008-02-09
I don't know about the Cisco card but when I looked up the Trendnet card on this page:

[http://trendnet.com/langen/products/proddetail.asp?status=view&prod=100_TEW-501PC&cat=80](http://trendnet.com/langen/products/proddetail.asp?status=view&prod=100_TEW-501PC&cat=80)

it look as if WPA2 is not supported by this card, only WEP & WPA-PSK. So, to connect to a wireless network encrypted using WPA2, you'll first need a card which has that capability.

---

### Post by voltage223 on 2008-02-09
"the TEW-501PC uses WPA-PSK with AES and TKIP encryption"

To my knowledge, I believe that "WPA with AES" is the same thing as WPA2, as the major difference with WPA2 is supposed to be the introduction of AES encryption.

---

