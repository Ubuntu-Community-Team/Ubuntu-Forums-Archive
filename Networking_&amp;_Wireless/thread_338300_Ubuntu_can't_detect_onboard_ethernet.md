---
title: "Ubuntu can't detect onboard ethernet"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by cajunaggie on 2007-01-14
My computer has two methods of connecting to the internet. One is the built-in ethernet port on the the motherboard and the other is a NetGear wireless card. Up until now I've been using the wireless card to connect to a router and then out to that newfangled interweb thingie.

I recently moved and my room has an ethernet jack for me to plug into. However, when I go to System>Administration>Networking the onboard card doesn't show up. All I can see is my wireless card, which goes by the designation of ath0.

When I try "ifup eth0" it tells me eth0 isn't configured. I'm fairly sure that when I installed the wireless card I jiggered whatever keeps track of my internet hardware. Unfortunately, I can't seem to find the instructions I followed to get the card up and running.:rolleyes: 

Where do I go to configure eth0? Right now I'm skimming bandwidth from someone's unlocked network and I'm sure he or she doesn't appreciate it

---

### Post by Iowan on 2007-01-15
Is eth0 set up in **/etc/network/interfaces**?

---

### Post by cajunaggie on 2007-01-15
No, I don't see it anywhere. My ~/interfaces looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid linksys

auto ath0
```
I tried replacing ath0 with eth0 and it went whacky on me.

---

### Post by jhenager on 2007-02-25
Question about this:
I have two machines with the same motherboard (PC Chips P23G).
The onboard LAN on the first one never seemed to work no matter what I did, so I put a 3Com card in it and it took off. Forgot about the onboard LAN.
I just setup a new system (with the same motherboard - PC Chips P23G), and Dapper seemed to recognize it fine, and I downloaded 109 updates with it. After restarting, however, the interface is no longer working. I checked the first system, and now I have two Eth interfaces on that system.
My question is: Can I just copy the interfaces file from /etc/network from the working machine to the problem machine - OR - is there a utility or command I can run that is similar to te 'Find New Hardware' functionality in the Bill Gates virus (Windows)?

Thanks in advance, guys. You rock, and Ubuntu rules.
Fix:
Powered off system and unplugged it. Eth0 came back. :guitar:

---

### Post by BenHines on 2007-03-02
The powering down thing is a known issue on the P23G motherboard.  You need to flash your motherboard with the latest BIOS for the P23G.  See my post here for details:

[http://www.ubuntuforums.org/showthread.php?p=2169097#post2169097](http://www.ubuntuforums.org/showthread.php?p=2169097#post2169097)

---

