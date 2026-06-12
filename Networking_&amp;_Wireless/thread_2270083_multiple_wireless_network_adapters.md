---
title: "multiple wireless network adapters"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by msquito on 2015-03-20
Okay - first, new with linux so please be gentle...
I've been reading for a couple days and tinkering but have had no luck solving my issue so here goes plea for help...

14.04 LTS on a Lenovo Yoga 2 Pro.  Y2P has an intel 7260 internal wireless card, works like a champ.  I recently purchased a TP-Link TL-WN722N USB nic with Atheros AR9271 chipset.  Upon plugging in TPL for first time, it lit-up and both of the interfaces showed up within the network manager aplet although I was unable to get internet connectivity through the TP-Link nic.  In my eagerness to get the second nic to work, I downloaded latest backports and made/installed driver for TP-Link nic.  This dropped the Intel nic out of the network manager entirely and I still didn't have connectivity with the TPL.  I managed to figure out how to get the iwlwifi driver made/installed and then I was back in business with the intel nic (seems like it might be a little less stable than before but I could be imagining that) and now the TPL nic has dissappeared.  I've cycled through this twice, played with editing the the interfaces file with no luck, can't get both interfaces to read using 'ifconfig -a' (although I can get one or the other depending upon which driver I've most recently installed).  With active intel nic, I can get the TPL to register using 'lsusb' but it doesn't light-up or give me any options to interact with it.  
In a perfect world, I'd default to the intel nic unless the TPL were plugged in then that would trump.  I'm fine with turning intel down or deactivating in network manager manually but I can't even get both nics to regiister any more!?  I've checked the 'rfkill list' and I'm not blocked but I'm only showing a single wireless interface (there's bluetooth there and its showing as soft-blocked but that is as it should-be).  Given I'm new to linux I'd just as soon use the network manager for both if that is an option although I am certainly becoming more comfortable with the terminal with all the tinkering in the last couple days...

any help super-appreciated
tia

---

