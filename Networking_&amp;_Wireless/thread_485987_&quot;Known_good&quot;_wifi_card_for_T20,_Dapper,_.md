---
title: "&quot;Known good&quot; wifi card for T20, Dapper, Edgy, Feisty"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by mattotoole on 2007-06-27
I'm using an IBM T20 with a Linksys WPC11 wifi card.  I'm still running Breezy because I can't get this card to work with Dapper, Edgy, or Feisty.  Instead of spending hours and hours of my precious time trying to get this card to work, I'd rather just spend $25-50 for a new one that does.  Any suggestions?

I've looked at the compatibility lists in the Wiki, etc.  This information is sketchy and incomplete, because results vary with each model/version of laptop, version of card, and version of Ubuntu, and not all of this is listed.

So I'm looking for real-world reports.  

Any suggestions?

---

### Post by t4thfavor on 2007-06-27
easy answer: Cisco CB21AG.
Slightly harder answer:Anything with atheros chipset.
Slightly more harder answer: If you have internal Mini PCI slot I have had good luck with Intel cards. But you have to make sure that the IBM will allow you to install third party wireless cards.


As of now don't get prismGT cards, they are broken in the current kernel.

---

### Post by p_quarles on 2007-06-27
Like t4thfavor said, Intel cards work well. I use a PRO/Wireless 3945ABG, and it worked right out of the box.

---

### Post by Niomi on 2007-06-27
Are you installing Dapper, Edgy or Fiesty or upgrading to them from Breezy?

I had trouble with a wireless card in a laptop which worked in Breezy but not in Dapper. (the laptop was stolen shortly after my upgrade to Edgy) A fresh install of Dapper didn't reconise the wireless card. Breezy picked it up right out of the box and would continue to do so if I upgraded Breezy to Dapper.

---

### Post by ljonesj on 2007-06-27
i was wondering this also i want a good card that lets kismet and aircrack-ng work my laptop is a 1.6ghz amd turion processor 80gig hardrive a dvdburner dual layer the version of this laptop is compaq v2000 more specific 2410us it has a broadcom 4318 built in wireless card which suckes for the stuff i need to do i am a network manager partime for a doc and sometimes i misplace stuff which bad but i need to check on the strength of the encyrption we use at the his home and offices and broadcom does not let me do that i still need windows for certain things i have but i need the dual boot option of ubuntu for this type of work any help would be great

---

### Post by ljonesj on 2007-06-27
does the linksys WUSB54G work and what version works the best and does kismet and aircrack work with it

---

### Post by t4thfavor on 2007-06-27
as far as I know nothing USB works well with aircrack. I know prism GT stuff used to work quite well with it, but not anymore. 

I still stand by the Cisco card (Atheros) it can inject as well as capture, and you can have multiple "vaps" that will allow you to surf wirelessly while you are cracking.
The intel cards only work with intel cpu's and the 3945 cards are mini pci express, and not miniPCI.

for a miniPCI intel card you will need 2200B/G or a 2915A/B/G card.

EDIT: The intel cards don't do injection very well.

---

