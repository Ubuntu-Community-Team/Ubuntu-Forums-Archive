---
title: "BCM4318 wireless card on ubuntu 8.10 laptop"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Riqz on 2008-11-07
I have an Asus A6K laptop with a broadcom 4318 wireless card.
You can imagine the nightmare i'm facing.

I have roamed the net, the forums, the howto's the troubleshooting. But i just cannot seem to make the card work.

The driver is properly installed on ndiswrapper. The thing is that my wlan0 doesnt exist. 
It reads the broadcom card as PCI and uses a driver called B43-pci-bridge. I have blacklisted everything even b44.

By playing around yesterday (using all the info on troubleshooting) i finally managed to get the card unassigned by doing -rmmode b34, b44, ssd, etc and then assiging ndiswrapper but it gives me errors as if the driver isnt liked by ndiswrapper. This happened using the bcmwl5.inf. It was downloaded from Broadcom webby so shud be legit.

The laptop reboots and i can see the wireless light on the laptop on for a few seconds (i guess its the bios turning it on) but when i enter Ubuntu it turns off completely.

When i scan for access points from terminal it says my pc has no scanning devices. 

I really have no idea how to go on now... Been trying for the past week. It really is a nightmare.

P.S. I will post code after i get home from work.
Just preparing you all for an epic tale of wireless networking.

Thanks in advance

---

### Post by Riqz on 2008-11-07
forum sure is moving fast today.
Little bump

---

### Post by krazykookmany on 2008-11-10
//

---

