---
title: "enabling a desktop wireless card"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by Lonnie12 on 2007-08-27
I have a netgear wireless card  it is wg311 network card. how do you enable it please put it in simple terms I dont understand linux very well.

Thanks Lonnie

---

### Post by bmartin on 2007-08-30
Unfortunately, it's not simple. According to [this page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear"), you probably have one of two chipsets (the chipset will determine how you can get it to work):
[LIST]
[*]One with an Atheros chipset
[*]One with a Texas Instruments chipset
[/LIST]
If you go to System > Administration > Network, does it show a wireless connection? If so, click on the Properties button and set the settings as appropriate.

If not, we'll have to do some more work. Open up a terminal and type **lspci**. Look for a line that relates to a network device, specifically a wireless device. Paste the line in here and I'll tell you the next step.

---

### Post by katsikaki!!! on 2008-01-05
i have installed the appropriate drivers for this card but linux still cannot find my wireless card. it says: "Hardware present: no". what should i do??? plz someone

---

