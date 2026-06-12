---
title: "Possible solution for network problems"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by VanDu on 2008-11-15
I, as many others have a problem with network in Ubuntu 8.10. DHCP, not working, manual entering of address didn't work as well. I was following [[COLOR="Red"]THIS[/COLOR]]("http://ubuntuforums.org/showthread.php?t=963335") thread closely, but none of a workaround solutions mentioned there didn't work for me.
I am dual booting with XP and everything is just fine there. So, faulty hardware was out of the question. 
I have a PCI Realtek 8139 NIC and that's the one i am using. But i have an onboard card as well, also Realtek 8139, but that one i was never using. Last night, just to test something, i plugged the network cable in to onboard card, and voila... internet came instantly. I suspected that there might be some conflict with cards, and tried to find out what could it be, but nothing similar existed on the web. Anyway... I went back to windows and enabled the onboard card, and disabled the PCI card. I updated the drivers for onboard one, becasue there are more settings after driver update for the card itself. And then, i booted ubuntu, and you can imagine my surprise... NO NETWORK AGAIN!:confused::confused::confused:   
And then i suspected on something I think it should be impossible. Can it be that when I update the drivers under WinXP, it messes up the card under ubuntu??? Well, yes it can!
I went back to Win again, rolled back drivers to old ones (default Win drivers, dated from 2001) and net was working again under ubuntu. I did the same for PCI card, just uninstalled it from device manager and installed the default drivers, and card is working now in ubuntu as well.
So, my question is... Is it possible that Win drivers could have any kind of influence on Ubuntu? :confused::confused::confused:

Can somebody else, who have a similar problem, try what I did to confirm this?

---

### Post by dino99 on 2008-11-17
very strange and unbeliavable : each os take care of hardware, there is no relation between them.
i wonder about modules boot order with intrepid kernel

---

### Post by jnorthr on 2008-11-17
assuming you reboot into each different o/s, it would seem unlikely that one o/s would load firmware into a network card which could NOT be over-written when you boot into the alternate o/s. But if this IS the case, you could try to physically power off your system as part of the reboot process - cos that would surely erase any lingering firmware that's installed by the 'previous' o/s.

---

