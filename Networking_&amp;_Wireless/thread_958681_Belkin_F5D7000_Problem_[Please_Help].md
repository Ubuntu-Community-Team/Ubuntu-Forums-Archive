---
title: "Belkin F5D7000 Problem [Please Help]"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by SerenityKill3r on 2008-10-25
hey guys,

just installed my card drivers via ndiswrapper, and the card is installed, theres a flashing orange light on the back, but no wireless connections are showing up in the network manager :(

If I click on it, it says wired network, but its greyed out and Wireless Networks, but theres no connections listed..

Thanks for any help,

Chris

---

### Post by SerenityKill3r on 2008-10-25
anyone? I need help quick :(

---

### Post by Steve1961 on 2008-10-25
> **SerenityKill3r said:**
> anyone? I need help quick :(

Which chipset does your card have?  I know Belkin have a tendency to change chipsets all the time.  To find out just post the relevant output from this command:

lspci -v

One of the f5d7000 cards has a ralink rt2500 chipset so you wont need ndiswrapper is that's the case.  Also, if you do need ndiswrapper have you loaded the module (modprobe ndiswrapper)?

---

### Post by SerenityKill3r on 2008-10-25
Its the Realtek 8185 chipset IIRC...I've tried both the Belkin and Realtek drivers to no effect...It recognises the wireless card, wlan0 is showing up in iwconfig/ifconfig but it will not let me connect to any networks...

---

### Post by Steve1961 on 2008-10-25
This link might be useful:

[http://www.willdaniels.co.uk/articles/howto-guides/10-howto/15-rtl8180-hardy](http://www.willdaniels.co.uk/articles/howto-guides/10-howto/15-rtl8180-hardy)

Oops, sorry, I've just spotted that this is for an 8180 and not 8185, although it could still be useful

---

