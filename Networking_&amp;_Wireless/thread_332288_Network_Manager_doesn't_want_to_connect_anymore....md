---
title: "Network Manager doesn't want to connect anymore..."
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by Slasher Fun on 2007-01-05
Hi everybody,

Today, I tried to add the Trevino's Sources List ([http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)) as my sources.list

Everything worked fine, but since this, NetworkManager doesn't want to connect anymore to any network :( Details : 

* When starting the GNOME session, NetworkManager is shown as disconnected, and the WiFi connexion doesn't work.
* Then, I choose my not-protected (for tests in order to try to fix the problem) WiFi network
* The connexion starts to establish (the two dark points and the rotating thing)
* After a second, before the first point becomes green, the icon comes back to the "disconnected" state, and the connexion still doesn't work.
* If I try "sudo dhclient eth1", wow, it works. But NetworkManager still appears as disconnected
* If then I try again to connect with NetworkManager, it still doesn't work and the connexion is lost until I type dhclient again.
* My /etc/network/interfaces only contains the two lines with the "lo" interface
* If I display "connexion information" on NetworkManager, I do have eth1 as interface, 48Mbits as speed, ipw2200 as driver, and everything else at zero but the MAC adresse that is correct.
* The NetworkManager version is the 0.6.3-2ubuntu6, from the official repositories

I use Ubuntu Edgy on a laptop (Acer Aspire 1692) with ipw2200 wifi chipset, and everything worked fine before the "big update"

Thanks in advance for any help that could be provided, :) 

Slasher Fun

---

### Post by groggyboy on 2007-01-05
i've heard that because trevino's repo is so bleeding edge, it's better to leave it commented out/disabled in your sources.list except when you wanna install something from it (like flash9).

i tried the repo on my computer, and it wanted to install a newer version of wpasupplicant (used by network-manager). you could try forcing it to use the official ubuntu version.  to do this, search for wpasupplicant in synaptic, then use the menu option Packages > Force Version... to select the older official package (0.5.4-5).

it may be that wpasupplicant has nothing to do with your problem, but considering that it was the only network-manager related package that would have changed when you upgraded with trevino's repo, it seems like a logical place to start troubleshooting! :D

---

### Post by teaker1s on 2007-01-05
I found that network manager applet requires 
system-administration-networking to not have ticks-see screenshot

---

### Post by Slasher Fun on 2007-01-06
Thanks groggyboy ! That was actually because of the wpa_supplicant version, strange since the network is not encrypted but well it works fine again.

:)

---

### Post by sojyujai on 2007-01-08
Thanks from me also!
I had the same strange problem with networkmanager.  I pulled out what little hair I have left trying to figure out the problem, messed with a lot of settings I probably shouldn't have and even considered switching to Mepis before I stumbled upon this thread.

It didn't even occur to me that the problem could have been due to that repository.  Anyway, I've forced the older version and all is working fine now.  I've disabled the Trevi repository for now, but is there a way to block wpasupplicant specifically from updating if I re-enable it?

---

