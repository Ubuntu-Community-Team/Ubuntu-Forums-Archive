---
title: "RTL8211 network device doesnt work?"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by megadodo on 2006-12-16
Hi

Ive recently built a PC (from what i believed were linux friendly components, it never occured to me that a wired network device wouldnt just work straight out the box!)
The motherboard is a Gigabyte GA-M61PM-S2 which has an onboard network device RTL8211 according to the manual. 

eth0 does not appear in the network settings and running ifup eth0 results in "device not found errors".

Ive installed linux on lots of different desktops and laptops, but i have never come across this before. Maybe i was just lucky in the past.

(I also have a RT61 wireless card, chosen especially because i read that it worked in linux only to find out it is broken in edgy for some unknown reason. To fix this requires downloading and installing and compiling and praying and other such activities which is hard to do with no internet connection...)

Any ideas how to make this work?
Thanks,
Richard

---

### Post by ajole on 2006-12-18
Me too.  I can't find anything anywhere that indicates what the problem is.  I do know that Gigabyte refers you to the manufacturer for Linux drivers, but I'm not sure it is a driver issue; as you say, it's not that it doesn't work, Edgy can't even see the thing, though WinXP MC runs it fine!
I have contacted Realtek support, but am still waiting for a reply (its only been an hour)
if I get a reply, I'll post here again.
Good luck!

---

### Post by megadodo on 2006-12-30
I also emailed them and received this reply:
> Dear Customer
Thanks for your Email.
RTL8211 is a PHYceiver which is a driverless hardware device.
Software / Driver are relative to Network controller ( MAC ) which is
integrated into chipset in such case mostly.
Please contact your mother board maker or chipset manufacturer to obtain
proper driver support.
Regards & Thanks for choosing our product.
Ryan Kao
Tech Support, Realtek

That mumbo jumbo doesn't mean anything to me, but the general gist i think is to contact the motherboard manufacturer (which in my case is Gigabyte [GA-M61PM-S2])
However I got bored waiting for the reply and bought a cheapo PCI network card that works fine, so i will see if i get round to emailing them.

Richard

---

### Post by betchern0t on 2007-01-04
This motherboard uses the nvidia 430 chipset. The gigabit ethernet card is implemented in two halves - my interpretation anyway - one is the PHY chip (8211) and the other is in the 430. You need the drivers for the 430 chipset. This is the forcedeth driver. However support for the 430 chipset is not included in the kernel until 2.6.18 and edgy uses 2.6.17.10. 

I upgraded my kernel to 2.6.19.1 and the card began working. Checkout 

[http://ubuntuforums.org/showthread.php?p=1965557#post1965557](http://ubuntuforums.org/showthread.php?p=1965557#post1965557)

Cheers Paul

---

