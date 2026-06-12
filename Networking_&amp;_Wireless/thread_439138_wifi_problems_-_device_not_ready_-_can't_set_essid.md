---
title: "wifi problems - device not ready - can't set essid -workaround"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by gypsy_roadhog on 2007-05-10
A lot of people seem to be having problems with wifi. My netgear WG311v1 pci card worked fine after upgrading to feisty - until I tried to change the configuration to wpa. After that nothing would help, even a complete re-installation of feisty.

The card accepted most settings through iwconfig (eg wep key etc) but would not accept any essid values (even though iwevent suggested that the essid had been accepted). Dmesg kept on reporting wlan0 device ready.

As I'd changed everything else with no effect I reasoned the problem must be some setting held within the card itself....... So I re-installed XP on a spare corner of the pc. I then configured the card with the windows setup program provided by netgear. This worked fine and I had a working connection again.

Better still whatever had been reset was retained and the card is now working back under my favoured OS, Ubuntu.

This workaround is very clumsy but could be helpful if you have a dual boot machine - or indeed access to a windows pc.

It must also give some clues to the system maintainers - I guess that ndiswrapper is either not trying to initialise the card completely, or is not recognising that the initialsiation has failed?

Hope this helps someone!  Neil

---

