---
title: "wireless"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by jlott on 2009-07-09
Hi

I have a acer aspire one netbook running ubuntu 9.04 which i have just installed. I am trying to get the wireless to work and the icon for wireless is there but when i click on it so select wireless network. it says it is disconected. Please help

Many thanks

Joseph

---

### Post by LewRockwell on 2009-07-09
> **LewRockwell said:**
> I've got an Acer Aspire One AOA-150-1864 which has the Atom N270(1.6GHz) 1GB ram 120GB HDD and the Dell Wireless 1390 WLAN Mini-Card

Right now it's triple-booting XP Professional SP3, Ubuntu 9.04 Jaunty(full version...not the UNR), and Puppy Linux 4.2.1 and I've got five more logical partitions for five more *nix distros
(wireless works fine with all three current OSes)

Pros: small, lightweight, minimal power consumption, will drive large external video devices via vga output(separate audio output requires additional wiring/equipment knowledge as opposed to "plug and play")

Cons: 8.9inch screen is too small for my tastes, no optical drive(you don't realize how much you enjoyed it til it's not there anymore), no advanced video output connections(only a serial vga port)

I only have this one because I got a good deal on it

If I were making a new purchase I would definitely stick with a full-size laptop for the obvious reasons(bigger screen, optical burner, better sound)

.

Pro-tip: Better titles get more and more relevant responses

The title may be edited by editing your thread's first post title area

.

---

### Post by nothingspecial on 2009-07-10
First things first, get a wired connection and do your updates if you haven`t already.

If that doesn`t fix it then there are a couple of things you can try.

I take it this is an atheros wireless card. To check, open up a terminal and type ```
sudo lshw -C network
```.

Near the top there should be an entry something like

```
product: AR242x 802.11abg Wireless Pci Express Adapter
```

If it`s not ignore the rest of this and post what card you do have ie what it says instead. If it is that card then in your menus go to system > administration > hardware drivers and you should have the option of changing to Alternate atheros madwifi driver. Try that.

Reboot and if that doesn`t work post back.

---

### Post by Peter09 on 2009-07-10
Good place to look.

[http://www.aspireoneuser.com/forum/](http://www.aspireoneuser.com/forum/)

---

### Post by superprash2003 on 2009-07-10
post output of
1)iwconfig
2)sudo iwlist scanning

---

