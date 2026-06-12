---
title: "Wireless networking not working"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by andypaxo on 2005-10-13
I have recently installed Hoary Hedgehog, and everything works fine except the wireless.
My card is a Safecom SWLPT-54108 (Cheap and nasty TI ACX111 PCI card). Hoary seemed to detect it on installation, but I have never managed to connect to the network.

I have tried [Craig's ACX guide]("http://www.houseofcraig.net/acx100_howto.php"), but had trouble with that; The script stops at the DCHP part, and using a predefined IP doesn't seem to work.

I have also looked at using [ndiswrapper]("http://ndiswrapper.sourceforge.net/"), but all the tutorials for this seem to involve apt-getting loads of packages (parts of ndis, kernel sources, gcc and goodness knows what else)
I don't know what these people use their wireless networks for, but I need it working in order to get on the internet, so apt-get is out.

If anyone can help me to get this set up, I would be most grateful. Failing that, could you point me to a wireless card that will work first time in Ubuntu?
Thanks in advance!

---

### Post by dotdot on 2005-10-13
ok (not being an export here on this..).

first off get a hold of ndiswrapper, it's ok ! , no need to download etc.
start up synaptic installer under admin on the panel at the top.
now when it starts up ...do a search for ndiswrapper.
select for install then .. install - have your cd handy.

.. now once youve installed it you need to get a hold of your drivers for the card you have ie the one which 'would work' under windows.
.. now get these onto your pc.... then use ndiswrapper to pick them up.

.. the rest is covered here.
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

.. have fun :)

---

### Post by andypaxo on 2005-10-14
Thank you very much for your help. I'm new to Linux and wasn't familiar with Synaptic.
I have now installed ndiswrapper with the hardware for my wireless card. Unfortunately, I still can't get onto my network; "iwlist scan" says "no scan results" and dhclient is stumped as well.

Hopefully some more digging around may turn up some answers, but it does seem like a lot of work :???:
Once again, cheers for the advice!

---

### Post by hamil on 2005-11-17
Seems that you did not get any further on your acx-100 wlan??

I found a post in this forums, with a link to this wikipage. It looks as this has solved my problem with my acx card. Maybe it is of your interest as well??

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29")

---

### Post by andypaxo on 2005-11-17
Thanks for the pointer!
Unfortunately, since my last post my network card has died completly and the BIOS won't boot when it is in the system (which should teach me not to buy cheap nasty hardware). I'll certainly keep ndiswrapper in mind when installing a new card though.

By the way, have you ever heard of any cards that are assured Linux compatibility? It seems there are a few "might work first time - might not if they have changed the chipset", but none which are guaranteed to work with no messing.

---

### Post by hamil on 2005-12-10
Well, if you look on this page:
[Linux-WLAN]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz")

They have listed diffrent cards, and commented those who are tested and working with Linux-wlan-ng

---

