---
title: "Recommend Hardware?"
date: 2005-05-31
forum: Networking &amp; Wireless
---

### Post by doans on 2005-05-31
I have been pulling my hair out using my wireless usb adapter (Netgear WG111) with Hoary! 

Connection lasts for hours sometimes and only minutes other times.  I have to deactivate it, unplug the usb adapter, wait for a few secs, plug adapter back in, and then activate it from the network-admin gui. 20 or 30 times a day!  This is very unproductive.

So, I was thinking that maybe someone out there could suggest some better hardware that would lead to a more stable wireless internet connection.  Anyone have suggestions? How is your wireless connection?  Is there a stable solution?

My setup:
Dual boot (WinXP/Ubuntu) desktop system using Netgear firewall router 802.11g (WGT624) and 128bit WEP encryption, a finely tuned Hoary setup, and ndiswrapper 1.2rc1-1,

---

### Post by thrift on 2005-05-31
Yes, there are very stable solutions.

I have two PCMCIA cards which both work well.

The first is an Xterasys that is based off of an atheros chip.  It appears to work fine, even in promiscuous mode, but is an 802.11b card.  Paid about $20 for it new.

The second is a proxim orinoco 11a/b/g combocard.  It is based off an orinoco card, is pretty feature rich, and has excellent linux support.  Paid about $70 for it new.

(found these both on pricewatch)

Orinoco chipsets appear to be one of the best.  Some of the Cisco's work really well.  Some of the prism chipsets work really well.

Hope that is helpfull.

---

### Post by doans on 2005-05-31
[QUOTE=thrift]Yes, there are very stable solutions.

I have two PCMCIA cards which both work well.

The first is an Xterasys that is based off of an atheros chip.  It appears to work fine, even in promiscuous mode, but is an 802.11b card.  Paid about $20 for it new.

The second is a proxim orinoco 11a/b/g combocard.  It is based off an orinoco card, is pretty feature rich, and has excellent linux support.  Paid about $70 for it new.

(found these both on pricewatch)

Orinoco chipsets appear to be one of the best.  Some of the Cisco's work really well.  Some of the prism chipsets work really well.

Hope that is helpfull.[/QUOTE]
 Thanks for the reply. I assumed there had to be some solutions that were more stable than my current setup.  But, I have a desktop system and I don't think PC Cards are the best way to go.  Maybe I am wrong?

So far, I am considering purchasing the Netgear WG311T. Seems to have good luck in Ubuntu that I can see. Anybody have the WG311T?

---

### Post by thrift on 2005-05-31
Repeat after me.

"It's not the card, it's the chipset"

Different models of the same card can have different chipsets, so be carefull.  One version of the card can work perfectly well, and another not work at all.  Althought PCMCIA cards aren't what you are looking for, from my experience, if you find an orinoco based PCI card, you'll be set.  I made sure when I got my card it had the chipset in the name. Searching on pricewatch I found a usb ethernet adapter with an orinoco chipset.  

I would think PCI would be the best choice for a desktop machine though.  Try searching for "Orinoco PCI" on pricewatch.com.  They appear to range between about $70 and $100.  You'll also find that many PCI versions of network cards are just the PCMCIA card stuck in a PCI card slot.  You'll see what I mean if you do the search.

Other chipsets should work fine, but the card doesn't matter.  It's the chipset.


By the way I think the Cisco chipset that is well supported is the Cisco Aironet.  It is pricey though.

---

### Post by byen on 2005-05-31
this may not be a solution but I hope you take it as a caution. while looking at various card ..oops i mean chipsets.. please be careful while selecting Broadcom cards...I had to go through hell to use my card and this stands true with almost every other Broadcom user. SO if this maker was on your list..strike it off!

---

### Post by thrift on 2005-05-31
Agreed.  Bad experiences with broadcom chipsets.  Avoid like the plague.

---

### Post by doans on 2005-06-02
Thanks for all the suggestions. I have gone ahead and purchased the Netgear WG311T PCI  which uses the Atheros AR5212 chipset and apparently has decent linux support.

I have been surfing away for about a day now, and have not had a bit of trouble. Also, the initial setup took just a few minutes. Currently using Ndiswrapper that I used with the previously mentioned usb adapter.  So far so good.  Thanks again for the help along the way.

---

### Post by thrift on 2005-06-02
You shouldn't need ndiswrapper for an Atheros chip.  Have you tried it without ndiswrapper?

---

### Post by doans on 2005-06-02
[QUOTE=thrift]You shouldn't need ndiswrapper for an Atheros chip.  Have you tried it without ndiswrapper?[/QUOTE]

No, I just used the new driver with ndiswrapper.  Are you saying just remove ndiswrapper and the driver is already included in Ubuntu?  Ubuntu will recognize the Atheros chipset and the wireles will work without ndiswrapper?

---

### Post by thrift on 2005-06-02
Correct.  With my atheros card, with no ndiswrapper installed, I plug it into my PCMCIA slot, hear a beep.  and voila the driver was loaded and I now have an ath0 interface.

Using a native driver should probably save you a lot of trouble.  Also the native driver is more feature rich and can work with kismet and the like.

---

