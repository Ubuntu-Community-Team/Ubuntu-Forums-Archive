---
title: "disappearing onboard ethernet adapter on shutdown!?"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by L0wInF4t on 2007-04-16
Hi

I'm only a week old with linux Ubuntu(6.10). A week of learning...

There's one problem I didn't got to solve...

When i shutdown ubuntu and reboot my onboard ethernet card is disable and nowhere to be found (even in the bios).

my way around:

the way I use, even tho is really anoying, before I boot up, i have to remove the jumper from my motherboard to clear Cmos memory, then my onboard ethernet reappear into bios setting and my connection works fine.

anyone have seen that issue before?
any help!?

Thank you

---

### Post by jglen490 on 2007-04-16
Maybe some details about your hardware such as the name and model of the wifi card, its connection type, what it shows up as in the BIOS might be helpful.

---

### Post by L0wInF4t on 2007-04-17
my motherboard is: ecs P4M800PRO-M (V2.0)
ethernet chipset: VIA® VT6103L 10/100

what shows up into the bios?
If i erase the cmos to have a fresh bios it shows up in feature: onboard lan: enable
and when I reboot without erasing the cmos that feature doesn't show up anymore and network is disable.

It's not wifi... it's wired...
I don't know what else could be usefull...:confused:

---

### Post by L0wInF4t on 2007-04-18
24h bump

---

### Post by mekaj on 2007-04-22
I'm experiencing the same problem in Feisty Fawn.  I have the same motherboard and I'm also using the integrated ethernet.

If I do a CMOS clear using the jumper settings in the same way that L0wInF4t described, BIOS acknowledges my ethernet.  More specifically, in the Features Setup submenu in BIOS there is a line that says Onboard LAN (enabled) and the next line is indented and says Onboard LAN boot ROM (disabled).  The second option setting doesn't have any on this problem.  After a reboot or shutdown without a CMOS clear, these two options disappear for no obvious reason.  Any suggestions?  Thanks.

---

### Post by kevinlyfellow on 2007-05-06
> **L0wInF4t said:**
> my motherboard is: ecs P4M800PRO-M (V2.0)
ethernet chipset: VIA® VT6103L 10/100

what shows up into the bios?
If i erase the cmos to have a fresh bios it shows up in feature: onboard lan: enable
and when I reboot without erasing the cmos that feature doesn't show up anymore and network is disable.

It's not wifi... it's wired...
I don't know what else could be usefull...:confused:

I was installing debian on a couple of these motherboards and was having nic issues.  I solved it by upgrading the bios.  [http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=673&DetailName=Bios&MenuID=1&LanID=9](http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=673&DetailName=Bios&MenuID=1&LanID=9)

If you need help, let me know

---

