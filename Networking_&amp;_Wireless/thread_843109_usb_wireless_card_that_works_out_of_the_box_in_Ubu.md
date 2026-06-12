---
title: "usb wireless card that works out of the box in Ubuntu 8.04"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by agel1 on 2008-06-28
can somebody recommend a cheap (usb wireless card that works out of the box in Ubuntu 8.04)

thanks

---

### Post by ModelM on 2008-06-28
In Ubuntu Hardy I successfully got a Zonet ZEW2502 working using ndiswrapper & the Windows driver. It was a snap getting it to work. I was unable to enable WPA-PSK encryption, however.

---

### Post by agel1 on 2008-06-28
> **ModelM said:**
> In Ubuntu Hardy I successfully got a Zonet ZEW2502 working using ndiswrapper & the Windows driver. It was a snap getting it to work. I was unable to enable WPA-PSK encryption, however.i want one with linux drivers, ndiswrapper is problematic

thanks

---

### Post by Lupgaru on 2008-06-28
This is the only one that I have had work after install on first boot. It's the LINKSYS Compact Wireless-G USB Adapter Model # WUSB54GC, FCC ID:Q87-WUSB54GC, IC; 3839A-WUSB54GC. Available from Amazon.com for less than$50. Don't get the Model with Speed Booster, driver not compatible(yet). It's worked for me on 2 laptops(Thinkpad and Acer) and 3 Desktops(Dell 1100, IBM, Custom Gaming Tower).

---

### Post by agel1 on 2008-06-28
> **Lupgaru said:**
> This is the only one that I have had work after install on first boot. It's the LINKSYS Compact Wireless-G USB Adapter Model # WUSB54GC, FCC ID:Q87-WUSB54GC, IC; 3839A-WUSB54GC. Available from Amazon.com for less than$50. Don't get the Model with Speed Booster, driver not compatible(yet). It's worked for me on 2 laptops(Thinkpad and Acer) and 3 Desktops(Dell 1100, IBM, Custom Gaming Tower).thanks

---

### Post by agel1 on 2008-06-29
this (WUSB54GC) cost 50 in tiger direct, if any of you know other usb card that work out of the box in Ubuntu 8.04 that isn't so expensive let me know

thanks

---

### Post by 714snoopy on 2008-06-30
> **agel1 said:**
> this (WUSB54GC) cost 50 in tiger direct, if any of you know other usb card that work out of the box in Ubuntu 8.04 that isn't so expensive let me know

thanks
How about $40 at Micro Center for the WUSB54GC?

[http://www.microcenter.com/single_product_results.phtml?product_id=0235428](http://www.microcenter.com/single_product_results.phtml?product_id=0235428)

---

### Post by Djeez2 on 2008-07-01
I have been messing with ndiswrappers for a year (no success) to get my wusb54gc to work. I am surprised that with 8.04 (to which I upgraded recently) it should work out of the box. Is there a way to get back to the original situation without completely reinstalling Ubuntu?

Thanks!

Djeez.

---

### Post by hajk on 2008-07-01
The WUSB54GC has a Ralink chipset for which there has recently been a driver, rt73usb, added to the kernel (>= 2.6.24). Mind you, this driver (and others in the rt2x00 suite of drivers) should still be considered of beta quality. One of the problems with the rt73usb driver is low speed; it may help to upgrade to a 2.6.25 kernel through backports if/when available.

I don't know what you mean by "getting back to the original sutuation..", you want to get back to messing with ndiswrapper? May be you mean getting back to the "legacy" Ralink drivers at SerialMonkey -- that's a possibility, though these legacy drivers are no longer actively developed, in favour of the rt2x00 ones mentioned before. 

For all of you struggling with Linux wireless drivers and ndiswrapper, you should also check out the possibility of using a wireless bridge (like the Linksys WET54G), which plugs into an Ethernet port of your computer. About the same price as a wireless adapter, slightly larger (about the size of a package of cigarettes), and no Linux wireless driver needed.

---

### Post by Tomatz on 2008-07-01
Belkin fd7050

---

### Post by Djeez2 on 2008-07-01
> **hajk said:**
> I don't know what you mean by "getting back to the original sutuation.."

What I mean is that over the year I have been experimenting with a lot of tips and scripts I found on the 'net and several people had an attempt on getting the thing to work. So I think the situation on my laptop is probably messed up.

What I am trying to do now is start from the Live CD. If I unplug the usb stick and plug it in again I get at least the Wireless Network menu, and I can "connect to other wireless network", using WPA, but no connection is established.

I give up (again). The thing I learned from this thread is that I should not go out and buy a new adapter that "works out of the box". (That is how I found this thread).

Anyway, thanks for your reply.

Djeez.

---

### Post by agel1 on 2008-07-05
i reset my router and (netgear wg311v3) is working with (wpa) in (ndiswrapper) the only thing i change in my router settings was the name of the wireless network, previous name was too long

thanks

---

### Post by Wheel_nut on 2008-07-05
I have a TP-Link TL-WN322G USB Adapter which works out of the box ... even on my ThinkPad X21 which is USB 1.1.

It cost me £6-49 from SVP.co.uk. 

Just plug it in and enter the WPA Key and it flies!

---

### Post by Efros on 2008-09-05
As a previous poster has said Belkin f5d7050, works very well, I have used it on a linksys router network, an apple airport network and also a rosewill network with no issues.

---

### Post by Michl on 2008-09-19
The WUSB54GC works out of the box on some equipment
not others.  For example, on Dell 221 and a Dell
laptop., immediately.  But a Dell GX280 has
problems with the usb and there it doesn't work,
not even in windows.

---

