---
title: "I've gone wireless and having problems"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by shavenlunatic on 2008-07-30
Hi,

I recently took the dive into wireless, and it hasn't worked out well.

I purchased 3 items recently:

NETGEAR WGR614 Cable/DSL 54 Mbps Wireless Router
Netgear WG111 Wireless-G USB Adapter
Acer Aspire 5715Z Notebook (Acer InviLink&#8482; 802.11b/g Wi-Fi CERTIFIED® network connection, supporting Acer SignalUp&#8482; wireless technology)

I figured to go for the Netgear items as they advertised that they are supplied with open source drivers.
====

Now, my desktop PC is running Kubuntu (KDE 4.1) with a dual boot with XP  (xp works fine with the wireless)

The laptop is running Ubuntu Hardy with a dual boot XP (xp working fine with the wireless)

====

Kubuntu on the desktop shows a wireless device in the restricted driver manager, but when I go to configure the wireless network, no available networks are listed.  This is pretty much the same situation on the laptop.


I don't expect you to fix it for me, but I've had a look around and can't seem to find a solution (probably me being blind) so if someone could just point me in the right direction it would be greatly appreciated.

Thanks in advance :)

---

### Post by brujoand on 2008-07-30
Did you actually install it from the restricted driver manager, that is, checked the box?

---

### Post by shavenlunatic on 2008-07-30
yes, the box is checked (I didn't do it, it just was there when I looked)

---

### Post by shavenlunatic on 2008-07-31
sorry to bump..but.. *bump*

---

### Post by shavenlunatic on 2008-08-05
really? No advice whatsoever? :(

---

### Post by brujoand on 2008-08-05
Try to do a
"iwconfig" in terminal and also see if this gives anything:
"sudo iwlist <interface usually wlan0 or eth1> scan

This will show if that driver are at all working

---

### Post by ish4269 on 2008-08-05
Hey 

Firstly I had Wireless problems with Hardy, it was hardy to fixy:). This may or may not work for you. Just randomly saw you where using Netgear.

I'm using the WG511T PCMCIA card. In (K)ubuntu-7.10 it worked like a dream, out of the box, with Knetworkmanager. I use WPA encryption on my network. 

Do you use you on board wireless card as well? first make sure the RADIO KILL SWITCH IS OFF. I won't go into the details, that is covered elsewhere in these forums.

UPGRADED TO HARDY: Result> Knetworkmanager refused to enable wireless. Gave up with Knetworkmanager and went back to the old school of editing:

/etc/network/interfaces  (added)

auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf /etc/wpa_supplicant.conf

/etc/wpa_supplicant.conf  (looks like)

network={
ssid="NETWORK_NAME"
        scan_ssid=0
       proto=WPA
        key_mgmt=WPA-PSK
psk=NOT_SHOWING_YOU
        pairwise=TKIP
        group=TKIP
}

Then restart machine.

NOTE: If you edit /etc/network/interfaces (K)networkmanager will not see any network interface you add to the file, including eth0

The above is WPA specific, but you shouldn't be using WEP or no-encryption on your network anyway, but that is my opinion.

---

