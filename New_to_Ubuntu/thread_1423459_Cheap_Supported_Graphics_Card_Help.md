---
title: "Cheap Supported Graphics Card Help"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by techiefox on 2010-03-06
My built in integrated graphics card is a  ATI Radeon Xpress 200  and it doesn't run very well under ubuntu or just linux in general , Does anybody know of a really cheap $10-15 graphics card thats PCI Express x16 VGA only on ebay that is fully supported in Ubuntu ? I dont play games or anything on it just basic web browsing and music  . If you can find one on ebay that is fully supported and has free shipping and buy it now , please post a link for me . Any advice is appreciated 

My computer is a eMachines W3503 and a link to the specs can be found at [http://www.walmart.com/ip/eMachines-160-GB-W3503/5027232](http://www.walmart.com/ip/eMachines-160-GB-W3503/5027232)

Thanks

---

### Post by Tahakki on 2010-03-06
My old card, a geForce 4400 Ti, worked perfectly with Karmic. You should be able to get it cheap - it's an old card.

---

### Post by soryu on 2010-03-06
Don't Go To Far Back I Have A geFORCE 100/200MX x32 VGA.
Open Gl,Hibernate, Suspend Problems.

---

### Post by techiefox on 2010-03-06
> **soryu said:**
> Don't Go To Far Back I Have A geFORCE 100/200MX x32 VGA.
Open Gl,Hibernate, Suspend Problems.

Well if you guys have any eBay links please post them , I have a VGA monitor

---

### Post by goldblattster on 2010-03-06
> **techiefox said:**
> My built in integrated graphics card is a  ATI Radeon Xpress 200  and it doesn't run very well under ubuntu or just linux in general , Does anybody know of a really cheap $10-15 graphics card thats PCI Express x16 VGA only on ebay that is fully supported in Ubuntu ? I dont play games or anything on it just basic web browsing and music  . If you can find one on ebay that is fully supported and has free shipping and buy it now , please post a link for me . Any advice is appreciated 

My computer is a eMachines W3503 and a link to the specs can be found at [http://www.walmart.com/ip/eMachines-160-GB-W3503/5027232](http://www.walmart.com/ip/eMachines-160-GB-W3503/5027232)

Thanks
I don't know about that- PCIE x16 is really a Mainstream/Hardcore Gaming standard.

---

### Post by jim Kane on 2010-03-06
> **techiefox said:**
> My built in integrated graphics card is a  ATI Radeon Xpress 200  and it doesn't run very well under ubuntu or just linux in general , Does anybody know of a really cheap $10-15 graphics card thats PCI Express x16 VGA only on ebay that is fully supported in Ubuntu ? I dont play games or anything on it just basic web browsing and music  . If you can find one on ebay that is fully supported and has free shipping and buy it now , please post a link for me . Any advice is appreciated 

My computer is a eMachines W3503 and a link to the specs can be found at [http://www.walmart.com/ip/eMachines-160-GB-W3503/5027232](http://www.walmart.com/ip/eMachines-160-GB-W3503/5027232)

Thanks


dont waste your time with S/H video cards
you can buy a new Nvidia &#65279;GeForce 8400 GS for less and it works perfectly with Ubuntu.

---

### Post by techiefox on 2010-03-06
> **jim Kane said:**
> dont waste your time with S/H video cards
you can buy a new Nvidia &#65279;GeForce 8400 GS for less and it works perfectly with Ubuntu.

Does that card work with a vga monitor ? Also will that card require a new power suppy?

---

### Post by 3rdalbum on 2010-03-06
> **techiefox said:**
> Does that card work with a vga monitor ? Also will that card require a new power suppy?

DVI can carry digital AND analog signals, so graphics cards usually come with an adapter that converts the DVI out into a VGA out. That is, unless they have a VGA (D-SUB) connector on the back; I've seen 8400GS' with a VGA connector. Not all of them will have, but if not they should have that adapter. Obviously, check for this when buying off eBay as some people might have lost the adapter.

It looks like the 8400 powers itself off the PCI-E bus, so as long as your power supply isn't currently drawing close to its limits you should be fine. It doesn't need any extra power connectors going straight to the card. FYI I used to have a PCI-E-powered 8600, so if you wanted some extra performance this would be a good way to go too.

I agree with an earlier poster who said not to buy too old a card. The 8000 series is the oldest I'd recommend. Anything earlier and you're looking at ancient drivers that will probably require you to edit your xorg.conf file. Also, the 8000 series (except for 8800) has VDPAU support, for video decoding acceleration.

---

### Post by techiefox on 2010-03-06
> **3rdalbum said:**
> DVI can carry digital AND analog signals, so graphics cards usually come with an adapter that converts the DVI out into a VGA out. That is, unless they have a VGA (D-SUB) connector on the back; I've seen 8400GS' with a VGA connector. Not all of them will have, but if not they should have that adapter. Obviously, check for this when buying off eBay as some people might have lost the adapter.

It looks like the 8400 powers itself off the PCI-E bus, so as long as your power supply isn't currently drawing close to its limits you should be fine. It doesn't need any extra power connectors going straight to the card. FYI I used to have a PCI-E-powered 8600, so if you wanted some extra performance this would be a good way to go too.

I agree with an earlier poster who said not to buy too old a card. The 8000 series is the oldest I'd recommend. Anything earlier and you're looking at ancient drivers that will probably require you to edit your xorg.conf file. Also, the 8000 series (except for 8800) has VDPAU support, for video decoding acceleration.

So based on your guys experience is that a decent card ?

---

### Post by jim Kane on 2010-03-07
> **techiefox said:**
> Does that card work with a vga monitor ? Also will that card require a new power suppy?

                                       Yes the 8400GS comes in a few variants all (i think) have D-sub vga
    [LEFT]mine has D-sub DVI and S-VID outputs, it runs from the PCI-E slot without need of an extra power connector.[/LEFT]
    [LEFT]And works 100% out of the box on *buntu all you have to do is click install driver under, system>hardware drivers. 



Jk
[/LEFT]

---

### Post by techiefox on 2010-03-08
> **jim Kane said:**
> Yes the 8400GS comes in a few variants all (i think) have D-sub vga
    [LEFT]mine has D-sub DVI and S-VID outputs, it runs from the PCI-E slot without need of an extra power connector.[/LEFT]
    [LEFT]And works 100% out of the box on *buntu all you have to do is click install driver under, system>hardware drivers. 



Jk
[/LEFT]




Cool that sound really simple , thanks

---

