---
title: "Doesn't find my network? (Wireless)"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by AlyssaTruax on 2008-07-20
Hi.

My wireless card is: Ethernet Controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

In my Hardware Drivers section is shows it as being enabled (Atheros driver)

So... On my windows computer it shows two networks, one is named "Hanson", the other is named "default". I connect to the Hanson one.

On Ubuntu it only lists 'default', and not 'Hanson'... When I connect to 'default' I have one bar and I can't ping out anywhere, or 192.168.1.0, nothing.. So I manually put in Hanson even though it didn't detect it. I've done this a few times now and it usually won't connect but then sometimes it'll say its at 98/100 connection and have four bars, but even when it's like that I can't ping out or go to a website or anything.

And I've disabled Wired Connection in hopes that it was messing things up but still nothing... 

I don't know what else to do, please help? :(


Edit: Okay so when I connect to Hanson manually, and then click the bars, it lists both default and Hanson now. When I'm connected to Hanson it has full 100%, and default has like 20%.... But on both I can't ping out anywhere or do anything :/?

---

### Post by AlyssaTruax on 2008-07-23
Any ideas? :confused:

---

### Post by AlyssaTruax on 2008-07-29
Sigh. Can someone please suggest something? Anything? 

When doing 'sudo /etc/init.d/networking/ restart', it gives me 

SIOCADDRT: No such process
Failed to bring up ath0.

Same when I do ifup ath0... The driver is enabled, though? 

Anyone?

---

### Post by bgerlich on 2008-07-29
Try using cli tool: "iwlist ath0 scanning". Does it list the other network?

If not, try recreating the interfacewith wlanconfig:
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode sta

post output of "dmesg | tail -n 20" and iwconfig right after recreating your interface.

---

### Post by AlyssaTruax on 2008-07-29
> **bgerlich said:**
> Try using cli tool: "iwlist ath0 scanning". Does it list the other network?

If not, try recreating the interfacewith wlanconfig:
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode sta

post output of "dmesg | tail -n 20" and iwconfig right after recreating your interface.

Okay. Just so you know I did "route add 192.168.0.1 ath0" and now my ifup says something like "Already configured" and my /etc/init.d/networking restart doesn't fail on ath0! So now, when I do iwconfig, it returns me being on the "Hanson" network (Good!), with signal of 99. And when I do "iwlist scanning" it shows me that "default" network. When I ping the gateway, 192.168.0.1, it returns host destination is unreachable... When I ping out to anywhere else it gives the same.

So.. Should I still recreate the interface? Where should I go from here? Thank for responding, I'm really in need of someone to hold my hand here.

---

### Post by bgerlich on 2008-07-29
NetworkManager and ifup don't really like each other. If you haven't stated otherwise in /etc/network/interfaces it is the NM, not ifup that handles your web interfaces. Quite a few people prefer Wicd to NM - try installing that - it will remove NM automatically. It could also be some sort of module-card quirk - sometimes recreating the interface remedies that. If not, maybe you will have luck with building new drivers, or even using ndiswrapper instead of madwifi.

I would say your MO should be:

1. try recreate the interface - it won't do any harm for sure.
2. install wicd
3. Checking if it is not a distro issue - get a Knoppix LiveCD and test the network with it.
4. Make sure it isn't a problem with your AP config (trying different wireless router, playing with some settings) or the easiest - get Backtrack 3 to run off USB thumb drive or LiveCD and check the network with kismet (is it visible, are the beacon packets received) - everything is available in a form of handy and easy to use tools - point and click really.
5. try to use ndiswrapper instead of standard network drivers
6. remove ndiswrapper and try to configure your network manually in /etc/network/interfaces (small chance of success).
7. Try to compile new drivers form madwifi svn repository - who knows - maybe it was a bug that has already been dealt with.

You can try the number 5 (ndiswrapper) and number 7 (compiling) before 4 and 5 but the Knoppix and Backtrack steps will give you more info about the problem.

Oh, and some may say you should try ndiswrapper as a first thing, I have pushed it down the list but this is just my personal preference.

---

### Post by AlyssaTruax on 2008-07-29
> **bgerlich said:**
> NetworkManager and ifup don't really like each other. If you haven't stated otherwise in /etc/network/interfaces it is the NM, not ifup that handles your web interfaces. Quite a few people prefer Wicd to NM - try installing that - it will remove NM automatically. It could also be some sort of module-card quirk - sometimes recreating the interface remedies that. If not, maybe you will have luck with building new drivers, or even using ndiswrapper instead of madwifi.

I would say your MO should be:

1. try recreate the interface - it won't do any harm for sure.
2. install wicd
3. Checking if it is not a distro issue - get a Knoppix LiveCD and test the network with it.
4. Make sure it isn't a problem with your AP config (trying different wireless router, playing with some settings) or the easiest - get Backtrack 3 to run off USB thumb drive or LiveCD and check the network with kismet (is it visible, are the beacon packets received) - everything is available in a form of handy and easy to use tools - point and click really.
5. try to use ndiswrapper instead of standard network drivers
6. remove ndiswrapper and try to configure your network manually in /etc/network/interfaces (small chance of success).
7. Try to compile new drivers form madwifi svn repository - who knows - maybe it was a bug that has already been dealt with.

You can try the number 5 (ndiswrapper) and number 7 (compiling) before 4 and 5 but the Knoppix and Backtrack steps will give you more info about the problem.

Oh, and some may say you should try ndiswrapper as a first thing, I have pushed it down the list but this is just my personal preference.

A big problem here is that this is a fresh install without any updates.. This computer has no way to get plugged directly. It's wireless or nothing. So I can't get anything from apt-get.

I'm not experienced enough to install Backtrack. This is my first Ubuntu install, just trying to grab at any information I can from googling to solve this problem. I have tried Linux Mint, though (Because it says you get more Wireless drivers or something), and same problem..

For recreating the ath0:

wlanconfig: command not found



It's been a week now without internet, I've been having to use my mom's laptop. A few other people use this computer- They like Ubuntu and they like the software it comes with, but they need the internet and are starting to get aggravated. 

I heard that Antheros or whatever brand it is that makes my wireless card just released new linux specific drivers that are open source, but that they aren't in the livecd yet.. Should I go back to Windows for the time being and then try Ubuntu later when the wireless drivers are updated and maybe other quirks are worked out? The next version perhaps? Please advise :(

---

### Post by bgerlich on 2008-07-29
Backtrack is really easy to install just download an USB version, unpack .iso with winrar ( or mount it in linux), copy the content to USB stick, after copying start the .bat file in "boot" directory on your USB and you are ready to go. 

To get to the point. I forgot the wlanconfig is not installed by default so you have to get your internet working at least for a moment - this can be achieved by plugging an ethernet cable straight to the AP. Is that not an option?

If not, you can try this: first turn of the network in NM and sudo ifconfig ath0 up . Then try to set the channel manually to the channel that your AP is using. sudo iwconfig ath0 channel X  (X -is the channel that the AP is using). Afterwards set the essid to "Hanson" by running sudo iwconfig ath0 essid "Hanson" . Then set the AP MAC address by typing sudo iwconfig ath0 ap 00:00:00:00:00:00 (where 00:00 etc is the MAC address of your AP). You can also set the transmission rate by typing sudo iwconfig ath0 rate 1M .After that run sudo dhclient ath0 to get the DHCP info.

---

