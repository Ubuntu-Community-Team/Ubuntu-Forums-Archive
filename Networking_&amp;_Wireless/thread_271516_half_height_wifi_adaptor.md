---
title: "half height wifi adaptor?"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by crispy_420 on 2006-10-04
Does anyone know of a pci wireless network adaptor that works well with dapper?

What I'm looking for should meet these requirements:

atleast 54mbs
have a half height adaptor for slim PC
native dapper/linux support (no ndiswrapper perferably)
pci (no USB)
works with network-manager (want to avoid rt2500 if possible)

Sounds pretty demanding right? In simple terms:

wireless g
half height
supported chipset

I've seen a few that may meet my needs but they are off brands or rebranded so finding their chipsets is near impossible.

Any help out there?

---

### Post by Patrick-Ruff on 2006-10-04
you could look around Ebay, theres often good wireless cards for cheap prices ;).

hell, I bought an Atheros MiniPCI card off of ebay, works very very very well :)


good luck.

---

### Post by crispy_420 on 2006-10-05
I found one I think:

[HERE]("http://www.gigabyte-usa.com/Products/Communication/Products_Spec.aspx?ProductID=970&ProductName=GN-WP01GS")
 
Anyone try/have this card?

---

### Post by Titus A Duxass on 2006-10-05
I have an Edimax EW7126 (RTL8180 chipset) which is half height and Link Sys card (forgotten which and it's at home) which is also half height.

Both work OTB with Dapper.

---

### Post by sadsac on 2006-10-05
The gigabyte model you referred to uses a ralink chipset. I've had better performance with the atheros chipset. Some decent atheros pci adapters are the Planet WL-8310, or the Edimax EW-7325IG.

---

### Post by crispy_420 on 2006-10-05
Not much luck searching for any of those.

Edimax EW7126 = only found sites in czech republic 
Planet WL-8310 = does not include half height adaptor
Edimax EW-7325IG = also no half height adaptor included

This is why I'm leaning toward the gigabyte one. It has al the parts I need in one package. It doesn't hurt that I can order it for around $25(US). About RaLink chipset, I'm not concerned with speed and performance. I had a RaLink in my laptop (to an atheros) and the only reason I switched out was incompatibility with networkmanager. This card will be used in a stationary system (mythtv build).

The rt2500 chipset is even recommended by the Free Software Foundation. [URL="https://www.fsf.org/resources/hw/net/wireless/cards.html"]HERE
[/URL]

Any other ideas. Maybe even some links to purchase?

---

### Post by sadsac on 2006-10-05
Actually I'm using the Edimax EW-7325IG now with a half height card slot cover I borrowed from a video card. I punched three holes (for the antenna connector and two LEDs) and it looks perfect. If you have trouble finding a suitable card you may want to just fashion a half height slot card cover yourself.

---

