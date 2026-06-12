---
title: "wifi card for laptop: Getting rid of broadcom..."
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by miesnerd on 2008-02-13
Im starting to get really sick of having to stick with certain distros which are not my favorite in order to get my broadcom hard to half work (works sometimes; always at reduced speeds). Ive decided that if Broadcom wont work with linux, I wont work with them. 
I know there are pricy cards made by companies which work exclusively with linux, but quite frankly, I want to as cheap as possible get away from Broadcom. I mean this nicely: screw them.

I have a Gateway MX6421 laptop :
[http://support.gateway.com/s/Mobile/Q106/Blade/5956sp2.shtml](http://support.gateway.com/s/Mobile/Q106/Blade/5956sp2.shtml) 

I saw this card:
[http://www.oxfordtec.com/us/product_info.php?products_id=106&language=en&cPath=41&source=googlebase](http://www.oxfordtec.com/us/product_info.php?products_id=106&language=en&cPath=41&source=googlebase)

Says it has an atheros chipset, so I assume it will fit/work.

What im looking to check is a) will it fit and work, and b) how hard is it to replace a laptop's wifi card. I know where the card is, but do I have to do any soldering?
Can I sell my broadcom card to rid myself of that horrid thing?
Any other pertinent advice?
 To me, its well worth 30 bucks to get a card that opens up the capabilities of my llaptop.

---

### Post by Hightide on 2008-02-13
HI miesnerd

have a look at the Ubuntu [wiki]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") for supported wireless cards first if you haven't already so. Its  a good knowledge source.

regards

:)

---

### Post by tturrisi on 2008-02-13
First:
Open the laptop and see it the wifi is mini-pci or mini-pci-express.  (pci-e is about 1.25" x 2" and pci is about 1.75" x 2")
If need mini-pci get this one:
[http://www.oxfordtec.com/us/p112/GIGABYTE-WI01HT-Wireless-miniPCI-card--Atheros-AR5006XS-Super-AG-single-chip-AR5414-108Mbps-mini-PCI-adapter/product_info.html](http://www.oxfordtec.com/us/p112/GIGABYTE-WI01HT-Wireless-miniPCI-card--Atheros-AR5006XS-Super-AG-single-chip-AR5414-108Mbps-mini-PCI-adapter/product_info.html)
If need mini-pci-e get this one:
[http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless/c42/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mPCIe-adapter/product_info.html](http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless/c42/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mPCIe-adapter/product_info.html)

I replaced the broadcom in my Dell with the pci-e model above and it's great.  Works w/ madwifi drivers, no problems ever.

No soldering necessary.  The antenna leads snap on-off the card.
Make sure they snap on tightly.
t's wise to place a small piece of elec tape on top to ensure they stay intact when mobile.

---

### Post by sharpycore on 2008-02-13
I'd like to jump on this thread. I'm sick of not being able to use aircrack or encryption so I'd like to ditch broadcom. I looked through the supported wireless cards list but it was a little bit cryptic. I was wondering if anyone running 64bit gutsy could say if they have a mini pci card that they know works for certain out of the box?
Thanks

---

### Post by miesnerd on 2008-02-13
sharpy-
I'll let ya know when I do it. I have 64 bit ubuntu installed on both my desktop and laptop. Sometimes, my broadcom card will work (after using Darknoob's fix) and sometimes it just wont. Darknoob did a good job with his deal, but broadcom is the dumb. The more and more "linux-centric" i get, the more and more I've decided that I dont want something that's "vista compatible" All that means to me is that you set up support for idiots. Great for you, now make hardware that intelligent people can configure and get to work to its potential.

---

### Post by miesnerd on 2008-02-13
I found this:
[http://www.notebookparts.com/products/description.php?II=13478](http://www.notebookparts.com/products/description.php?II=13478)
meaning that since a mini pci (not pci-e) is sold to fix the MX6421 (my model) i should be fine.
Actually, after looking at gateway's documentation it looks like my laptop might support either mini pci or pci-e.
[http://support.gateway.com/s/Mobile/Q106/Blade/8511418.pdf](http://support.gateway.com/s/Mobile/Q106/Blade/8511418.pdf)

But i doubt that's the case. Considering that its an old, cheap laptop at this point, im fairly certain its mini pci.

---

### Post by tturrisi on 2008-02-14
> **miesnerd said:**
> I found this:
[http://www.notebookparts.com/products/description.php?II=13478](http://www.notebookparts.com/products/description.php?II=13478)
meaning that since a mini pci (not pci-e) is sold to fix the MX6421 (my model) i should be fine.
Actually, after looking at gateway's documentation it looks like my laptop might support either mini pci or pci-e.
[http://support.gateway.com/s/Mobile/Q106/Blade/8511418.pdf](http://support.gateway.com/s/Mobile/Q106/Blade/8511418.pdf)

But i doubt that's the case. Considering that its an old, cheap laptop at this point, im fairly certain its mini pci.

Just take off the cover plate and LOOK at the card.  If it's bigger than 1.25" wide then it's a mini-pci.  If the width is about 1.25" than it's a mini-pci-e.

---

### Post by sharpycore on 2008-02-20
> **miesnerd said:**
> sharpy-
I'll let ya know when I do it. I have 64 bit ubuntu installed on both my desktop and laptop. Sometimes, my broadcom card will work (after using Darknoob's fix) and sometimes it just wont. Darknoob did a good job with his deal, but broadcom is the dumb. The more and more "linux-centric" i get, the more and more I've decided that I dont want something that's "vista compatible" All that means to me is that you set up support for idiots. Great for you, now make hardware that intelligent people can configure and get to work to its potential.

I PMed you, but for the thread... I went ahead and got an Intel 2915 mini pci card. Works instantly with 64 bit Gutsy. Well worth doing.

---

