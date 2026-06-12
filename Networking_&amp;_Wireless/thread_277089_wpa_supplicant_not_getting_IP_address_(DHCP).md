---
title: "wpa_supplicant not getting IP address (DHCP)"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by nothingxs on 2006-10-13
Warning, Linux newbie ahead.

I have wpa_supplicant configured to boot on startup. However, it seems that there's no communication with the DHCP servers, and so I'm not getting an IP address (sometimes causing the connection to time out). Using **dhclient** immediately afterwards lets me browse, so it really so far seems to be that I'm missing something to get DHCP working.

Is there any way I can set my card up to get a new IP address automatically through DHCP everytime I connect to a new network?

---

### Post by wieman01 on 2006-10-14
Install "wpa_supplicant" only if you need WPA. Otherwise remove it as it may create problems when the PC connects to your network.

Are you running a wireless network there or ethernet? If ethernet you won't need encryption anyway (WPA). If this does not help please post the contents of the following file (terminal command):
> sudo gedit /etc/network/interfaces
Enter your password when prompted.

---

### Post by nothingxs on 2006-10-14
I need WPA, which is why I installed WPA supplicant.

I'm a newbie, but not that new. I've a bit of experience from tinkering here and there, but I otherwise am pretty clueless.

There's a wireless network here, and ethernet. However, it's hard to use the ethernet everywhere and it's just easier for me to use the wireless so I can get my computer on my desk. 

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 0c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


auto eth0
```

I had found a utility sometime ago that was written in Python that no longer worked on Ubuntu, that was pretty much like having Windows' Zeroconf in Ubuntu. If that had WPA support, it'd be nice to have an easy and accessible interface like that to run wireless from. :-#

---

### Post by nothingxs on 2006-10-14
New symptom: it seems the wireless connection is really slow, as though everytime the connection has to look up a new address through DNS or when the wireless connection comes out of an idle state, it will sit there for six or seven seconds before moving. If I, say, click through quickly through a website, the pages all load very quickly. If I stop, wait a bit and then open a new site, it'll take ~6 seconds for the connection to react. This is pretty odd.

---

### Post by wieman01 on 2006-10-14
> **nothingxs said:**
> New symptom: it seems the wireless connection is really slow, as though everytime the connection has to look up a new address through DNS or when the wireless connection comes out of an idle state, it will sit there for six or seven seconds before moving. If I, say, click through quickly through a website, the pages all load very quickly. If I stop, wait a bit and then open a new site, it'll take ~6 seconds for the connection to react. This is pretty odd.
As far as the performance issue is concerned, try this:
> Disable ipv6 in Firefox:

a. URL field: about:config
b. Search for ipv6.
c. Right-click->toggle

To disable ipv6 globally/system-wide, search the forum.
Let me know if browsing gets faster. If not, the we disable "ipv6" globally.

_**EDIT:**_
To disable "ipv6" globally see this thread: [http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

---

### Post by wieman01 on 2006-10-14
> **nothingxs said:**
> I had found a utility sometime ago that was written in Python that no longer worked on Ubuntu, that was pretty much like having Windows' Zeroconf in Ubuntu. If that had WPA support, it'd be nice to have an easy and accessible interface like that to run wireless from. :-#
Ok, there are two utilities that you can use if you don't want to mess around with text files. 

1. NetworkManager (plus Gnome & KDE GUI)
2. Wifi-Radar

I personally recommend that you give Wifi-Radar a try because NetworkManager does not support Static IP (as opposed to DHCP) and cannot deal with hidden ESSID's. If these tools are no option, let me know & we continue here.

---

### Post by nothingxs on 2006-10-15
Wifi-Radar doesn't have WPA** support.](*,) If it did, though, that would be very awesome.

As for right now, I'd like to know how to create a symlink or whatever to make my wpasupplicant.sh script that I've placed in etc/init.d/ run everytime I start my computer, instead of my having to start it manually. I'd also like it to immediately have DHclient sit "idle" to wait to try and renew my IP lease. 

I'll disable IPV6 and let you know how that turned out. It only affects my wireless connection, but maybe that'll help it anyways. Thanks!

---

### Post by wieman01 on 2006-10-15
> **nothingxs said:**
> Wifi-Radar doesn't have WEP support.](*,) If it did, though, that would be very awesome.
Hang on... Do you need WPA or WEP? Or both? WPA_Supplicant is no good for WEP, but I assume you know that.

Wifi-Radar DOES support both WEP & WPA.

---

### Post by wieman01 on 2006-10-15
> **nothingxs said:**
> As for right now, I'd like to know how to create a symlink or whatever to make my wpasupplicant.sh script that I've placed in etc/init.d/ run everytime I start my computer, instead of my having to start it manually. I'd also like it to immediately have DHclient sit "idle" to wait to try and renew my IP lease.
As for the symlink... Actually wpa_supplicant is started as it is part of you "interfaces" file. If you include it there, there is no need for another start-script.

---

### Post by nothingxs on 2006-10-15
> **wieman01 said:**
> As for the symlink... Actually wpa_supplicant is started as it is part of you "interfaces" file. If you include it there, there is no need for another start-script.

It isn't starting from there.

---

### Post by wieman01 on 2006-10-15
> **nothingxs said:**
> It isn't starting from there.
Well, in theory it is. And as far as my PCs are concerned wpa_supplicant is controlled by the "interfaces" configuration file. What makes you think it does not? Do you have to restart it manually?

Apparently something is wrong, but it would help if you described the symptoms in more detail. Plus it would be helpful if you posted your wpa_suplicant configuration file as well.

Also let us know what your network settings are: WEP, WPA, DHCP, MAC filtering, router or simple modem, etc. I think we are getting there, it's just that I know too little about your network. It will help if you outlined it a bit.

---

### Post by nothingxs on 2006-10-15
For whatever reason, it has decided it wants to start at bootup, now. Maybe I just needed to reboot more than once. o_O

I've disabled IPv6 as well using a bad_list file. This made my connection very fast. And now everything seems to be working just fine. Adding networks manually isn't such a big deal, so I'm 100% set. Thanks :)

---

### Post by wieman01 on 2006-10-15
> **nothingxs said:**
> For whatever reason, it has decided it wants to start at bootup, now. Maybe I just needed to reboot more than once. o_O

I've disabled IPv6 as well using a bad_list file. This made my connection very fast. And now everything seems to be working just fine. Adding networks manually isn't such a big deal, so I'm 100% set. Thanks :)
This is... a suprising end. But I am (genuinely) glad this hard worked for you. :-) See you next time then.

---

### Post by nothingxs on 2006-10-15
I'm surprised it worked with that amount of work, myself. Now I have a Netgear WG511v2 Marvell card I need to pawn off somewhere. ](*,)

---

### Post by nothingxs on 2006-10-15
> **nothingxs said:**
> I'm surprised it worked with that amount of work, myself. Now I have a Netgear WG511v2 Marvell card I need to pawn off somewhere. ](*,)

It didn't really work, apparently. My home wireless networking is still painfully slow, but apparently it's fast anywhere else. I'm looking into it being a router issue.

---

### Post by wieman01 on 2006-10-15
Oh, then you're right. Will be a router issue. There are a number of settings you can change to boost your (wireless) network's performance e.g. beacon interval, RTS threshold, etc. Check it through the configuration tool of your router, there should be something like "wireless settings" or "enhanced settings". I had to do the same because the initial setup resulted in painfully slow transfer rates.

---

