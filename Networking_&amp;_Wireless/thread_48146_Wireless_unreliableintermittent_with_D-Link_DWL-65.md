---
title: "Wireless unreliable/intermittent with D-Link DWL-650+"
date: 2005-07-11
forum: Networking &amp; Wireless
---

### Post by 4ebees on 2005-07-11
Hi all,

I have 5.0.4 installed (dual boot with Windersninetyeight) on an old Compaq 7770DMT Armada.

I have a D-Link DWL-650+ wireless card - picked up by Ubuntu 'out of the box'.

I've set everything to default (on the w'router) so there's no WEP etc.

I have twice, from the same position in the room, been able to connect to the web, but that's it.

As Ubuntu recognises the card and I can set the wlan0 to active BUT, having done nothing else but close Ffox and restart it, I have lost the connection and acquire find it again. I can connect, from the same position, with Winders, but not Ubuntu. Everything is the same as it was prior to losing the connection - ie I have not made any changes to anything. :???: 

(all this is in my living room - the only place I can get a wireless connection)

The connection seem quite unstable with Ubuntu but not Winders (!!!!!) - is this something to do with Ubuntu's connection to the card????

Is there a wireless signal strength app I can install to check what it's able to 'see'?

Is there something else I need to look at?

I'm new to wireless in Linux, and so would appreciate any assistance able to be offered.  I'm assuming there are other settings I need to change, but I'm afraid I'm not sure where to start.

I have just checked 

iwconfig

and the signal is below 60 (in Winders this means that I lose the connection)

also 

Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag: 0

tail -f /var/log/messages

provides 

Radio scan found 0 stations 

Admittedly after my initial jubilation at having wireless connectivity, this sudden loss is very weird.

Many thanks.

---

### Post by john_van_v on 2005-07-19
I have a 630, I am curious if you had and success, my liveCD didnt get me started.

---

### Post by 4ebees on 2005-07-19
[QUOTE=john_van_v]I have a 630, I am curious if you had and success, my liveCD didnt get me started.[/QUOTE]
 Hi John,

Thanks for reminding me to post back here.
(Long Reply :))
I don't know if this helps at all (most likely not).

The problem turned out to be less than obvious. As I mentioned, I had a wireless router connected to my network. I'd completely forgotten that it could act as a DHCP server. So when I had reset it to the 'default options', this option had been reactivated. 

I made a post to the Smoothwall forum because I kept getting these wierd disconnect issues - Smoothwall was connected to the web, but my connections to it and the web were being randomly teminated and I had to deactivate/reactivate the relevant machines network device to get 'net connection back.

One of the posts on the Smoothwall forum asked if I had anything acting as a DHCP server other than Smoothwall and I suddenly remembered. DOH!   :rolleyes: 
The Wireless connection has improved dramatically since.

I should mention that Ubie has been able to work on everything on my laptop, except sound. I cannot get the damn thing to work and I'm probably going to have to post about that.

If you are able to create space for it, I'd seriously suggest dual-booting. Ubie was easy to set up on my old laptop. If you're not familiar with the naming and file type policies, join your local Linux User Group; they'll be very helpful.

If you'd like, e-mail me or post your details (you'd need to post details about your machine, the partitions - such as do you have a C: and D: drive: - etc) and I give you a hand (and some directions to other material too). It's less difficult than you may imagine. If you've ever installed Winders, you can dual-boot your machine (with a little help :)).

---

### Post by funkydan2 on 2005-07-19
Maybe you need to increase the txpower of the card?

Obviously you need to read the documentation (maybe at [http://acx100.sf.net](http://acx100.sf.net) and also "man iwconfig) to make sure you don't damage your card.

---

### Post by 4ebees on 2005-07-20
[QUOTE=funkydan2]Maybe you need to increase the txpower of the card?

Obviously you need to read the documentation (maybe at [http://acx100.sf.net](http://acx100.sf.net) and also "man iwconfig) to make sure you don't damage your card.[/QUOTE]

Hi funkydan2,

The problem is resolved at present.

What I'd like to do is set up specific details for this access point, WEP etc... though to be truthful, the range for my set up is so poor that it's only accessible from my living room [where the aerial's located]. I've read through the Man pages, but am a little confused by them. For instance, the Man pages read (for setting the ESSID name):

**iwconfig eth0 essid NAME**

Whereas my config file shows 

**iwconfig wlan0 essid NAME**

I'm also not sure if you enter the config details in a long paragraph, e.g.:

**iwconfig wlan0 essid NAME freq N.UMBER channel NUMBER**

or in a column, e.g.:
[B]
iwconfig wlan0 essid NAME
iwconfig wlan0 freq NUMBER
iwconfig wlan0 channel NUMBER[/B]

Guess I should check out the posts or make one of my own :)

---

### Post by funkydan2 on 2005-07-20
wlan0 = the first (computers like to count from 0) wireless card
eth0 = the first ethernet card

But to confuse things, some kernel modules name the wireless cards as ethernet cards.  The acx100 driver calls it wlanX (where X is the number of the card).

In /etc/network/interfaces people generally write the various parameters in a column - it's probably a style thing.  I'm not sure if the 'long paragraph' option works, but it probably does work.

With your WEP key: the version of the kernel module that comes with Hoary doesn't support WEP.  You'll need to update the kernel modules to get WEP working - i've put a post about my experience in this on [my blog](http://saunders.90megs.com/blog/index.php?entry=entry050705-073812).  Unfortunately, there's no WPA support yet.

---

### Post by skyboy on 2005-07-20
can you post /etc/network/interface

I have DWL-AG650 too and a celeron intel wifi card too, and both are orking at the same time :)

---

### Post by 4ebees on 2005-07-21
This is my /etc/network/interfaces config:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface wlan0 inet dhcp
wireless-essid NAME
channel NUMBER
auto wlan0

iface eth0 inet dhcp

[QUOTE=skyboy]can you post /etc/network/interface

I have DWL-AG650 too and a celeron intel wifi card too, and both are orking at the same time :)[/QUOTE]

---

### Post by skyboy on 2005-07-21
by the way, I checked to txpower of mine, and compared to the celeron wifi card, the quality of the link varies from 33 to 92/100 (the best for the celeron wifi card) and they are at the same place. so yes indeed, the transmission power is much less for the D-Link card.
What I've done is setting the power with "iwconfig ath0 txpower 70", (yes, for me, the DLINK is on ath0) and it did improove a bit.
So maybe you could give it a try.

---

### Post by 4ebees on 2006-05-26
Well, nearly a year later :)

I managed to fix the problem - but in the interim bought a newer laptop with integrated wireless card. I can't recall what I did as I have since sold the other laptop. I now am playing around with an even OLDER laptop with the same wireless PCMCIA card and so will have to see if I can get it going.

Thanks for the assistance 'way back then' (I have had recurrent problems where I don't get e-mail about things I have posts I have logged or have subscribed to).


[QUOTE=skyboy]by the way, I checked to txpower of mine, and compared to the celeron wifi card, the quality of the link varies from 33 to 92/100 (the best for the celeron wifi card) and they are at the same place. so yes indeed, the transmission power is much less for the D-Link card.
What I've done is setting the power with "iwconfig ath0 txpower 70", (yes, for me, the DLINK is on ath0) and it did improove a bit.
So maybe you could give it a try.[/QUOTE]

---

