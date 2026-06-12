---
title: "Please help -- wireshark!"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by DerGeist on 2007-03-16
Hi guys, please help me as this is driving me nuts.

What I'm trying to do is sniff the network traffic on my home network. I'm using a D-Link 802.11g wireless router with WEP encryption enabled (hexadecimal 40-bit key).

I want to use wireshark to sniff all the traffic on my network so I can monitor what people on my network are doing (I run a bed-and-breakfast type thing, and I want to keep tabs on what people are doing on my network so they don't abuse it. They are made well-aware they will be logged and monitored, so there's no question about that. If they don't like it -- don't use it ;) ).

I have the ipw2200 driver with monitor mode, promiscuous mode, kernel, etc. all working. I can successfully go into monitor mode using the command:

```
sudo iwconfig eth1 mode monitor
```

Doing that makes kismet work just fine, and running in Wireshark under monitor mode yields tons and tons of undecoded wireless info from surrounding (encrypted) networks.

**What's the problem?**

Simple: In Wireshark, I select promiscuous mode and capture. But all I see is *my* traffic, which really doesn't help me at all -- I know what *I'm* doing! :)

I tried inserting the WEP key in the Preferences->IEEE802.11 section of Wireshark, and I tried all the following formats to no avail:

AB:CD:EF:01
ABCDEF01
ab:cd:ef:01

But still, I only get *my* traffic. I also tried twiddling with the FCS/WEP bit check boxes above the WEP key box.

If anyone can help, it is greatly appreciated since this is really driving me nuts. I really need to get this working. I've tried thousands of google searches to no avail, and I searched these forums exhaustively. Here's my system info:

-Intel PRO Wireless 2200BG Card (802.11b+g)
-ipw2200, driver: 1.1.2kmprq
-Edgy Eft, fully up-to-date

Wireshark running as root, info:
Version 0.99.3a

Compiled with GTK+ 2.10.4, with GLib 2.12.3, with libpcap 0.9.4,
with libz 1.2.3, with libpcre 6.4, without UCD-SNMP or Net-SNMP, with ADNS,
without Lua.

Running with libpcap version 0.9.4 on Linux 2.6.17-11-generic

So, again, any help would be awesome. Thanks so much.

---

### Post by inCursorated on 2007-03-16
i'd use kismet to capture and wireshark to analyze.

---

### Post by Kamikaze Wardriver on 2007-03-19
I'm not sure about your set up but are you trying to sniff the wired connections? If so you router maybe putting on a different segment. I know that I can not use Nessus againts my wired computers from my wireless connection. The reason I suspect is that there is some routing going on. My wireless is not on the same network segment as the wired connections and there for I can not get traffic. This maybe what you are seeing as well.

---

### Post by rfdeshon on 2007-07-11
Here is what I had to do to get mine to work. First, to sniff with my computer (also using IPW2200 card), I had to disable the card in NetworkManager (I don't know if you are using networkmanager or not) and disconnect from the network. Then I did sudo iwconfig <interface> mode monitor. I opened wireshark (root) put in the wep key into my prefrences then, and only then (not connected via wireless card to any network, just in monitor mode) was I able to capture in promiscuous mode and get anything besides my own traffic and broadcast traffic. The thing is, if you try and put it in monitor mode while connected to a network, it defaults back to managed, same thing if you try to connect to the network AFTER putting it in monitor mode. I agonized over this one for weeks trying to figure out who was bogging down the wireless in my building, now I've got him hahaha.

---

### Post by tturrisi on 2007-07-11
> I opened wireshark (root) put in the wep key into my prefrences 
Where in wireshark preferences did you put the wep key?

---

### Post by Fanatico on 2008-01-22
I have the very same problem:( Where in wireshark preferences did I have to put the wep key? In Edit->Preferences->Protocols tab I see "No specific preferences" and nothing else. Please help!

The problem I am trying to resolve is that in monitor mode I see only broadcast packet and nothing else.

---

### Post by kirsche on 2008-01-22
Wireshark -. Preferences -> Protocols -> IEEE 802.11

---

### Post by Fanatico on 2008-01-23
> **kirsche said:**
> Wireshark -. Preferences -> Protocols -> IEEE 802.11

The problem is that the Wireshark -> Preferences -> Protocols tab is empty. I can't click on the plus sign next to word "Protocols" in the Wireshark -> Preferences and open list of available protocols.

I tried to open Wireshark -. Preferences -> Protocols on my WindowsXP computer and there I can see list of protocols (including  IEEE 802.11) without any problems. So it seems to me the problem is Ubuntu specific.

Could anyone give me advice what went wrong?

Thanks

---

### Post by kirsche on 2008-01-23
What version of wireshark are you using?
Just had a quick look at a fresh install - in 0.99.6 i can expand the protocols section fine.

---

### Post by Fanatico on 2008-01-23
> **kirsche said:**
> What version of wireshark are you using?
Just had a quick look at a fresh install - in 0.99.6 i can expand the protocols section fine.

I am also using 0.99.6.

---

### Post by kirsche on 2008-01-23
Have a look at your $home/.wireshark/preferences

Have a try to change something in there and see if it applies (are any other preference changes saved?)

---

### Post by hahahan on 2008-01-23
I had simliar problems. ifconfig didn't show the NIC beeing promiscous whilst wireshark running in promiscious mode. ifconfig yournic promisc solves that problem.
Also using aircrack-ng.org's airdecap-ng to de-encrypt the dump might help you out.

Hoping beeing helpfull.

---

