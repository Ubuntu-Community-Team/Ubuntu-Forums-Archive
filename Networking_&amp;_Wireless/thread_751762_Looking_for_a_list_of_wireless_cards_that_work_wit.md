---
title: "Looking for a list of wireless cards that work with kismet?"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by thenetduck on 2008-04-10
Hey I am am going to buy a T or R series IBM Laptop and I trying to make sure I get a wireless card that will work great with Kismet. Does anyone know where I would find a list of cards that will work with kismet? 

The Net Duck

---

### Post by chili555 on 2008-04-10
I don't know where there might be a list, however I use kismet successfully on my T60 running an Intel 3945.  [http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_3945ABG_Mini-PCI_Express_Adapter](http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_3945ABG_Mini-PCI_Express_Adapter)

---

### Post by thenetduck on 2008-04-11
Great thanks,

If anyone else is reading this that has a Think Pad running Intel Wireless WiFi Link 4965AGN card, are you able to run kismet with it? 

I like the idea of being able to run on an n based network. 

The Net Duck

[edit]
Ok it looks like it still used the Iwl4965 (same as the abg card) so it should work with the new card aswell. 

Question to chili555: Are you using Iwl4965 or ndiswrapper? For your wireless card? 

Thanks a bunch!

The Net Duck

---

### Post by Junglizer on 2008-04-11
> **thenetduck said:**
> it]
Ok it looks like it still used the Iwl4965 (same as the abg card) so it should work with the new card aswell. 

Question to chili555: Are you using Iwl4965 or ndiswrapper? For your wireless card? 

Thanks a bunch!

The Net Duck

This would probably have to be the Iwl4965 driver, you cannot put a card into monitor (rfmon mode) using ndiswrapper.

---

### Post by Junglizer on 2008-04-11
Also, in response to your original question, you can at least find the supported capture sources at the Kismet site: [http://www.kismetwireless.net/documentation.shtml]("http://www.kismetwireless.net/documentation.shtml")

---

### Post by chili555 on 2008-04-11
> Question to chili555: Are you using Iwl4965 or ndiswrapper? For your wireless card?
I am using ipw3945.I have tried iwl3945 and, for me, they work equally well, except the wireless LED doesn't light under iwl3945.

My 3945 has worked perfectly since minute one with my T60. I am not doing file transfers or streaming HD video to my laptop that would require 802.11n.

---

